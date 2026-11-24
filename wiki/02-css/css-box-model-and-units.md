---
id: 02-02
module: css
title: 盒模型與單位
status: published
tags:
  - "#CSS"
  - "#BoxModel"
  - "#單位"
  - "#rem"
  - "#px"
  - "#vh"
  - "#dvh"
  - "#border-box"
summary: CSS 盒模型四層結構、content-box 與 border-box 差異、rem/em/vw/vh/dvh 單位選擇指南。
source: raw/02-box-model-and-units.md
last_updated: 2026-11-24
related:
  - "[[MOC: 瀏覽器渲染與效能優化]]"
  - "[[MOC: 版面佈局與響應式設計]]"
---

# 盒模型與單位

> 瀏覽器眼中，每個元素都是一個透明矩形盒子。理解盒模型與單位是精確控制佈局的基礎。

## 🎯 為什麼 (Why)

「設定寬度 100% 加上 Padding 後網頁出現水平滾動條」是初學者最常見的噩夢。根本原因是不了解 `content-box` 與 `border-box` 的差異，以及單位選擇不當導致無法響應式。

## 🧠 核心概念

### 盒模型四層（從內到外）

```
+---------------------------------------+
| Margin (外邊距) - 盒子與盒子之間距離 |
+---------------------------------------+
| Border (邊框) - 包裹在內邊距外的線條 |
+---------------------------------------+
| Padding (內邊距) - 內容與邊框間距     |
+---------------------------------------+
| Content (內容) - 實際文字或圖片       |
+---------------------------------------+
```

### `content-box` vs `border-box`

| 屬性 | 邏輯 | 實際總寬度公式 | 結果 |
|------|------|---------------|------|
| `content-box` (預設) | `width` 僅指 Content | `width + padding + border` | `width: 100%` + padding → 佈局爆掉 |
| `border-box` (專業標準) | `width` 是整個盒子總寬 | 瀏覽器自動壓縮 Content | `width: 100%` 永遠是 100%，佈局穩固 |

### 專業習慣：全域重設

```css
* {
    box-sizing: border-box;
}
```

### CSS 單位系統

| 單位 | 類型 | 說明 | 推薦場景 |
|------|------|------|----------|
| `px` | 絕對 | 固定不變 | 邊框 `1px`、圖標大小 |
| `rem` | 相對 (根) | 相對於 HTML 根字體 (預設 16px) | 基礎字體大小，支援使用者縮放 (A11y) |
| `em` | 相對 (父) | 相對於父元素字體 | 元件內邊距隨字體比例縮放 |
| `vw` / `vh` | 相對 (視窗) | 視窗寬/高的 1% | 滿版背景 |
| `dvh` / `dvw` | 動態視口 | 動態計算可見區域 | **手機端全螢幕，避免地址欄遮擋** |
| `%` | 相對 (父) | 相對於父元素寬/高 | 佈局寬度 |

### `100vh` 在手機上的陷阱

手機瀏覽器的 `100vh` 會包含地址欄高度，導致頁面底部被遮住。**專業做法**：使用 `100dvh`（動態視口高度），它會根據地址欄顯示/隱藏狀態實時計算真正可見區域。

## 💻 Code Snippet

```css
/* 全域盒模型重設 */
* {
    box-sizing: border-box;
}

/* 基礎字體：使用 rem 支援 A11y 縮放 */
html {
    font-size: 16px;
}

body {
    font-size: 1rem;      /* 16px */
    line-height: 1.6;
}

/* 滿屏 Hero：使用 100dvh 避免手機地址欄遮擋 */
.hero {
    height: 100dvh;
    display: flex;
    justify-content: center;
    align-items: center;
}

/* 佈局寬度：使用 % 或 max-width 限制 */
.container {
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
}
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 未設 `box-sizing: border-box` | 全域加上 `* { box-sizing: border-box; }` |
| 手機端用 `100vh` | 改用 `100dvh` 動態視口高度 |
| 全站只用 `px` 做字體 | 基礎字體用 `rem`，支援瀏覽器縮放 |
| 佈局寬度固定 `1200px` | 用 `width: 90%; max-width: 1200px;` |

## 🔗 關聯連結

- [[MOC: 瀏覽器渲染與效能優化]]：跨模組效能主題
- [[MOC: 版面佈局與響應式設計]]：Flexbox/Grid 與 RWD

## 🏷️ 標籤

#CSS #BoxModel #單位 #rem #px #vh #dvh #border-box
