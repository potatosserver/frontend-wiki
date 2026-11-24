# 04. 多媒體與表格 (Multimedia and Tables)

純文字的網頁是枯燥的。為了讓資訊傳達更高效，我們需要引入**視覺化元素 (圖片、影片)** 以及**結構化數據 (表格)**。

本章將教授如何正確地嵌入多媒體資源，並建立專業的數據表格。

---

## 1. 圖片處理 `<img>`

圖片是網頁最常用的元素。但圖片如果使用不當，會導致頁面加載緩慢，甚至在某些裝置上顯示異常。

### 核心屬性
- `src`：圖片的路徑 (絕對路徑或相對路徑)。
- `alt`：**替代文字 (Alternative Text)**。這是最容易被忽略但最重要的屬性。
  - **作用**：當圖片加載失敗時顯示文字 $\rightarrow$ 讓螢幕閱讀器告知視障人士圖片內容 $\rightarrow$ 告知 Google 圖片在講什麼 (SEO)。

**🚀 程式碼範例：專業圖片寫法**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>04-multimedia-and-tables</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <img src="images/profile.jpg" alt="開發者本人在辦公室工作的照片" width="300" height="200">
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 2. 影音元素 `<video>` 與 `<audio>`

現代 HTML5 允許我們直接在網頁中播放音影，而不需要依賴第三方插件 (如 Flash)。

### 影片實作 `<video>`
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>04-multimedia-and-tables</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <video width="640" height="360" controls poster="thumbnail.jpg">
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.webm" type="video/webm">
    您的瀏覽器不支持 video 標籤。
</video>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```
- `controls`：顯示播放/暫停/音量控制條。
- `poster`：影片加載前的封面圖。
- `autoplay` / `muted`：自動播放 (注意：大多數瀏覽器規定- 必須 muted 才能自動播放)。

### 音訊實作 `<audio>`
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>04-multimedia-and-tables</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <audio controls>
    <source src="music.mp3" type="audio/mpeg">
    您的瀏覽器不支持 audio 標籤。
</audio>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 3. 數據表格 `<table>`

表格用於呈現對比性強的結構化數據。表格的語法相對複雜，因為它採取的是 **「行優先」** 的構建方式。

### 核心標籤結構
- `<table>`：表格根容器。
- `<thead>`：表頭區域。
- `<tbody>`：主體數據區域。
- `<tfoot>`：表格底部 (例如總計)。
- `<tr>` (Table Row)：定義一行。
- `<th>` (Table Header)：定義標題單元格 (預設粗體且置中)。
- `<td>` (Table Data)：定義普通數據單元格。

**🚀 程式碼範例：專業數據表格**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>04-multimedia-and-tables</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <table border="1">
    <thead>
        <tr>
            <th>站點名稱</th>
            <th>目前車輛數</th>
            <th>距離 (km)</th>
            <th>狀態</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>台北車站</td>
            <td>12</td>
            <td>0.5</td>
            <td>正常</td>
        </tr>
        <tr>
            <td>忠孝新生</td>
            <td>0</td>
            <td>1.2</td>
            <td>缺車</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">總計站點</td>
            <td>2</td>
        </tr>
    </tfoot>
</table>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```
- `colspan`：合併橫向單元格。
- `rowspan`：合併縱向單元格。

---

## 🛠️ 主專案功能疊加

現在，為你的主專案增加視覺內容與數據：

1. **作品展示**：建立一個作品集區域，為每個作品加入 `<img>` 圖片與正確的 `alt` 描述。
2. **規格對比**：建立一個 `<table>` 表格，對比你學習的不同技術（如：學習時間 vs 難易度）。
3. **多媒體實作**：嘗試嵌入一段關於你作品的介紹影片 `<video>`。

---
<p align="center">
<a href="03-forms-and-inputs.md">03-forms-and-inputs ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/html/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="05-semantics-and-a11y.md">05-semantics-and-a11y ➡️</a>
</p>
