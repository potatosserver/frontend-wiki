---
id: 02-05
module: css
title: CSS Grid 佈局
status: published
tags: ["#CSS", "#Grid", "#網格", "#二維佈局", "#auto-fill", "#minmax""]
summary: CSS Grid 顯示方式、grid-template-columns、1fr 分數單位、auto-fill/minmax 自適應列數，適合二維佈局。
source: raw/05-grid-practical.md
last_updated: 2026-11-24
related:
  - [[Flexbox 佈局]]
  - [[MOC: 版面佈局與響應式設計]]
---

# CSS Grid 佈局

> Flexbox 處理「一條線」佈局，CSS Grid 處理「整個平面」佈局。同時控制行與列時，Grid 是唯一正確選擇。

## 🎯 為什麼 (Why)

用 Flexbox 做作品集牆（每行 3 卡、高度一致）很困難，需為每個卡片設寬度且難控制行列間距。Grid 原生支援二維佈局，讓作品集牆、儀表板等佈局變得簡單。

## 🧠 核心概念

### 啟動 Grid 模式

```css
.works-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}
```

### 關鍵屬性

| 屬性 | 說明 | 範例 |
|------|------|------|
| `grid-template-columns` | 定義列數與寬度 | `repeat(3, 1fr)` = 三個等寬列 |
| `1fr` (Fractional Unit) | 分數單位，自動均分剩餘空間 | `1fr 1fr 1fr` |
| `gap` | 行與列間距 | `gap: 20px` |
| `grid-column` | 元素橫跨幾列 | `grid-column: span 2` |

### 自適應列數 (無需 Media Query)

```css
.works-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
}
```

- `minmax(250px, 1fr)`：每格最小 250px，最大 1fr
- 結果：PC 上可能 4 列、平板 2 列、手機 1 列，**完全不需要 Media Query**

### 橫跨多列

```css
.work-card:first-child {
    grid-column: span 2;   /* 橫跨 2 列，強調核心作品 */
}
```

## 💻 Code Snippet

```css
.works-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
    max-width: 1200px;
    margin: 0 auto;
}

.work-card {
    background: white;
    border: 1px solid #ddd;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    transition: transform 0.2s;
}

.work-card:hover {
    transform: translateY(-5px);
}

.featured {
    grid-column: span 2;
    background: #eef2ff;
    border: 2px solid #2563eb;
}
```

```html
<div class="works-grid">
    <div class="work-card featured">
        <h3>核心專案 A</h3>
        <p>這是最重要的作品，橫跨兩列。</p>
    </div>
    <div class="work-card"><h3>作品 B</h3><p>描述...</p></div>
    <div class="work-card"><h3>作品 C</h3><p>描述...</p></div>
    <!-- 更多卡片... -->
</div>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 用 Flexbox 強行做每行 3 卡 | 用 Grid `repeat(auto-fill, minmax(...))` |
| 為每個斷點寫 Media Query 調整列數 | 用 `auto-fill` 自動適應螢幕寬度 |
| 核心作品沒視覺差異 | 用 `grid-column: span 2` 讓重要作品更大 |
| Grid 子元素沒間距 | 在父容器加 `gap: 20px` |

## 🔗 關聯連結

- [[Flexbox 佈局]]：一維彈性佈局
- [[MOC: 版面佈局與響應式設計]]：Flexbox/Grid 與 RWD

## 🏷️ 標籤

#CSS #Grid #網格 #二維佈局 #auto-fill #minmax
