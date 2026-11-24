# agent.md — frontend-wiki LLM 編譯 SOP

本檔案為給 LLM 的完整標準作業程序（SOP），規範如何處理 `raw/` 檔案、如何拆解成原子 Wiki 卡片、如何建立 MOC、如何更新 `index.md` 與 `log.md`。

所有編譯動作必須遵循本 SOP，並與 `SCHEMA.md` 保持一致。

---

## 1. 編譯總流程（六步驟）

```
步驟 1: 讀取 raw/ 檔案
   ↓
步驟 2: 拆解為原子卡片（提取 Why / 核心概念 / Code Snippet / 避坑）
   ↓
步驟 3: 寫入 wiki/<模組>/<卡片>.md（含完整 Frontmatter）
   ↓
步驟 4: 建立/更新 MOC（wiki/00-mocs/）
   ↓
步驟 5: 彙整主專案藍圖（wiki/projects/project-blueprint.md）
   ↓
步驟 6: 更新 index.md 與 log.md
```

---

## 2. 步驟 1：讀取 raw/ 檔案

### 2.1 入口點
所有原始教材位於 `raw/` 資料夾，來自 `frontend-mastery/curriculum/`。目前 18 篇分佈於：

| 模組 | raw/ 檔案 | 對應 wiki/ 資料夾 |
|------|----------|------------------|
| HTML | `01-skeleton-and-encoding.md` | `wiki/01-html/` |
| HTML | `02-text-and-basic-tags.md` | `wiki/01-html/` |
| HTML | `03-forms-and-inputs.md` | `wiki/01-html/` |
| HTML | `04-multimedia-and-tables.md` | `wiki/01-html/` |
| HTML | `05-semantics-and-a11y.md` | `wiki/01-html/` |
| CSS | `01-intro-and-selectors.md` | `wiki/02-css/` |
| CSS | `02-box-model-and-units.md` | `wiki/02-css/` |
| CSS | `03-positioning-and-zindex.md` | `wiki/02-css/` |
| CSS | `04-flexbox-practical.md` | `wiki/02-css/` |
| CSS | `05-grid-practical.md` | `wiki/02-css/` |
| CSS | `06-responsive-design.md` | `wiki/02-css/` |
| JS | `01-basics-and-variables.md` | `wiki/04-js/` |
| JS | `02-operators-and-control-flow.md` | `wiki/04-js/` |
| JS | `03-functions-and-scope.md` | `wiki/04-js/` |
| JS | `04-dom-manipulation-mastery.md` | `wiki/04-js/` |
| JS | `05-array-and-object-deep-dive.md` | `wiki/04-js/` |
| JS | `06-async-and-promises.md` | `wiki/04-js/` |
| JS | `07-engine-and-event-loop.md` | `wiki/04-js/` |

### 2.2 唯讀原則
`raw/` 中的檔案**嚴禁修改**。編譯僅單向輸出：`raw/` → `wiki/`。

---

## 3. 步驟 2：拆解為原子卡片

### 3.1 拆解原則

每篇 raw 檔案必須拆解為一張 Wiki 卡片，卡片內容不得直接複製 raw 全文，而應：

1. **提取「為什麼 (Why)」** — 學習此觀念的動機與痛點
2. **提取「核心概念」** — 底層原理、圖解說明、對比表格
3. **提取「Code Snippet」** — 精簡、可複製即用的程式碼（不超過 30 行）
4. **提取「避坑對比 (❌ vs ✅)」** — 錯誤做法與正確做法並列
5. **移除「主專案功能疊加」** — 該內容抽離至 `wiki/projects/project-blueprint.md`，卡片專注技術觀念

### 3.2 卡片標準結構（必須包含）

```
---
id: <模組編號>-<卡片編號>
module: <html|css|js>
title: <中文標題>
status: published
tags: [<標籤1>, <標籤2>]
summary: <一句話摘要>
source: raw/<原始檔名>.md
last_updated: <YYYY-MM-DD>
related:
  - [[關聯頁面1]]
  - [[關聯頁面2]]
---

# <中文標題>

> <一句話摘要，重複 Frontmatter 內容>

## 🎯 為什麼 (Why)

<說明學習動機與痛點>

## 🧠 核心概念

<底層原理、圖解說明、對比表格>

## 💻 Code Snippet

```<語言>
<精簡程式碼>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|

