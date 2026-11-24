# SCHEMA.md — frontend-wiki 知識庫規範

本檔案規範 frontend-wiki 知識庫的 Frontmatter 結構、Obsidian [[WikiLink]] 命名原則、MOC 寫法與 [Stub] 標記規範。所有 Wiki 卡片必須遵守本規範。

---

## 1. Frontmatter 結構

每張 Wiki 卡片（`.md`）必須以 YAML Frontmatter 開頭，欄位如下：

```yaml
---
id: 04-03                 # 模組編號-卡片編號，唯一識別碼（範例：JS 模組第 3 篇）
module: js                # 所屬模組：html / css / js / design-systems / devtools-api / cross
title: 函數與作用域      # 中文標題
status: published         # drafted / published / stub / deprecated
tags: [#JS, #函數, #作用域]   # 標籤，小寫英文，以 # 開頭
summary: 函數宣告、函式表達式與區塊/函數作用域差異，含閉包基本概念。  # 一句話摘要
source: raw/03-functions-and-scope.md   # 對應 raw/ 檔案路徑
last_updated: 2026-11-24
related:                  # 手動關聯的相關頁面（WikiLink 名稱，非檔案路徑）
  - [[Closure]]
  - [[Hoisting]]
---
```

### 欄位說明

| 欄位 | 必填 | 說明 |
|------|------|------|
| `id` | ✅ | `NN-XX` 格式，例如 `04-03` 表示第 04 模組第 03 篇。同模組內不得重複。 |
| `module` | ✅ | 必須為 `html`、`css`、`js`、`design-systems`、`devtools-api`、`cross` 或 `projects` 之一。 |
| `title` | ✅ | 中文標題，簡潔明瞭。 |
| `status` | ✅ | `published`（正式發布）、`drafted`（草稿）、`stub`（預留）、`deprecated`（棄用）。 |
| `tags` | ✅ | 陣列格式，每個標籤以 `#` 開頭，例如 `[#JS, #函數]`。常見標籤請參見第 3 节。 |
| `summary` | ✅ | 一句話摘要，不超過 2 行，用於索引頁快速瀏覽。 |
| `source` | ✅ | 對應 `raw/` 中的原始檔案路徑，方便溯源與重新編譯。 |
| `last_updated` | ✅ | ISO 日期格式 `YYYY-MM-DD`。 |
| `related` | ❌ | 陣列，列出與本頁面相關的 WikiLink 名稱，用於建立知識圖譜邊緣。 |

---

## 2. 檔案命名規範

### 2.1 一般 Wiki 卡片

```
<前綴>-<kebab-case>.md
```

| 模組 | 前綴 | 範例 |
|------|------|------|
| HTML | `html-` | `html-skeleton-and-encoding.md` |
| CSS | `css-` | `css-box-model-and-units.md` |
| JavaScript | `js-` | `js-functions-scope-and-closures.md` |
| Design Systems | `m3-` | `m3-color-system.md` |
| DevTools & API | `dev-` | `dev-f12-overview.md` |
| Cross / MOC | `moc-` | `moc-browser-rendering-and-perf.md` |
| 專案藍圖 | `project-` | `project-blueprint.md` |
| Stub | `_stub-` | `_stub-m3-overview.md` |

### 2.2 預留 Stub 檔案

尚未導入的模組使用 `_stub-<模組>.md` 命名，放在對應模組資料夾下：

```
wiki/03-design-systems/_stub-m3-overview.md
wiki/05-devtools-and-api/_stub-f12-and-api-overview.md
```

Stub 檔案 Frontmatter 必須設定 `status: stub`，標籤包含 `#Stub`。

---

## 3. 標籤規範（Tags）

標籤使用小寫英文，以 `#` 開頭，陣列格式。常見標籤清單：

