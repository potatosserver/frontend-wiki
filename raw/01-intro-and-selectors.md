# 01. 改變顏色與文字 (Intro and Selectors)

想像一下，如果你現在打開你的網站，看到的只有黑白文字和白色背景 $\rightarrow$ 這就像是一棟只有水泥牆、沒有刷漆的房子。

CSS (Cascading Style Sheets) 的目的就是讓你能夠**精確地控制**頁面上任何一個元素的視覺外觀。但請記住：**CSS 永遠是在對 HTML 的結構進行「索引」和「修飾」。**

---

## 1. 視覺實驗：如何讓文字變色？

不要去管複雜的定義，我們先來體驗一次完整的「HTML $\rightarrow$ CSS」流程。

### ⚡️ 實驗 A：針對「所有」相同標籤 (標籤選擇器)

如果你想讓頁面上**所有的段落**都變成藍色，你不需要一個一個設定，只需要告訴瀏覽器「所有的 `<p>` 標籤都要變色」。

**第一步：在 HTML 中寫入內容**
```html
<p>我是第一段文字。</p>
<p>我是第二段文字。</p>
```

**第二步：在 CSS 中指定選擇器**
```css
p {
    color: blue;
}
```

**💡 發生了什麼事？**
- `p` $\rightarrow$ 這是 **「標籤選擇器 (Tag Selector)」**。它直接對準 HTML 的標籤名稱。
- **結果**：所有 `<p>` 標籤都會同步變藍。這在設定全站基礎字體時非常有用。

---

## 2. 精確控制：我想只改變「這一個」元素

如果你想讓某些文字是藍色，某些是紅色，你就不能用標籤選擇器。這時候我們需要在 HTML 中加上一個 **「標記」**，然後在 CSS 中根據這個標記來抓取。

### ⚡️ 實驗 B：使用「類標記」 (類選擇器)

**第一步：在 HTML 中使用 `class` 屬性**
`class` 就像是一個貼紙，你可以把它貼在任何標籤上。
```html
<p class="highlight">我是重要的文字 (藍色)</p>
<p>我是普通文字 (黑色)</p>
```

**第二步：在 CSS 中使用 `.` 來選中類標記**
```css
.highlight {
    color: blue;
    font-weight: bold;
}
```

**💡 關鍵對應：**
- **HTML** $\rightarrow$ `class="highlight"` (貼上標記)
- **CSS** $\rightarrow$ `.highlight` (根據標記選中 $\rightarrow$ 注意必須以 `.` 開頭)
- **結果**：只有貼了 `highlight` 標籤的元素會變色。這是工業界最常用的方式。

### ⚡️ 實驗 C：使用「唯一 ID」 (ID 選擇器)

如果你需要一個在全頁面中**絕對唯一**的元素（例如：主標題），請使用 `id`。

**第一步：在 HTML 中使用 `id` 屬性**
```html
<h1 id="main-title">我的品牌網站</h1>
```

**第二步：在 CSS 中使用 `#` 來選中 ID**
```css
#main-title {
    color: #2563eb;
    text-align: center;
}
```

**💡 關鍵對應：**
- **HTML** $\rightarrow$ `id="main-title"` (設定唯一身分證)
- **CSS** $\rightarrow$ `#main-title` (根據 ID 選中 $\rightarrow$ 注意必須以 `#` 開頭)

---

## 3. 權重之謎：為什麼我的樣式沒生效？

這是初學者最容易崩潰的地方：**「我在 HTML 寫了 class，CSS 也寫了，為什麼它還是沒變色？」**

這就是 CSS 的 **權重 (Specificity)** 機制。如果同一個 HTML 元素被多個 CSS 規則選中，瀏覽器會根據「精確度」來決定誰贏。

**權重對照表 (由高到低)：**
1. **行內樣式** (直接寫在 HTML 標籤的 `style="..."` 裡) $\rightarrow$ **最強** $\rightarrow$ 幾乎能蓋過所有東西。
2. **ID 選擇器 (`#id`)** $\rightarrow$ **很強** $\rightarrow$ 因為 ID 是唯一的。
3. **類選擇器 (`.class`)** $\rightarrow$ **中等** $\rightarrow$ 最常用的平衡選擇。
4. **標籤選擇器 (`p`, `h1`)** $\rightarrow$ **最弱** $\rightarrow$ 僅用於基礎設定。

**🚀 實戰對比：誰會贏？**
```html
<!-- HTML -->
<p id="main-p" class="text-blue">你好</p>
```
```css
/* CSS */
p { color: red; }            /* 1分 (標籤) */
.text-blue { color: blue; }  /* 10分 (類) */
#main-p { color: green; }    /* 100分 (ID) */
```
- **最終結果**：文字會是 **綠色** $\rightarrow$ 因為 `#main-p` 的權重最高。

---

## 🚀 全量實作範例：基礎配色系統

請建立以下兩個檔案，觀察 HTML 標籤與 CSS 選擇器是如何協同工作的。

**檔案 1：`index.html`**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>視覺實驗 01</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- 1. 使用 ID 選中唯一標題 -->
    <h1 id="main-title">我的品牌網站</h1>
    
    <!-- 2. 使用標籤選擇器控制所有段落 -->
    <p>這是一個普通的段落，會遵循全域設定。</p>
    
    <!-- 3. 使用 class 選中特定強調段落 -->
    <p class="highlight">這段文字使用了類選擇器，所以會呈現強調色。</p>
</body>
</html>
```

**檔案 2：`style.css`**
```css
/* 1. 標籤選擇器：所有 body 內容的基礎設定 */
body {
    color: #333;
    font-family: sans-serif;
    line-height: 1.6;
}

/* 2. ID 選擇器：專門針對 #main-title 這個唯一元素 */
#main-title {
    color: #2563eb;
    text-align: center;
    font-size: 2.5rem;
}

/* 3. 類選擇器：只要有 class="highlight" 的元素都會生效 */
.highlight {
    color: #e11d48;
    font-weight: bold;
    background-color: #fff1f2;
}
```

---

## 🛠️ 主專案功能疊加

現在，請在你的主專案中實作基礎樣式：

1. **定義主題色**：使用 `:root` 設定主色、文字色與背景色。
2. **全域重設**：使用 `*` 設定 `box-sizing: border-box` 並清除預設 margin/padding。
3. **基礎排版**：設定 `body` 的字體 (推薦 Inter) 與行高 `1.6`。

---
<p align="center">
<a href="../01-HTML-Mastery/05-semantics-and-a11y.md">第5 semantics and a11y ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/css/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-box-model-and-units.md">02-box-model-and-units ➡️</a>
</p>
