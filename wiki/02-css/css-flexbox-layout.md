---
id: 02-04
module: css
title: Flexbox 佈局
status: published
tags:
  - "#CSS"
  - "#Flexbox"
  - "#彈性盒子"
  - "#對齊"
  - "#居中"
  - "#gap"
summary: Flexbox 啟動方式、主軸與交叉軸對齊、justify-content/align-items/flex 屬性，實作完美對齊與自適應伸縮。
source: raw/04-flexbox-practical.md
last_updated: 2026-11-24
related:
  - "[[CSS Grid 佈局]]"
  - "[[MOC: 版面佈局與響應式設計]]"
---

# Flexbox 佈局

> Flexbox (彈性盒子) 是現代前端開發的靈魂，核心目標只有一個：不需要計算像素，就能實現完美的對齊與分佈。

## 🎯 為什麼 (Why)

傳統的 `margin-left: 20%` 或 `text-align: center` 在不同螢幕上容易跑掉。Flexbox 提供宣告式的對齊方式，讓佈局更穩定、更容易維護。

## 🧠 核心概念

### 啟動 Flex 模式

```css
.parent {
    display: flex;
}
```

啟動後，子元素成為「彈性項目」，受 `justify-content`（主軸）與 `align-items`（交叉軸）控制。

### 主軸與交叉軸

| 屬性 | 軸向 | 常用值 | 說明 |
|------|------|--------|------|
| `justify-content` | 主軸 (預設水平) | `flex-start`, `flex-end`, `center`, `space-between`, `space-around` | 控制沿主軸的對齊與分佈 |
| `align-items` | 交叉軸 (預設垂直) | `flex-start`, `flex-end`, `center`, `baseline`, `stretch` | 控制垂直於主軸的對齊 |

### 居中標準配方

```css
.center-box {
    display: flex;
    justify-content: center;   /* 水平居中 */
    align-items: center;       /* 垂直居中 */
    height: 100dvh;
}
```

### `flex` 自適應伸縮

```css
.input-field {
    flex: 1;   /* 佔滿所有剩餘空間 */
}
.btn {
    flex: 0;   /* 保持原始大小，不伸縮 */
}
```

### `gap` 屬性

現代 CSS 最強屬性之一，直接設定 Flex 子元素間距，無需對每個子元素設 margin。

```css
.nav-links {
    display: flex;
    gap: 20px;
}
```

## 💻 Code Snippet

```css
/* 導航欄：Logo 左、連結右，垂直置中 */
.nav-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    height: 60px;
    background: white;
}

.nav-links {
    display: flex;
    list-style: none;
    gap: 20px;
}

/* Hero Section 絕對居中 */
.hero {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    height: 100dvh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
}
```

```html
<nav class="nav-container">
    <div class="logo">我的品牌</div>
    <ul class="nav-links">
        <li><a href="#">首頁</a></li>
        <li><a href="#">作品</a></li>
        <li><a href="#">聯絡</a></li>
    </ul>
</nav>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 用 `margin-left: 20%` 做對齊 | 用 `justify-content: space-between` 或 `gap` |
| 每個子元素分別設 `margin` 間距 | 統一在父容器用 `gap` |
| 垂直居中用大量 `padding` 猜測 | 用 `display: flex; align-items: center` |
| 忽略 `100vh` 手機地址欄問題 | 改用 `100dvh` |

## 🔗 關聯連結

- [[CSS Grid 佈局]]：二維網格佈局
- [[MOC: 版面佈局與響應式設計]]：Flexbox/Grid 與 RWD

## 🏷️ 標籤

#CSS #Flexbox #彈性盒子 #對齊 #居中 #gap
