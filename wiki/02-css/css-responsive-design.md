---
id: 02-06
module: css
title: 響應式設計
status: published
tags:
  - "#CSS"
  - "#RWD"
  - "#響應式"
  - "#MediaQuery"
  - "#clamp"
  - "#Mobile-First"
  - "#Viewport"
summary: 響應式設計核心：viewport 設定、@media 媒體查詢、clamp/min/max 流體函數、Mobile-First 策略。
source: raw/06-responsive-design.md
last_updated: 2026-11-24
related:
  - "[[CSS Grid 佈局]]"
  - "[[Flexbox 佈局]]"
  - "[[MOC: 版面佈局與響應式設計]]"
---

# 響應式設計

> 讓網頁在 iPhone、iPad、MacBook 與 4K 螢幕上都提供完美閱讀體驗，內容隨螢幕寬度「流動」而非簡單縮小。

## 🎯 為什麼 (Why)

裝置多元化時代，專業網頁必須適應所有螢幕。沒有響應式設計，手機使用者必須左右滾動才能看完整內容，體驗極差。

## 🧠 核心概念

### Viewport 設定（基礎）

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

沒加這行，手機瀏覽器會模擬 PC 寬度並縮小頁面，文字變得像螞蟻一樣小。

### @media 媒體查詢

```css
/* 預設樣式 (手機優先) */
.container {
    flex-direction: column;
}

/* 螢幕寬度大於 600px 時 (平板與 PC) */
@media (min-width: 600px) {
    .container {
        flex-direction: row;
    }
}
```

### Mobile-First 策略

1. **先寫手機版樣式**（最簡單單列佈局）
2. **用 `@media (min-width: ...)`** 隨螢幕變寬逐漸增加複雜度

**為什麼**：手機最受限，先搞定能確保基本可用性；程式碼更簡潔，不需要在 PC 版寫完後再用 `max-width` 去覆蓋。

### 流體函數

| 函數 | 說明 | 範例 |
|------|------|------|
| `clamp(最小, 理想, 最大)` | 字體隨螢幕縮放，但不超出範圍 | `font-size: clamp(1.5rem, 5vw, 3rem)` |
| `min()` | 取較小值 | `width: min(90%, 1200px)` |
| `max()` | 取較大值 | `width: max(50%, 300px)` |

## 💻 Code Snippet

```css
/* 手機優先：單列佈局 */
.profile-card {
    background: white;
    padding: 30px;
    border-radius: 20px;
    text-align: center;
    width: 90%;           /* 手機：佔 90% 寬度 */
    max-width: 400px;     /* PC：最大 400px */
    margin: 0 auto;
}

/* 流體標題：隨螢幕平滑縮放 */
h1 {
    font-size: clamp(1.5rem, 5vw, 3rem);
}

/* 平板與 PC：增加內距與邊框 */
@media (min-width: 600px) {
    .profile-card {
        padding: 50px;
        border: 2px solid #2563eb;
    }
}
```

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<div class="profile-card">
    <h1>Andrew Cho</h1>
    <p>前端工程師 | 視覺設計師</p>
</div>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 先寫 PC 版再用 `max-width` 覆蓋手機 | 採用 Mobile-First，從 `min-width` 漸進增強 |
| 固定寬度 `1200px` 佈局 | 用 `width: 90%; max-width: 1200px` 流體寬度 |
| 字體固定 `24px` | 用 `clamp(1.5rem, 5vw, 3rem)` 流體縮放 |
| 忘記 `<meta viewport>` | 必須在 `<head>` 加入 viewport 標籤 |

## 🔗 關聯連結

- [[Flexbox 佈局]]：彈性盒子佈局
- [[CSS Grid 佈局]]：二維網格佈局
- [[MOC: 版面佈局與響應式設計]]：跨模組 RWD 主題

## 🏷️ 標籤

#CSS #RWD #響應式 #MediaQuery #clamp #Mobile-First #Viewport
