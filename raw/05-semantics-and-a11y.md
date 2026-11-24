# 05. 語義化與無障礙 (Semantics and Accessibility)

至此，你已經掌握了所有的 HTML 標籤。但專業工程師與初學者的最大區別在於：**初學者關注「怎麼讓它看起來像這樣」，而專業工程師關注「這個標籤的意義是什麼」。**

本章將教你如何擺脫 `<div>` 依賴症，讓你的網頁對 Google (SEO) 和 視障人士 (A11y) 都極其友好。

---

## 1. 為什麼要追求語義化？ (Semantic HTML)

大多數新手在構建網頁時，會陷入 **「Div 陷阱」 (Div Soup)** —— 所有的東西都用 `<div>` 包裹。
雖然視覺上沒問題，但對瀏覽器和爬蟲來說，這就像是一本書沒有目錄、沒有章節標題，全部都是純文字。

### 語義化標籤的四大好處：
1. **SEO 排名提升**：Google 的爬蟲會優先讀取 `<main>`, `<article>`, `<nav>` 裡的內容，並賦予更高權重。
2. **無障礙支持 (A11y)**：螢幕閱讀器會告訴視障人士：「現在進入導航區 (Nav)」或「這是一個獨立文章 (Article)」。
3. **代碼可讀性**：看到 `<header>` 立即知道是頁首 $\rightarrow$ 比看 `<div class="top-container-inner">` 快得多。
4. **設備兼容性**：某些瀏覽器能根據標籤自動優化顯示效果。

---

## 2. 核心語義化標籤詳解

請嘗試用以下標籤替換你的 `<div>`：

### A. 結構級標籤 (Landmarks)
| 標籤 | 意義 | 建議用法 |
| :--- | :--- | :--- |
| `<header>` | 頁首 | 放置 Logo、主導航、搜尋框。 |
| `<nav>` | 導航 | 放置主要導航連結 (Menu)。 |
| `<main>` | 主內容 | **每頁僅限一個**。包含該頁唯一的、最核心的內容。 |
| `<article>` | 獨立文章 | 內容具有獨立意義，即使單獨抽出來放別處也能被理解 (如部落格文章)。 |
| `<section>` | 內容分區 | 將相關內容分組 (通常內部會包含一個 `<h2>` 標題)。 |
| `<aside>` | 側欄 | 與主內容間接相關的資訊 (如側邊廣告、相關連結)。 |
| `<footer>` | 頁尾 | 版權宣告、聯繫資訊、社交連結。 |

### B. 內容級語義標籤
- `<time>`：定義日期和時間 $\rightarrow$ `<time datetime="2026-07-14">今天</time>`。
- `<mark>`：標記高亮文字 (像用螢光筆畫線)。
- `<figure>` 與 `<figcaption>`：為圖片或圖表提供標題說明 $\rightarrow$ 將圖片與其說明綁定在一起。

---

## 3. 實戰對比：糟糕 vs 專業

### ❌ 糟糕的寫法 (Div Soup)
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>05-semantics-and-a11y</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <div id="header">
  <div class="nav">
    <div class="link">Home</div>
    <div class="link">About</div>
  </div>
</div>
<div id="content">
  <div class="main-title">我的攝影部落格</div>
  <div class="post">
    <div class="post-title">如何拍好風景</div>
    <div class="post-body">...</div>
  </div>
</div>
<div id="footer">© 2026 My Site</div>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

### ✅ 專業的寫法 (Semantic HTML)
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>05-semantics-and-a11y</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <header>
  <nav>
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/about">About</a></li>
    </ul>
  </nav>
</header>
<main>
  <article>
    <h1>我的攝影部落格</h1>
    <h2>如何拍好風景</h2>
    <p>...</p>
  </article>
</main>
<footer>
  <p>&copy; 2026 My Site</p>
</footer>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 🛠️ 主專案功能疊加

最後一步，將你的主專案進行『專業重構』：

1. **標籤替換**：將所有用來做區塊的 `<div>` 替換為 `<header>`, `<main>`, `<section>`, `<article>`, `<footer>`。
2. **結構校對**：確保頁面只有一個 `<h1>` 且層級遞減 (`h1` -> `h2` -> `h3`)。
3. **無障礙檢查**：確認所有圖片都有 `alt`，所有輸入框都有 `label`。

---
<p align="center">
<a href="04-multimedia-and-tables.md">04-multimedia-and-tables ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/html/05-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../02-CSS-Mastery/01-intro-and-selectors.md">01-intro-and-selectors ➡️</a>
</p>