## 🔗 關聯連結

- [[相關概念1]]
- [[相關概念2]]

## 🏷️ 標籤

#HTML #CSS #JS ...
```

### 3.3 命名對應表

| raw/ 檔名 | wiki/ 卡片檔名 | id | module |
|----------|--------------|-----|--------|
| `01-skeleton-and-encoding.md` | `html-skeleton-and-encoding.md` | `01-01` | `html` |
| `02-text-and-basic-tags.md` | `html-text-links-and-lists.md` | `01-02` | `html` |
| `03-forms-and-inputs.md` | `html-forms-and-validation.md` | `01-03` | `html` |
| `04-multimedia-and-tables.md` | `html-multimedia-and-tables.md` | `01-04` | `html` |
| `05-semantics-and-a11y.md` | `html-semantics-and-a11y.md` | `01-05` | `html` |
| `01-intro-and-selectors.md` | `css-selectors-and-specificity.md` | `02-01` | `css` |
| `02-box-model-and-units.md` | `css-box-model-and-units.md` | `02-02` | `css` |
| `03-positioning-and-zindex.md` | `css-positioning-and-zindex.md` | `02-03` | `css` |
| `04-flexbox-practical.md` | `css-flexbox-layout.md` | `02-04` | `css` |
| `05-grid-practical.md` | `css-grid-layout.md` | `02-05` | `css` |
| `06-responsive-design.md` | `css-responsive-design.md` | `02-06` | `css` |
| `01-basics-and-variables.md` | `js-basics-and-variables.md` | `04-01` | `js` |
| `02-operators-and-control-flow.md` | `js-operators-and-control-flow.md` | `04-02` | `js` |
| `03-functions-and-scope.md` | `js-functions-scope-and-closures.md` | `04-03` | `js` |
| `04-dom-manipulation-mastery.md` | `js-dom-manipulation.md` | `04-04` | `js` |
| `05-array-and-object-deep-dive.md` | `js-arrays-objects-and-hof.md` | `04-05` | `js` |
| `06-async-and-promises.md` | `js-async-and-promises.md` | `04-06` | `js` |
| `07-engine-and-event-loop.md` | `js-engine-and-event-loop.md` | `04-07` | `js` |

---

## 4. 步驟 3：寫入 Wiki 卡片

### 3.1 檔案路徑
- HTML 卡片：`wiki/01-html/html-<名稱>.md`
- CSS 卡片：`wiki/02-css/css-<名稱>.md`
- JS 卡片：`wiki/04-js/js-<名稱>.md`

### 3.2 Frontmatter 範例（JS 第 3 篇）

```yaml
---
id: 04-03
module: js
title: 函數與作用域
status: published
tags: [#JS, #函數, #作用域, #閉包]
summary: 函數宣告、函式表達式與區塊/函數作用域差異，含閉包基本概念。
source: raw/03-functions-and-scope.md
last_updated: 2026-11-24
related:
  - [[Closure]]
  - [[Hoisting]]
---
```

---

## 5. 步驟 4：建立 MOC（專題地圖）

### 5.1 需建立的 4 份 MOC

| MOC 檔名 | 標題 | 涉及概念 |
|----------|------|----------|
| `moc-a11y-and-seo.md` | A11y 無障礙與 SEO 實務 | 語義化標籤、alt 屬性、label 綁定、meta 設定 |
| `moc-frontend-pitfalls.md` | 現代前端避坑指南 | Div Soup、CSS 權重、Quirks Mode、亂碼、vh 陷阱 |
| `moc-browser-rendering-and-perf.md` | 瀏覽器渲染與效能優化 | Box Model、Event Loop、渲染模式、clamp、Mobile-First |
| `moc-layout-and-rwd.md` | 版面佈局與響應式設計 | Flexbox、Grid、Media Query、clamp、auto-fill |

### 5.2 MOC 內容結構

每份 MOC 必須包含：

1. **模組索引表** — 列出該主題涉及的模組與相關卡片（WikiLink）
2. **概念交叉索引** — 跨模組概念對照表
3. **❌ vs ✅ 避坑速查** — 錯誤做法與正確做法
4. **相關 MOC** — 與其他 MOC 的雙向連結

### 5.3 MOC Frontmatter 範例

```yaml
---
id: moc-01
module: cross
title: 現代前端避坑指南
status: published
tags: [#MOC, #Pitfalls]
summary: 跨 HTML/CSS/JS 的常見錯誤與正確做法對比表。
last_updated: 2026-11-24
---
```

---

## 6. 步驟 5：彙整主專案藍圖

### 6.1 檔案路徑
`wiki/projects/project-blueprint.md`

### 6.2 內容來源
從 18 篇 raw 檔案的「🛠️ 主專案功能疊加」區段提取所有步驟，統一彙整為：

1. **專案概述** — 個人品牌網站目標與產出
2. **階段規劃表** — 階段、任務、相關卡片、驗收標準
3. **驗收清單 (Checklist)** — 可勾選的清單
4. **關聯卡片** — 所有相關 WikiLink

### 6.3 注意
各 Wiki 卡片中不得重複「主專案功能疊加」內容，僅保留技術觀念與 Code Snippet。主專案步驟統一由 `project-blueprint.md` 管理。

---

## 7. 步驟 6：更新 index.md 與 log.md

### 7.1 index.md 更新規則

在專案根目錄的 `index.md` 中：

1. 列出所有模組與對應卡片（WikiLink）
2. 標示每張卡片的 `status`（published / stub / deprecated）
3. 按模組分組顯示（HTML / CSS / JS / Design Systems / DevTools & API）
4. 加入 MOC 與專案藍圖的快速連結

### 7.2 log.md 更新規則（Append-only）

`log.md` **僅追加，不修改歷史**。每次編譯完成後，在最上方追加新記錄：

```
## <YYYY-MM-DD>
- 編譯完成: wiki/<模組>/<卡片>.md | source: raw/<檔名>.md | status: published | tags: [<標籤>]
- 新增 MOC: wiki/00-mocs/moc-<名稱>.md | status: published
- 編譯完成: wiki/projects/project-blueprint.md | status: published
```

範例：

```
## 2026-11-24
- 編譯完成: wiki/01-html/html-skeleton-and-encoding.md | source: raw/01-skeleton-and-encoding.md | status: published | tags: [#HTML, #骨架, #編碼]
- 編譯完成: wiki/02-css/css-box-model-and-units.md | source: raw/02-box-model-and-units.md | status: published | tags: [#CSS, #BoxModel]
- 新增 MOC: wiki/00-mocs/moc-browser-rendering-and-perf.md | status: published
- 編譯完成: wiki/projects/project-blueprint.md | status: published
```

---

## 8. Stub 處理規則

對於尚未導入的模組（Design Systems M3、DevTools & API）：

1. 建立 `_stub-<模組>.md` 檔案於對應資料夾
2. Frontmatter 設定 `status: stub`，標籤包含 `#Stub`
3. 內容僅說明預留原因與待辦事項
4. 未來 raw 資料到位後，替換為完整卡片並移除 `#Stub`

---

## 9. WikiLink 連結規則

### 9.1 連結語法
- 同資料夾：`[[卡片標題]]`
- 跨資料夾：`[[資料夾/卡片標題]]` 或直接使用卡片標題（若 vault 中唯一）
- 概念名稱：`[[Box Model]]`、`[[Event Loop]]`、`[[Specificity]]`

### 9.2 反向連結
編寫時請主動在相關頁面加入雙向連結，例如在 `css-box-model-and-units.md` 中加入 `[[moc-browser-rendering-and-perf]]`。

---

## 10. 驗收清單（編譯完成後必須檢查）

- [ ] 所有 18 篇 raw 檔案皆有對應 Wiki 卡片
- [ ] 每張卡片 Frontmatter 完整（id, module, title, status, tags, summary, source, last_updated, related）
- [ ] 每張卡片包含：為什麼 (Why)、核心概念、Code Snippet、避坑對比、關聯連結、標籤
- [ ] 4 份 MOC 均已建立於 `wiki/00-mocs/`
- [ ] `wiki/projects/project-blueprint.md` 已彙整 18 課主專案步驟
- [ ] `index.md` 已更新總目錄與卡片狀態
- [ ] `log.md` 已追加編譯紀錄（僅追加，未修改歷史）
- [ ] `wiki/03-design-systems/_stub-m3-overview.md` 已建立
- [ ] `wiki/05-devtools-and-api/_stub-f12-and-api-overview.md` 已建立

---

*本 SOP 與 SCHEMA.md 為 frontend-wiki 的標準操作規範，如需變更請先更新本檔案。*
