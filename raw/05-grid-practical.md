# 05. 打造網格佈局 (Grid Practical)

如果說 Flexbox 是處理「一條線」的專家 $\rightarrow$ 只要處理水平或垂直其中一個方向，那麼 **CSS Grid (網格佈局)** 就是處理「整個平面」的指揮官。

專業工程師的準則是：**「一維佈局用 Flexbox，二維佈局用 Grid」**。當你需要同時控制 **行 (Rows)** 與 **列 (Columns)** 的對齊時，Grid 是唯一正確的選擇。

---

## 1. 視覺問題：我想打造一個「整齊的作品集牆」

想像你要建立一個作品展示區，每行 3 個卡片，且所有卡片的高度必須一致，無論內容多寡。如果你用 Flexbox，你必須為每個卡片設定寬度，且很難控制行與行的間距。

### ⚡️ 解決方案：Grid 網格系統

**第一步：在 HTML 中建立容器與子元素**
```html
<div class="works-grid">
    <div class="work-card">作品 1</div>
    <div class="work-card">作品 2</div>
    <div class="work-card">作品 3</div>
    <div class="work-card">作品 4</div>
    <div class="work-card">作品 5</div>
    <div class="work-card">作品 6</div>
</div>
```

**第二步：在 CSS 中定義網格規則**
```css
.works-grid {
    display: grid;
    /* 定義 3 個等寬的列，每列佔 1 份 (fr) */
    grid-template-columns: repeat(3, 1fr);
    /* 設定行與列的間距 */
    gap: 20px;
}

.work-card {
    background: #f9f9f9;
    border: 1px solid #ddd;
    padding: 20px;
    text-align: center;
}
```

**💡 關鍵原理解析：**
- `display: grid` $\rightarrow$ 將容器變為網格模式。
- `grid-template-columns` $\rightarrow$ 決定有幾列，以及每列多寬。
- `1fr` (Fractional Unit) $\rightarrow$ **分數單位**。它會自動計算剩餘空間並均分。`repeat(3, 1fr)` 等於 `1fr 1fr 1fr`。

---

## 2. 視覺問題：我想讓某個元素「橫跨多列」

有時候，你希望首個作品（最重要的一個）比其他作品更大，橫跨兩列。

**🚀 實作方法：`grid-column`**
```css
.work-card:first-child {
    grid-column: span 2; /* 橫跨 2 列 */
    background: #eef2ff;
}
```

---

## 3. 視覺問題：如何讓網格「自動適應」螢幕寬度？

如果你設定 `repeat(3, 1fr)`，那麼在手機上也會強行擠成 3 列 $\rightarrow$ 畫面會崩潰。專業的做法是使用 `auto-fill` 或 `auto-fit`。

**⚡️ 終極自適應配方：**
```css
.works-grid {
    display: grid;
    /* 只要寬度大於 250px，就自動填滿盡量多的列 */
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
}
```

**💡 為什麼這樣寫？**
- `minmax(250px, 1fr)` $\rightarrow$ 告訴瀏覽器：「這個格子的最小寬度是 250px，最大寬度是 1fr」。
- **結果**：在 PC 上可能是 4 列 $\rightarrow$ 在平板上是 2 列 $\rightarrow$ 在手機上自動變成 1 列 $\rightarrow$ **完全不需要寫 Media Query 就能實現基本響應式！**

---

## 🚀 全量實作範例：專業作品集牆

請建立以下檔案，體驗 Grid 的強大。

**檔案 1：`index.html`**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>Grid 實驗</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h2 style="text-align: center;">我的作品集</h2>
    <div class="works-grid">
        <div class="work-card featured">
            <h3>核心專案 A</h3>
            <p>這是最重要的一個作品，所以它橫跨兩列。</p>
        </div>
        <div class="work-card"><h3>作品 B</h3><p>描述文字...</p></div>
        <div class="work-card"><h3>作品 C</h3><p>描述文字...</p></div>
        <div class="work-card"><h3>作品 D</h3><p>描述文字...</p></div>
        <div class="work-card"><h3>作品 E</h3><p>描述文字...</p></div>
        <div class="work-card"><h3>作品 F</h3><p>描述文字...</p></div>
    </div>
</body>
</html>
```

**檔案 2：`style.css`**
```css
body { font-family: sans-serif; padding: 40px; background: #fafafa; }

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

---

## 🛠️ 主專案功能疊加

現在，請在你的主專案中實作網格佈局：

1. **建立作品集區塊**：使用 `display: grid` 建立 `works-grid` 容器。
2. **實作自適應列數**：使用 `repeat(auto-fill, minmax(..., 1fr))` 確保在手機與電腦上都美觀。
3. **強調核心作品**：選擇一個作品卡片，使用 `grid-column: span 2` 讓它更醒目。

---
<p align="center">
<a href="04-flexbox-practical.md">04-flexbox-practical ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/css/05-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="06-responsive-design.md">06-responsive-design ➡️</a>
</p>
