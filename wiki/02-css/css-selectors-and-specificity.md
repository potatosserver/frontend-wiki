---
id: 02-01
module: css
title: 選擇器與特異度
status: published
tags: ["#CSS", "#選擇器", "#特異度", "#Specificity", "#ID", "#類""]
summary: CSS 標籤選擇器、類選擇器、ID 選擇器的用法與權重計算，解決樣式沒生效的問題。
source: raw/01-intro-and-selectors.md
last_updated: 2026-11-24
related:
  - [[盒模型]]
  - [[MOC: 現代前端避坑指南]]
---

# 選擇器與特異度

> CSS 永遠是在對 HTML 結構進行「索引」和「修飾」，選擇器決定哪些元素會被樣式影響。

## 🎯 為什麼 (Why)

初學者最常遇到「我在 HTML 寫了 class，CSS 也寫了，為什麼沒生效？」——這是 CSS 特異度（Specificity）機制導致的。理解權重才能避免樣式衝突與亂用 `!important`。

## 🧠 核心概念

### 三種基本選擇器

| 選擇器 | 語法 | 說明 | 權重分數 |
|--------|------|------|----------|
| 標籤選擇器 | `p` | 選中所有同標籤元素 | 1 分 |
| 類選擇器 | `.highlight` | 選中 `class="highlight"` | 10 分 |
| ID 選擇器 | `#main-title` | 選中唯一 `id` 元素 | 100 分 |

### 特異度計算範例

```html
<p id="main-p" class="text-blue">你好</p>
```

```css
p { color: red; }            /* 1 分（標籤） */
.text-blue { color: blue; }  /* 10 分（類） */
#main-p { color: green; }    /* 100 分（ID） */
```

**最終結果**：文字為 **綠色**，因為 `#main-p` 權重最高。

### 行內樣式

直接寫在 HTML 標籤的 `style="..."` 權重最強，幾乎能蓋過所有選擇器，專業開發中應盡量避免。

## 💻 Code Snippet

```css
/* 1. 標籤選擇器：所有 body 內容基礎設定 */
body {
    color: #333;
    font-family: sans-serif;
    line-height: 1.6;
}

/* 2. ID 選擇器：專門針對唯一元素 */
#main-title {
    color: #2563eb;
    text-align: center;
    font-size: 2.5rem;
}

/* 3. 類選擇器：所有 class="highlight" 元素 */
.highlight {
    color: #e11d48;
    font-weight: bold;
    background-color: #fff1f2;
}
```

```html
<h1 id="main-title">我的品牌網站</h1>
<p>普通段落，遵循全域設定。</p>
<p class="highlight">使用類選擇器強調。</p>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 為了覆蓋樣式亂用 `!important` | 調整選擇器特異度，或重構 CSS 結構 |
| 同一頁多個相同 `id` | `id` 須全頁唯一，多個用 `class` |
| 樣式沒生效就改行內 `style` | 檢查特異度，確認沒有更高權重選擇器衝突 |
| 只用標籤選擇器控制所有樣式 | 使用 `class` 做元件化樣式，標籤選擇器僅用於基礎重設 |

## 🔗 關聯連結

- [[盒模型]]：CSS 盒模型與單位
- [[MOC: 現代前端避坑指南]]：跨模組避坑對比

## 🏷️ 標籤

#CSS #選擇器 #特異度 #Specificity #ID #類
