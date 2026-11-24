# frontend-wiki 總目錄

前端工程師知識庫，依照 HTML / CSS / JS 模組組織，採用 Obsidian `[[WikiLink]]` 雙向連結，支援知識圖譜閱覽。

> 💡 **本索引頁使用標準 Markdown 相對路徑連結**，可在 GitHub 網頁直接點擊跳轉到對應的 Markdown 檔案。wiki 卡片內部則使用 `[[WikiLink]]` 雙向連結，適合在 Obsidian 中開啟查看知識圖譜。

---

## 📚 模組總覽

| 模組 | 資料夾 | 卡片數 | 狀態 |
|------|--------|--------|------|
| HTML | [wiki/01-html/](./wiki/01-html/) | 5 | ✅ published |
| CSS | [wiki/02-css/](./wiki/02-css/) | 6 | ✅ published |
| JavaScript | [wiki/04-js/](./wiki/04-js/) | 7 | ✅ published |
| Design Systems (M3) | [wiki/03-design-systems/](./wiki/03-design-systems/) | 0 | ⚠️ stub |
| DevTools & API | [wiki/05-devtools-and-api/](./wiki/05-devtools-and-api/) | 0 | ⚠️ stub |

---

## 🧩 MOC 主題地圖

| MOC | 檔案 | 說明 |
|-----|------|------|
| A11y 無障礙與 SEO | [moc-a11y-and-seo.md](./wiki/00-mocs/moc-a11y-and-seo.md) | 語義化標籤、alt 文字、label 綁定 |
| 現代前端避坑指南 | [moc-frontend-pitfalls.md](./wiki/00-mocs/moc-frontend-pitfalls.md) | 跨模組錯誤與正確做法對比 |
| 瀏覽器渲染與效能優化 | [moc-browser-rendering-and-perf.md](./wiki/00-mocs/moc-browser-rendering-and-perf.md) | 盒模型、Event Loop、clamp、Mobile-First |
| 版面佈局與響應式設計 | [moc-layout-and-rwd.md](./wiki/00-mocs/moc-layout-and-rwd.md) | Flexbox、Grid、Media Query、Mobile-First |

---

## 📄 卡片列表

### HTML (01-html)

| 卡片 | 檔案 | 標籤 | 狀態 |
|------|------|------|------|
| [骨架與編碼](./wiki/01-html/html-skeleton-and-encoding.md) | `html-skeleton-and-encoding.md` | `#HTML` `#骨架` `#編碼` `#UTF-8` `#SEO` | published |
| [文字與基礎標籤](./wiki/01-html/html-text-links-and-lists.md) | `html-text-links-and-lists.md` | `#HTML` `#標題` `#段落` `#超連結` `#列表` `#SEO` | published |
| [表單與輸入](./wiki/01-html/html-forms-and-validation.md) | `html-forms-and-validation.md` | `#HTML` `#表單` `#輸入` `#驗證` `#A11y` | published |
| [多媒體與表格](./wiki/01-html/html-multimedia-and-tables.md) | `html-multimedia-and-tables.md` | `#HTML` `#圖片` `#影片` `#音訊` `#表格` `#A11y` | published |
| [語義化 HTML](./wiki/01-html/html-semantics-and-a11y.md) | `html-semantics-and-a11y.md` | `#HTML` `#語義化` `#A11y` `#SEO` `#Landmark` | published |

### CSS (02-css)

