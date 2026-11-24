# frontend-wiki — LLM Wiki 教學簡報專案

本專案為 TAICA 生成式AI課程第10集「用 LLM Wiki 做一份教學 HTML 簡報」的作業交付。包含 LLM Wiki 知識庫與單頁教學型 HTML 簡報。

---

## 🔄 步驟三：Loop / Graph 流程設計說明

### 節點圖 (Workflow Graph)

```text
[Node A] 檢索 raw/ 原始教材
      ↓
[Node B] 提煉成原子 Wiki 卡片 (Why / 核心概念 / Code Snippet / 避坑)
      ↓
[Node C] 審查卡片 Frontmatter 與內容規範 (SCHEMA.md 對照)
      ↺ (迴圈回 Node B 若不符合)
      ↓
[Node D] 代碼生成：編譯 wiki/ 卡片 + 建立 MOC + 編寫 project-blueprint.md
      ↓
[Node E] 驗證：index.md 超連結、index.html 簡報引用、YAML Frontmatter 解析
      ↺ (迴圈回 Node D 若驗證失敗)
      ↓
[輸出] 推送至 GitHub + GitHub Pages 部署
```

### Loop 與檢查點說明

| 迴圈 | 來源節點 → 目標節點 | 觸發條件 | 審查/重新生成內容 |
|------|---------------------|----------|-------------------|
| Loop B | Node C → Node B | 卡片 Frontmatter 欄位缺失、tags 語法錯誤、WikiLink 格式不正確 | 重新撰寫卡片，補齊 `id`/`module`/`status`/`tags`/`summary`/`source`/`last_updated`/`related` |
| Loop D | Node E → Node D | GitHub Pages YAML 解析錯誤（如 `#` 未加引號導致 flow sequence 錯誤）、index.html 引用斷鏈 | 修正 YAML Frontmatter（改為區塊序列 `- "tag"`）、補上缺失的 wiki 引用 |

### 停損機制與設計原因

**停損機制：** 單張卡片編輯最多重複 **3 次** (Loop B/D 合計)，超過上限後標記為 `status: drafted` 並移至 `wiki/99-archive/`，不阻塞後續卡片編譯。

**設計原因：**
1. **先修大綱再產代碼**：Node C (審查) 設在 Node D (代碼生成) 之前，確保卡片結構正確後才大量產出，避免後期大幅重構。
2. **快速失敗、早期修正**：在 Node E 驗證階段即發現 YAML/斷鏈問題，避免推送至 GitHub 後才發現網頁錯誤。
3. **停損防止無限迴圈**：設定 3 次上限避免 LLM 反覆產出錯誤卡片導致專案停滯。

---

## 🤔 步驟四：反思

### 最常出錯的節點

**Node C (卡片審查 / Frontmatter 檢查)** 最常出錯。具體錯誤包括：
- YAML flow sequence `[#HTML, #CSS]` 中的 `#` 被解析為註解符號，導致 GitHub Pages/Jekyll 顯示 `did not find expected ',' or ']' while parsing a flow sequence`
- 流式序列加引號後仍出現 `unexpected end of stream while scanning quoted scalar`
- `related` 欄位的 `[[WikiLink]]` 語法被 YAML 解析器誤判為嵌套流式序列

### 檢查前移

發現 YAML 解析錯誤後，將檢查從 **Node E (驗證)** 前移至 **Node C (卡片生成時)**：
- 在編寫每張卡片時，即採用 **YAML 區塊序列 (block sequence)** 格式：`tags:` 下方以 `  - "#HTML"` 寫入，避免 flow sequence 的 `#` 問題
- `related` 欄位統一使用 `  - "[[WikiLink]]"` 區塊序列格式，避免 `[[` 被誤判
- 編輯完成後立即以本地 Python `yaml` 模組預先解析，確認無誤後再推送

### Workflow 調整

**有，已修改 workflow/graph。** 具體調整：
1. **新增 Node C (審查節點)**：原本流程僅有 Node A→B→D→E，缺乏中間審查；新增 Node C 專門對照 SCHEMA.md 檢查 Frontmatter 完整性，減少 Node E 的驗證失敗率。
2. **將 YAML 格式標準前置**：在 agent.md SOP 中明確規定 `tags` 與 `related` 必須使用區塊序列，而非流式序列，從源頭杜絕 `#` 註解錯誤。
3. **新增本地 YAML 預檢**：推送前執行 `python3 -c "import yaml; yaml.safe_load(open('wiki/xx.md'))"` 預驗證，避免 GitHub Pages 編譯失敗。

---

## 📂 專案檔案結構

```
frontend-wiki/
├── README.md                 ← 本檔案 (步驟三/四說明)
├── agent.md                  ← LLM 編譯 SOP
├── SCHEMA.md                 ← Wiki 卡片規範
├── index.md                  ← 全庫總目錄 (含標準 Markdown 相對路徑超連結)
├── log.md                    ← 追加式編譯日誌
├── index.html                ← 單頁教學型 HTML 簡報 (6 頁)
├── raw/                      ← 18 篇原始教材 (唯讀)
│   ├── 01-skeleton-and-encoding.md
│   └── ... (共 18 篇)
├── wiki/
│   ├── 00-mocs/              ← 4 份專題地圖
│   ├── 01-html/              ← 5 篇 HTML 卡片
│   ├── 02-css/               ← 6 篇 CSS 卡片
│   ├── 03-design-systems/    ← _stub-m3-overview.md (Stub)
│   ├── 04-js/                ← 7 篇 JS 卡片
│   ├── 05-devtools-and-api/  ← _stub-f12-and-api-overview.md (Stub)
│   └── projects/
│       └── project-blueprint.md ← 實戰藍圖
└── .git/
```

---

*審查完成日期：2026-11-24 | 審查員：TAICA 生成式AI 課程作業審查助教*