| 標籤 | 用途 |
|------|------|
| `#HTML` | HTML 模組內容 |
| `#CSS` | CSS 模組內容 |
| `#JS` | JavaScript 模組內容 |
| `#MOC` | 主題地圖頁面 |
| `#Pitfalls` | 避坑指南相關 |
| `#A11y` | 無障礙設計 |
| `#Performance` | 效能優化 |
| `#SEO` | 搜尋引擎優化 |
| `#Project` | 專案實作相關 |
| `#Stub` | 預留頁面 |
| `#BoxModel` | CSS 盒模型專題 |
| `#EventLoop` | JS 事件循環專題 |
| `#Specificity` | CSS 權重專題 |

可視需求自行擴充，但必須一致使用 `#` 前綴。

---

## 4. Obsidian [[WikiLink]] 命名原則

### 4.1 連結語法

所有頁面間連結必須使用 Obsidian 雙向連結：

```
[[頁面名稱]]                    # 連結到同資料夾或同 vault 的其他頁面
[[01-html/html-skeleton-and-encoding]]  # 使用相對路徑（推薦，避免名稱衝突）
[[Box Model]]                   # 連結到概念名稱，前提是該頁面存在
```

### 4.2 頁面名稱（顯示名稱）

WikiLink 顯示名稱建議使用**卡片標題**（不含副檔名），例如：

- `[[Box Model]]` → 對應 `wiki/02-css/css-box-model-and-units.md`
- `[[Event Loop]]` → 對應 `wiki/04-js/js-engine-and-event-loop.md`
- `[[Semantic HTML]]` → 對應 `wiki/01-html/html-semantics-and-a11y.md`

若頁面名稱重複，請加上模組前綴區分，例如 `[[HTML: Box Model]]` 與 `[[CSS: Box Model]]`。

### 4.3 反向連結

Obsidian 會自動顯示「反向連結」（誰連結到本頁）。編寫時請主動在相關頁面加入 `[[本頁面標題]]`，以建立雙向連結網路。

---

## 5. MOC（主題地圖）寫法

MOC 放在 `wiki/00-mocs/`，檔名格式為 `moc-<主題關鍵字>.md`。

### 5.1 MOC Frontmatter

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

### 5.2 MOC 內容結構

每份 MOC 必須包含：

1. **模組索引表** — 列出該主題涉及的模組與相關卡片
2. **概念交叉索引** — 跨模組概念對照表（例如 Box Model 同時涉及 CSS 與佈局）
3. **❌ vs ✅ 避坑速查** — 錯誤做法與正確做法並列對比
4. **相關 MOC** — 與其他 MOC 的 WikiLink 連結

---

## 6. [Stub] 標記規範

### 6.1 何時使用 Stub

當模組目錄已建立，但 `raw/` 中尚無對應教材，或 Wiki 卡片尚未編譯完成時，使用 Stub 預留位置。

### 6.2 Stub 寫法

1. 檔名：`_stub-<模組>.md`
2. Frontmatter `status: stub`，標籤包含 `#Stub`
3. 內容僅說明預留原因與待辦事項
4. 未來 raw 資料到位後，替換為完整卡片，移除 `#Stub` 與 `status: stub`

### 6.3 範例（見 templates/stub-template.md）

---

## 7. 索引頁規範（index.md）

`index.md` 放在專案根目錄，必須包含：

1. 全庫總目錄（按模組分組列出所有卡片）
2. 每張卡片的狀態（published / stub / deprecated）
3. 快速導航連結（WikiLink）
4. 學習進度概覽（可選）

---

## 8. 日誌規範（log.md）

`log.md` 放在專案根目錄，**僅追加，不修改歷史**。

格式範例：

```markdown
## 2026-11-24
- 新增 raw: 01-skeleton-and-encoding.md (來源: frontend-mastery/curriculum/01-HTML-Mastery/)
- 編譯完成: wiki/01-html/html-skeleton-and-encoding.md | status: published | tags: #HTML #骨架 #編碼
- 新增 MOC: wiki/00-mocs/moc-layout-and-rwd.md | status: drafted
```

每筆記錄必須包含：日期、動作、涉及檔案、狀態、標籤。

---

*本規範由 agent.md SOP 管理，如需變更請先更新 agent.md 與 SCHEMA.md，再同步調整既有卡片。*