| 卡片 | 檔案 | 標籤 | 狀態 |
|------|------|------|------|
| [選擇器與特異度](./wiki/02-css/css-selectors-and-specificity.md) | `css-selectors-and-specificity.md` | `#CSS` `#選擇器` `#特異度` `#Specificity` `#ID` `#類` | published |
| [盒模型與單位](./wiki/02-css/css-box-model-and-units.md) | `css-box-model-and-units.md` | `#CSS` `#BoxModel` `#單位` `#rem` `#px` `#vh` `#dvh` `#border-box` | published |
| [定位與層級](./wiki/02-css/css-positioning-and-zindex.md) | `css-positioning-and-zindex.md` | `#CSS` `#定位` `#Positioning` `#Z-Index` `#Relative` `#Absolute` `#Fixed` `#Sticky` | published |
| [Flexbox 佈局](./wiki/02-css/css-flexbox-layout.md) | `css-flexbox-layout.md` | `#CSS` `#Flexbox` `#彈性盒子` `#對齊` `#居中` `#gap` | published |
| [CSS Grid 佈局](./wiki/02-css/css-grid-layout.md) | `css-grid-layout.md` | `#CSS` `#Grid` `#網格` `#二維佈局` `#auto-fill` `#minmax` | published |
| [響應式設計](./wiki/02-css/css-responsive-design.md) | `css-responsive-design.md` | `#CSS` `#RWD` `#響應式` `#MediaQuery` `#clamp` `#Mobile-First` `#Viewport` | published |

### JavaScript (04-js)

| 卡片 | 檔案 | 標籤 | 狀態 |
|------|------|------|------|
| [基礎與變數](./wiki/04-js/js-basics-and-variables.md) | `js-basics-and-variables.md` | `#JS` `#變數` `#let` `#const` `#資料型別` `#JavaScript` | published |
| [運算符與控制流程](./wiki/04-js/js-operators-and-control-flow.md) | `js-operators-and-control-flow.md` | `#JS` `#運算符` `#if` `#else` `#迴圈` `#for` `#while` `#布林` | published |
| [函數與作用域](./wiki/04-js/js-functions-scope-and-closures.md) | `js-functions-scope-and-closures.md` | `#JS` `#函數` `#箭頭函數` `#作用域` `#閉包` `#Closure` | published |
| [DOM 操作](./wiki/04-js/js-dom-manipulation.md) | `js-dom-manipulation.md` | `#JS` `#DOM` `#querySelector` `#addEventListener` `#DarkMode` `#createElement` | published |
| [陣列與物件](./wiki/04-js/js-arrays-objects-and-hof.md) | `js-arrays-objects-and-hof.md` | `#JS` `#陣列` `#物件` `#Object` `#Array` `#map` `#filter` `#forEach` `#高階函數` | published |
| [異步與 Promise](./wiki/04-js/js-async-and-promises.md) | `js-async-and-promises.md` | `#JS` `#異步` `#Async` `#Await` `#Promise` `#fetch` `#API` | published |
| [引擎與事件循環](./wiki/04-js/js-engine-and-event-loop.md) | `js-engine-and-event-loop.md` | `#JS` `#EventLoop` `#單執行緒` `#CallStack` `#TaskQueue` `#Microtask` `#Macrotask` | published |

---

## 🚀 專案實作

| 項目 | 檔案 | 說明 |
|------|------|------|
| [個人品牌網站實戰藍圖](./wiki/projects/project-blueprint.md) | `wiki/projects/project-blueprint.md` | 18 篇疊加任務的驗收清單與實作路線圖 |

---

## 📋 預留 Stub (待補完)

| 項目 | 檔案 | 說明 |
|------|------|------|
| [M3 設計系統](./wiki/03-design-systems/_stub-m3-overview.md) | `wiki/03-design-systems/_stub-m3-overview.md` | 預留 M3 色彩、組件、動畫內容 |
| [F12 與 API](./wiki/05-devtools-and-api/_stub-f12-and-api-overview.md) | `wiki/05-devtools-and-api/_stub-f12-and-api-overview.md` | 預留 F12、官方 API、逆向工程、CORS 內容 |

---

## 📖 如何閱讀

所有 wiki 卡片內部使用 Obsidian `[[WikiLink]]` 雙向連結。建議在 Obsidian 中開啟本資料夾，於「圖譜視圖」查看知識關聯，或使用「反向連結」查看哪些頁面引用了當前概念。

在 GitHub 網頁中，可直接點擊上方各表格中的 **藍色超連結** 跳轉到對應的 Markdown 檔案。

---

*維護機制：採用標準 LLM Wiki 架構，詳見 `agent.md` 與 `SCHEMA.md`。編譯紀錄請參見 `log.md`。*
