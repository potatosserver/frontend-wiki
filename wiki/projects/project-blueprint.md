---
id: proj-01
module: projects
title: 個人品牌網站實戰藍圖
status: published
tags: [#Project, #Blueprint, #HTML, #CSS, #JS]
summary: 18 篇疊加任務的驗收清單與實作路線圖，彙整所有主專案功能步驟。
last_updated: 2026-11-24
related:
  - [[html-semantics-and-a11y]]
  - [[css-flexbox-layout]]
  - [[css-grid-layout]]
  - [[css-responsive-design]]
  - [[js-dom-manipulation]]
  - [[js-arrays-objects-and-hof]]
  - [[js-async-and-promises]]
---

# 個人品牌網站實戰藍圖與驗收清單

本藍圖彙整 18 課 HTML/CSS/JS 的「主專案功能疊加」步驟，目標是建立一個專業的個人品牌網站。各 Wiki 卡片專注技術觀念，主專案步驟統一在此彙整。

## 📌 專案概述

建立一個具備響應式佈局、深色模式、作品集篩選、異步數據載入與無障礙支援的個人品牌網站，適用於個人複習與開發速查手冊。

## 🗺️ 階段規劃

| 階段 | 任務 | 相關卡片 | 驗收標準 |
|------|------|---------|---------|
| 第 1 階段：HTML 骨架 | 建立 `index.html`，設定 UTF-8 編碼與 `lang="zh-Hant"`，寫出 `<head>` 與 `<body>` 基礎結構 | [[html-skeleton-and-encoding]] | 頁面可正確解碼，中文無亂碼，語言標籤正確 |
| 第 2 階段：內容標籤 | 建立 Hero Section (`<h1>` + `<p>`)、關於我 (`<ul>` 技能列表)、導航連結 (`<a target="_blank">`) | [[html-text-links-and-lists]] | 標題層級正確（每頁一個 `<h1>`），超連結在新分頁開啟 |
| 第 3 階段：聯絡表單 | 建立 `<form method="POST">`，實作姓名/電子郵件/訊息欄位，加上 `<label>` 綁定與 `required` 驗證 | [[html-forms-and-validation]] | 所有輸入框有標籤，必填欄位無法跳過提交 |
| 第 4 階段：多媒體與表格 | 作品集區塊加入 `` 與有意義的 `alt`，建立技術對比 `<table>`，嵌入 `<video>` 介紹影片 | [[html-multimedia-and-tables]] | 所有圖片有 `alt`，表格使用 `<th>` 標題行 |
| 第 5 階段：語義化重構 | 將 `<div>` 區塊替換為 `<header>`、`<nav>`、`<main>`、`<section>`、`<article>`、`<footer>` | [[html-semantics-and-a11y]] | 頁面只有一個 `<h1>`，標籤層級遞減，通過無障礙檢查 |
| 第 6 階段：CSS 基礎樣式 | 使用 `:root` 定義主題色，`*` 設定 `box-sizing: border-box`，`body` 設定字體與行高 `1.6` | [[css-selectors-and-specificity]]<br>[[css-box-model-and-units]] | 全站盒模型一致，字體可縮放 (rem) |
| 第 7 階段：Flexbox 佈局 | 導航欄使用 `justify-content: space-between` (Logo 左、連結右)，Hero Section 絕對居中 | [[css-flexbox-layout]] | 導航欄兩端對齊，Hero 在螢幕正中央 |
| 第 8 階段：CSS Grid 佈局 | 建立 `works-grid` 容器，使用 `repeat(auto-fill, minmax(250px, 1fr))` 自適應列數，核心作品 `grid-column: span 2` | [[css-grid-layout]] | 作品集牆在手機/平板/PC 上列數自動調整，無橫向捲軸 |
| 第 9 階段：響應式設計 | 加入 `<meta viewport>`，使用 `clamp()` 流體標題，`@media (min-width: ...)` 漸進增強佈局 | [[css-responsive-design]] | 跨裝置顯示正常，無水平滾動條，字體平滑縮放 |
| 第 10 階段：JS 基礎變數 | 在 `js-playground.html` 驗證變數與資料型別，建立 `myCity` 與 `currentTemp` | [[js-basics-and-variables]] | 變數宣告正確，`const`/`let` 使用得宜 |
| 第 11 階段：JS 控制流程 | 實作偶數過濾器、成績分級系統、`while` 倒數計時 | [[js-operators-and-control-flow]] | 邏輯判斷正確，無死迴圈 |
| 第 12 階段：JS 函數與閉包 | 實作 `calculatePrice(price, tax)` 函數、箭頭函數改寫、私有計數器閉包 | [[js-functions-scope-and-closures]] | 函數可重複呼叫，閉包狀態私有 |
| 第 13 階段：DOM 操作 | 實作主題切換按鈕 (`.dark-mode` 類名切換)、動態問候標題、表單 submit 攔截 (`preventDefault`) | [[js-dom-manipulation]] | 點擊按鈕背景切換，表單不跳頁且在 Console 印出數據 |
| 第 14 階段：陣列與物件篩選 | 建立 `projects` 陣列 (6 個作品物件)，實作分類按鈕篩選，`.map()` 動態渲染作品卡片 | [[js-arrays-objects-and-hof]] | 點擊分類按鈕正確篩選，作品由 JS 動態生成 |
| 第 15 階段：異步數據載入 | Hero Section 加入隨機金句區塊，`async/await` 抓取 API 數據，顯示 Loading 狀態與錯誤處理 | [[js-async-and-promises]] | 數據載入時顯示 Loading，失敗時顯示錯誤訊息而非空白 |
| 第 16 階段：效能優化 | 非緊急 `<script>` 加上 `defer`，避免主執行緒阻塞，繁重計算用 `setTimeout(..., 0)` 拆分 | [[js-engine-and-event-loop]] | HTML 先渲染，JS 後執行，頁面無卡死 |

## ✅ 驗收清單 (Checklist)

- [ ] HTML 通過 W3C 驗證，無語法錯誤
- [ ] CSS 無重複選擇器，Specificity 合理，未濫用 `!important`
- [ ] JS 無全域變數污染，使用 `const`/`let` 而非 `var`
- [ ] 所有圖片皆有有意義的 `alt` 屬性 (A11y)
- [ ] 所有輸入框皆有對應的 `<label>` 綁定 (A11y)
- [ ] 行動裝置檢視正常，無橫向捲軸 (RWD)
- [ ] 深色模式切換正常運作 (DOM 操作)
- [ ] 作品集分類篩選正確 (陣列高階函數)
- [ ] API 載入顯示 Loading，失敗有錯誤訊息 (異步處理)
- [ ] 頁面首次渲染無白屏，`<script>` 加上 `defer` (效能)

## 🔗 關聯卡片

- [[html-skeleton-and-encoding]]
- [[html-text-links-and-lists]]
- [[html-forms-and-validation]]
- [[html-multimedia-and-tables]]
- [[html-semantics-and-a11y]]
- [[css-selectors-and-specificity]]
- [[css-box-model-and-units]]
- [[css-flexbox-layout]]
- [[css-grid-layout]]
- [[css-responsive-design]]
- [[js-basics-and-variables]]
- [[js-operators-and-control-flow]]
- [[js-functions-scope-and-closures]]
- [[js-dom-manipulation]]
- [[js-arrays-objects-and-hof]]
- [[js-async-and-promises]]
- [[js-engine-and-event-loop]]
