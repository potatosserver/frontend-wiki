# 02. 文字與基礎標籤 (Text and Basic Tags)

在建立了網頁的骨架後，現在我們要開始填充內容。HTML 的標籤（Tags）就像是**「標記」**，告訴瀏覽器這段文字應該被視為什麼。

一個專業的開發者不會隨意使用標籤來達到視覺效果（例如：為了讓字變大而使用 `<h1>`），而是會根據**內容的性質**來選擇正確的標籤。

---

## 1. 標題標籤 (Headings): `<h1>` 到 `<h6>`

標題標籤用於定義頁面的結構層級。

### 語法與層級
- `<h1>`：頁面中最重要的主題（通常每頁僅限一個）。
- `<h2>` $\rightarrow$ `<h6>`：次要標題，層級越深，字體通常越小。

**🚀 程式碼範例：正確的層級結構**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>02-text-and-basic-tags</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <h1>我的專業攝影作品集</h1> <!-- 頁面主標題 -->
    <h2>風景攝影</h2>         <!-- 第一大類 -->
        <h3>山脈系列</h3>       <!-- 子類別 -->
        <h3>海洋系列</h3>       <!-- 子類別 -->
    <h2>人像攝影</h2>         <!-- 第一大類 -->
        <h3>商業人像</h3>       <!-- 子類別 -->
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

**⚠️ 專業陷阱：不要用標題來控制大小**
- **錯誤寫法**：我想讓這段字變大 $\rightarrow$ 使用 `<h1>`。
- **專業寫法**：根據意義使用 `<h3>` $\rightarrow$ 使用 **CSS** 來調整字體大小。
- **原因**：Google 爬蟲會根據 `<h1>` $\rightarrow$ `<h6>` 來判斷你的網頁內容重點。如果你亂用，會嚴重影響 SEO。

---

## 2. 段落與文字格式化 (Text Formatting)

### A. 段落標籤 `<p>`
`<p>` 代表一個段落 (Paragraph)。瀏覽器會自動在段落前後加入一定的間距。

### B. 常用格式化標籤
| 標籤 | 效果 | 意義 (Semantic Meaning) |
| :--- | :--- | :--- |
| `<strong>` | **粗體** | 表示內容非常**重要** (螢幕閱讀器會加重語氣)。 |
| `<em>` | *斜體* | 表示內容被**強調**。 |
| `<br>` | 強制換行 | 單個標籤，不需要閉合 (Self-closing)。 |
| `<hr>` | 水平線 | 分隔不同的內容主題。 |

**🚀 程式碼範例：複合使用**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>02-text-and-basic-tags</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <p>
    歡迎來到我的網站！這裡有 <strong>最專業</strong> 的攝影教學。<br>
    如果你是初學者，我建議從 <em>基礎光影</em> 開始學習。
</p>
<hr>
<p>聯繫我：email@example.com</p>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 3. 超連結 (Hyperlinks): `<a>` 標籤

連結是網頁的靈魂，它將全球的資訊串聯在一起。`<a>` 標籤必須搭配 `href` 屬性才能運作。

### 核心屬性
- `href`：目標網址 (URL)。
- `target="_blank"`：在新分頁打開連結 (常用於外部連結，避免使用者離開你的網站)。

**🚀 程式碼範例：各種連結方式**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>02-text-and-basic-tags</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <!-- 1. 外部連結 (絕對路徑) -->
<a href="https://www.google.com" target="_blank">前往 Google 搜尋</a>

<!-- 2. 內部連結 (相對路徑) -->
<a href="about.html">關於我</a>

<!-- 3. 錨點連結 (跳轉到同一頁的特定位置) -->
<a href="#contact-section">跳轉到聯絡資訊</a>
...
<div id="contact-section">這裡是我聯絡資訊的位置</div>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 4. 列表 (Lists): `<ul>`, `<ol>`, `<li>`

列表用於組織條列式資訊，分為「無序」與「有序」兩種。

### A. 無序列表 `<ul>` (Unordered List)
使用圓點標記，適用於順序不重要的項目 (例如：購物清單)。
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>02-text-and-basic-tags</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <ul>
    <li>蘋果</li>
    <li>香蕉</li>
    <li>橘子</li>
</ul>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

### B. 有序列表 `<ol>` (Ordered List)
使用數字標記，適用於有步驟順序的內容 (例如：食譜)。
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>02-text-and-basic-tags</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <ol>
    <li>打開冰箱</li>
    <li>取出雞蛋</li>
    <li>開火加熱</li>
</ol>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 🛠️ 主專案功能疊加

現在，請在你的主專案中疊加以下內容：

1. **Hero Section**：建立一個 `<h1>` 標題（你的名字）與一個簡短的 `<p>` 自我介紹。
2. **關於我**：建立一個 `<section>` 區塊，使用 `<ul>` 列出你的 3 個核心技能。
3. **導航連結**：建立一個 `<a>` 標籤連結到你的 GitHub 頁面，並設定為新分頁打開。

---
<p align="center">
<a href="01-skeleton-and-encoding.md">01-skeleton-and-encoding ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/html/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-forms-and-inputs.md">03-forms-and-inputs ➡️</a>
</p>
