# 06. 適應所有螢幕 (Responsive Design)

在今天這個裝置多元的時代，一個專業的網頁必須能夠在 **iPhone, iPad, MacBook, 以及 4K 螢幕** 上都提供完美的閱讀體驗。這就是 **響應式設計 (Responsive Design)** 的核心。

響應式設計的目標是：**讓內容根據螢幕寬度「流動」，而非簡單地縮小整個頁面。**

---

## 1. 視覺問題：我的網頁在手機上「崩潰」了

如果你在 PC 上設計了一個寬 1200px 的導航欄，當它在寬 375px 的 iPhone 上打開時，使用者必須左右滾動才能看到完整內容 $\rightarrow$ 這就是典型的「崩潰」。

### ⚡️ 解決方案 A：Viewport 設定 (基礎)

在所有 HTML 的 `<head>` 中，必須加上這行代碼。如果沒加，手機瀏覽器會嘗試「模擬 PC 寬度」然後把整個頁面縮小到像螞蟻一樣。

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### ⚡️ 解決方案 B：媒體查詢 (Media Queries)

媒體查詢就像是給瀏覽器的一組「條件指令」：**「如果螢幕寬度小於 X 像素，請執行這套樣式」。**

**🚀 實作範例：**
```css
/* 預設樣式 (PC 模式) */
.container {
    display: flex;
    flex-direction: row;
}

/* 當螢幕寬度小於 768px 時 (平板與手機) */
@media (max-width: 768px) {
    .container {
        flex-direction: column; /* 將水平排列改為垂直排列 */
        text-align: center;
    }
}
```

---

## 2. 進階技巧：流體佈局與現代函數

除了 `@media`，現代 CSS 提供了一些更聰明的函數，讓我們能實作「平滑過渡」而非「跳躍式切換」。

### A. `clamp()`：設定範圍限制
`clamp(最小值, 理想值, 最大值)` $\rightarrow$ 讓字體大小隨螢幕縮放，但不會變得太小或太大。

**實作案例：**
```css
h1 {
    /* 字體最小 1.5rem, 理想 5vw, 最大 3rem */
    font-size: clamp(1.5rem, 5vw, 3rem);
}
```

### B. `min()` 與 `max()`
- `width: min(90%, 1200px);` $\rightarrow$ 寬度是 90%，但最大不超過 1200px。這比寫 `width: 90%; max-width: 1200px;` 更簡潔。

---

## 3. 專業策略：Mobile-First (手機優先)

專業前端工程師不再是「先寫 PC 版 $\rightarrow$ 再修手機版」，而是採取 **「手機優先」** 策略。

**邏輯路徑：**
1. **先寫手機版樣式** (最簡單、最基礎的單列佈局)。
2. **使用 `@media (min-width: ...)`** $\rightarrow$ 隨著螢幕變寬，逐漸增加複雜度 (例如 1 列 $\rightarrow$ 2 列 $\rightarrow$ 3 列)。

**為什麼要這樣做？**
- 手機螢幕最受限，最容易出錯 $\rightarrow$ 先搞定手機版能確保基本可用性。
- 程式碼更簡潔，不需要在 PC 版寫了大量樣式後，再用 `max-width` 去「覆蓋」或「取消」它們。

---

## 🚀 全量實作範例：完全響應式的個人名片

請建立以下檔案，體驗從手機到 PC 的自動適應。

**檔案 1：`index.html`**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>響應式實驗</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="profile-card">
        <img src="avatar.jpg" alt="頭像" class="avatar">
        <h1>Andrew Cho</h1>
        <p>前端工程師 | 視覺設計師</p>
        <div class="links">
            <a href="#">GitHub</a>
            <a href="#">LinkedIn</a>
        </div>
    </div>
</body>
</html>
```

**檔案 2：`style.css`**
```css
body {
    margin: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100dvh;
    background: #f0f2f5;
    font-family: sans-serif;
}

.profile-card {
    background: white;
    padding: 30px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    width: 90%;             /* 手機版：佔寬度 90% */
    max-width: 400px;       /* PC 版：最大 400px */
}

.avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background: #ddd;
}

.links {
    display: flex;
    justify-content: center;
    gap: 15px;
    margin-top: 20px;
}

/* 響應式調整：當螢幕寬度大於 600px 時 */
@media (min-width: 600px) {
    .profile-card {
        padding: 50px;
        background: #fff;
        border: 2px solid #2563eb;
    }
}
```

---

## 🛠️ 主專案功能疊加

現在，請讓你的主專案適應所有螢幕：

1. **設定 Viewport**：確認 `<head>` 中有 `meta name="viewport"` 標籤。
2. **實作響應式佈局**：
    - 導航欄 $\rightarrow$ 在手機上改為垂直排列或隱藏。
    - 作品集牆 $\rightarrow$ 使用 `repeat(auto-fill, minmax(...))` 實現自動列數調整。
3. **流體文字**：使用 `clamp()` 讓標題在手機與 PC 之間平滑縮放。

---
<p align="center">
<a href="05-grid-practical.md">05-grid-practical ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/css/06-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../03-Design-Systems-M3/01-m3-color-system.md">01-m3-color-system ➡️</a>
</p>
