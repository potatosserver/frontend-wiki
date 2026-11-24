---
id: 01-05
module: html
title: 語義化 HTML
status: published
tags: ["#HTML", "#語義化", "#A11y", "#SEO", "#Landmark""]
summary: 擺脫 Div Soup，使用 `<header>` `<nav>` `<main>` `<article>` `<section>` `<aside>` `<footer>` 等語義化標籤提升 SEO 與無障礙。
source: raw/05-semantics-and-a11y.md
last_updated: 2026-11-24
related:
  - [[骨架與編碼]]
  - [[文字與基礎標籤]]
  - [[A11y 無障礙與 SEO]]
---

# 語義化 HTML

> 專業工程師關注「這個標籤的意義是什麼」，而非「怎麼讓它看起來像這樣」。

## 🎯 為什麼 (Why)

初學者常陷入 **Div Soup（Div 湯）**，所有內容都用 `<div>` 包裹。雖然視覺正常，但對瀏覽器與爬蟲來說就像一本沒有目錄的書。語義化標籤能提升 SEO 排名、無障礙支援、程式碼可讀性與設備相容性。

## 🧠 核心概念

### 結構級標籤 (Landmarks)

| 標籤 | 意義 | 建議用法 |
|------|------|----------|
| `<header>` | 頁首 | Logo、主導航、搜尋框 |
| `<nav>` | 導航 | 主要導航連結 (Menu) |
| `<main>` | 主內容 | **每頁僅限一個**，核心內容 |
| `<article>` | 獨立文章 | 可單獨抽出也能理解（如部落格文章） |
| `<section>` | 內容分區 | 相關內容分組，通常內部包含 `<h2>` |
| `<aside>` | 側欄 | 與主內容間接相關（廣告、相關連結） |
| `<footer>` | 頁尾 | 版權、聯繫、社交連結 |

### 內容級語義標籤

- `<time>`：日期時間，`<time datetime="2026-07-14">今天</time>`
- `<mark>`：高亮標記
- `<figure>` + `<figcaption>`：圖片與標題綁定

## 💻 Code Snippet

```html
<!-- ❌ Div Soup（糟糕） -->
<div id="header">
  <div class="nav">
    <div class="link">Home</div>
  </div>
</div>

<!-- ✅ 語義化 HTML（專業） -->
<header>
  <nav>
    <ul>
      <li><a href="/">Home</a></li>
    </ul>
  </nav>
</header>
<main>
  <article>
    <h1>文章標題</h1>
    <p>文章內容...</p>
  </article>
</main>
<footer>
  <p>&copy; 2026 My Site</p>
</footer>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 所有區塊都用 `<div>` | 使用 `<header>`、`<main>`、`<section>`、`<footer>` 等 |
| 每頁多個 `<h1>` | 每頁僅限一個 `<h1>`，層級遞減 |
| 圖片沒 `alt` | 所有圖片加上有意義的 `alt` |
| 輸入框沒 `label` | 所有輸入框綁定 `<label>` |

## 🔗 關聯連結

- [[骨架與編碼]]：HTML 基礎骨架
- [[文字與基礎標籤]]：標題層級與列表
- [[A11y 無障礙與 SEO]]：跨模組無障礙與搜尋優化 MOC

## 🏷️ 標籤

#HTML #語義化 #A11y #SEO #Landmark
