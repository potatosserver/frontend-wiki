# 04. 完美對齊與分佈 (Flexbox Practical)

如果你曾嘗試用 `margin-left: 20%` 或者 `text-align: center` 來讓元素居中，然後發現它在不同螢幕上全部跑掉 $\rightarrow$ 歡迎來到 Flexbox 的世界。

**Flexbox (彈性盒子)** 是現代前端開發的靈魂。它的核心目標只有一個：**讓你不需要計算像素，就能實現完美的對齊與分佈。**

---

## 1. 視覺問題：我想讓東西「絕對居中」

這是所有前端開發者的終極噩夢。如果你想讓一個元素在父容器中水平且垂直地完全居中，Flexbox 是最快、最穩定的解法。

**🚀 居中標準配方 (The Center Recipe)**
只要在父元素加上這三行，內部的子元素就會瞬間居中。

**第一步：HTML 結構**
```html
<div class="center-box">
    <div class="content">我是居中的內容</div>
</div>
```

**第二步：CSS 魔法**
```css
.center-box {
    display: flex;              /* 啟動 Flex 模式 */
    justify-content: center;    /* 水平居中 */
    align-items: center;        /* 垂直居中 */
    height: 100dvh;             /* 填滿整個可見螢幕高度 */
    background: #f0f0f0;
}

.content {
    padding: 20px;
    background: white;
    border-radius: 8px;
}
```

**💡 核心原理：**
- `display: flex` $\rightarrow$ 告訴瀏覽器：「我的孩子們現在是彈性盒子，請根據我的指令排列」。
- `justify-content` $\rightarrow$ 控制 **主軸 (Main Axis)** 的對齊 (預設是水平方向)。
- `align-items` $\rightarrow$ 控制 **交叉軸 (Cross Axis)** 的對齊 (預設是垂直方向)。

---

## 2. 視覺問題：我想讓元素「平均分佈」

在打造導航欄時，我們通常希望 Logo 在左邊，連結在右邊，且彼此之間有相等的間距。

### ⚡️ 解決方案：`justify-content` 的四種模式

**實作範例：**
```css
.nav-container {
    display: flex;
    /* 嘗試切換以下屬性，觀察視覺變化 */
    justify-content: flex-start;   /* 全部靠左 (預設) */
    justify-content: flex-end;     /* 全部靠右 */
    justify-content: center;       /* 全部居中 */
    justify-content: space-between; /* 兩端對齊，中間均分 (導航欄最愛) */
    justify-content: space-around; /* 每個元素周圍均分間距 */
}
```

**🚀 實戰對比：導航欄實作**
```html
<nav class="nav-container">
    <div class="logo">我的品牌</div>
    <ul class="nav-links">
        <li><a href="#">首頁</a></li>
        <li><a href="#">作品</a></li>
        <li><a href="#">聯絡</a></li>
    </ul>
</nav>
```
```css
.nav-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    height: 60px;
    background: white;
}

.nav-links {
    display: flex;
    list-style: none;
    gap: 20px; /* 現代 CSS 的最強屬性：直接設定子元素間距 */
}
```

---

## 3. 視覺問題：我想讓元素「自適應伸縮」

有時候我們希望一個元素佔滿剩餘空間，而另一個元素保持固定大小。這就是 `flex` 屬性的威力。

**⚡️ 實作場例：搜尋欄與按鈕**
```html
<div class="search-bar">
    <input type="text" class="input-field" placeholder="搜尋作品...">
    <button class="btn">搜尋</button>
</div>
```
```css
.search-bar {
    display: flex;
    gap: 10px;
}

.input-field {
    flex: 1; /* 關鍵：讓輸入框佔滿所有剩餘空間 */
    padding: 8px;
}

.btn {
    flex: 0; /* 按鈕保持原始大小，不伸縮 */
    padding: 8px 20px;
}
```

---

## 🚀 全量實作範例：完美對齊的首頁 Hero Section

請建立以下檔案，體驗 Flexbox 的強大。

**檔案 1：`index.html`**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>Flexbox 實驗</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <section class="hero">
        <div class="hero-content">
            <h1>打造專業前端工程師的路徑</h1>
            <p>從零開始，掌握工業級網頁開發標準。</p>
            <div class="btn-group">
                <a href="#" class="btn-primary">開始學習</a>
                <a href="#" class="btn-secondary">查看作品</a>
            </div>
        </div>
    </section>
</body>
</html>
```

**檔案 2：`style.css`**
```css
body { margin: 0; font-family: sans-serif; }

.hero {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    height: 100dvh; /* 使用動態視口高度，確保手機端完美居中 */
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
}

.hero-content {
    max-width: 600px;
    padding: 20px;
}

.btn-group {
    display: flex;
    justify-content: center;
    gap: 15px;
    margin-top: 30px;
}

.btn-primary {
    background: white;
    color: #764ba2;
    padding: 12px 24px;
    text-decoration: none;
    border-radius: 50px;
    font-weight: bold;
}
```

---

## 🛠️ 主專案功能疊加

現在，請在你的主專案中實作完美對齊：

1. **導航欄佈局**：使用 `justify-content: space-between` 讓 Logo 在左、連結在右。
2. **Hero Section 居中**：使用 Flexbox 讓你的自我介紹在螢幕正中央。
3. **按鈕分佈**：使用 `gap` 屬性讓你的行動按鈕 (CTA) 保持適當間距。

---
<p align="center">
<a href="03-positioning-and-zindex.md">03-positioning-and-zindex ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/css/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="05-grid-practical.md">05-grid-practical ➡️</a>
</p>
