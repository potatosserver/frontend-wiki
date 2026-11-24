---
id: 02-03
module: css
title: 定位與層級
status: published
tags:
  - "#CSS"
  - "#定位"
  - "#Positioning"
  - "#Z-Index"
  - "#Relative"
  - "#Absolute"
  - "#Fixed"
  - "#Sticky"
summary: CSS position relative/absolute/fixed/sticky 用法與 z-index 層疊順序，含「父層 Relative 子層 Absolute」組合技。
source: raw/03-positioning-and-zindex.md
last_updated: 2026-11-24
related:
  - "[[盒模型與單位]]"
  - "[[Flexbox 佈局]]"
  - "[[MOC: 現代前端避坑指南]]"
---

# 定位與層級

> 元素預設依「自然流動」排列，當需要精確放置（如固定導航欄、卡片右上角標籤）時，使用 CSS 定位強行改變座標。

## 🎯 為什麼 (Why)

依賴自然流動無法實作「固定在頂部的導航欄」或「卡片右上角的 New 標籤」。定位讓開發者能精確控制元素座標與疊加順序。

## 🧠 核心概念

### 五種 position 值

| 值 | 行為 | 脫離文檔流 | 常見用途 |
|----|------|-----------|----------|
| `static` (預設) | 自然流動 | 否 | 預設佈局 |
| `relative` | 相對原位移動 | 否 | 作為絕對定位的座標原點 |
| `absolute` | 相對最近定位祖先定位 | 是 | 卡片標籤、彈出視窗 |
| `fixed` | 相對視窗固定 | 是 | 固定導航欄、懸浮按鈕 |
| `sticky` | 達到閾值後固定 | 否 | 目錄標題黏住頂部 |

### 核心組合技：父層 Relative + 子層 Absolute

```html
<div class="card">
    <span class="badge">New</span>
    <img src="project.jpg" alt="作品">
    <p>我的作品名稱</p>
</div>
```

```css
.card {
    position: relative;   /* 成為子層的座標原點 */
    width: 300px;
}

.badge {
    position: absolute;   /* 可在父層內隨意移動 */
    top: 10px;
    right: 10px;
    background: red;
    color: white;
}
```

**⚠️ 關鍵**：若父層沒有 `position: relative`，子層 `absolute` 會一直往上找直到 `<body>`，標籤會飛到頁面頂端。

### z-index 層疊順序

- 數字越大 → 越靠近使用者（越在上層）
- `z-index` 僅在有 `position` (relative/absolute/fixed/sticky) 的元素上生效
- 受限於 **層疊上下文 (Stacking Context)**：父層被壓下，子層再高也沒用

```css
.modal-overlay { position: fixed; z-index: 100; }
.modal-content { position: fixed; z-index: 200; } /* 內容在遮罩上面 */
```

## 💻 Code Snippet

```css
/* 固定導航欄 */
.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    height: 60px;
    background: #2563eb;
    z-index: 1000;
}

/* 卡片定位組合 */
.card {
    position: relative;
    width: 250px;
    border: 1px solid #ddd;
    border-radius: 12px;
    overflow: hidden;
}

.badge {
    position: absolute;
    top: 12px;
    right: 12px;
    background: #e11d48;
    color: white;
    padding: 4px 8px;
    font-size: 12px;
    border-radius: 4px;
    z-index: 10;
}
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 子層 `absolute` 但父層沒 `relative` | 父層加上 `position: relative` |
| `z-index: 9999` 都沒效 | 檢查元素是否有 `position`，且父層未建立較低層疊上下文 |
| 所有浮動元素都用 `fixed` | 只需固定視窗時用 `fixed`，滾動後黏住用 `sticky` |
| 導航欄 z-index 太低被內容遮擋 | 導航欄設 `z-index: 1000` 以上 |

## 🔗 關聯連結

- [[盒模型與單位]]：CSS 盒模型基礎
- [[Flexbox 佈局]]：彈性盒子佈局
- [[MOC: 現代前端避坑指南]]：跨模組避坑對比

## 🏷️ 標籤

#CSS #定位 #Positioning #Z-Index #Relative #Absolute #Fixed #Sticky
