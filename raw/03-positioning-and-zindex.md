# 03. 精確放置元素 (Positioning and Z-Index)

在之前的章節中，我們發現元素是按照「自然流動 (Normal Flow)」排列的 $\rightarrow$ 一個接一個，從上到下，從左到右。但如果你想實作「固定在頂部的導航欄」或「卡片右上角的通知小紅點」，你就不能依賴自然流動。

這時候，我們需要使用 **定位 (Positioning)** 來強行改變元素的座標。

---

## 1. 視覺問題：我想把東西放在「特定位置」

想像一下，你有一個作品集卡片，你想在卡片的右上角加上一個「New」的標籤。如果你直接寫，標籤會被擠到內容下面。

### ⚡️ 解決方案：Relative $\rightarrow$ Absolute 組合技

這是 CSS 中最經典的定位模式：**「父層 Relative, 子層 Absolute」**。

**第一步：在 HTML 中建立父子結構**
```html
<div class="card">
    <span class="badge">New</span>
    <img src="project.jpg" alt="作品">
    <p>我的作品名稱</p>
</div>
```

**第二步：在 CSS 中設定定位**
```css
/* 父層：設定為 Relative，成為子層的「座標原點」 */
.card {
    position: relative;
    width: 300px;
    border: 1px solid #ccc;
}

/* 子層：設定為 Absolute，可以隨意在父層內移動 */
.badge {
    position: absolute;
    top: 10px;    /* 距離頂部 10px */
    right: 10px;  /* 距離右側 10px */
    background: red;
    color: white;
    padding: 2px 8px;
}
```

**💡 關鍵對應：**
- 如果父層沒有 `position: relative` $\rightarrow$ 子層的 `absolute` 會一直往上找，直到找到 `<body>` 為止 $\rightarrow$ 你的標籤會飛到頁面頂端！

---

## 2. 視覺問題：我想讓導航欄「永遠跟著我」

當頁面很長時，使用者如果想回到頂端，必須滾動很久。專業的做法是實作 **固定導航欄 (Sticky Header)**。

### ⚡️ 解決方案：Fixed 與 Sticky

**A. `position: fixed` (絕對固定)**
元素脫離文檔流，完全固定在視窗的某個座標。
```css
.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    height: 60px;
    background: white;
    z-index: 1000; /* 確保它在最上層 */
}
```

**B. `position: sticky` (黏性定位)**
元素在達到指定位置前是正常的，一旦滾動到該位置，它就「黏」在那裡。
```css
.category-title {
    position: sticky;
    top: 0;
    background: #f0f0f0;
}
```

---

## 3. 視覺問題：誰應該在上面？ (Z-Index)

當多個元素重疊時，瀏覽器如何決定誰在上面？這就是 **Z-Index (層疊順序)**。

**💡 核心邏輯：數字越大 $\rightarrow$ 越靠近使用者 (越在上層)。**

**🚀 實戰對比：**
```css
.modal-overlay {
    position: fixed;
    z-index: 100; /* 背景遮罩 */
}

.modal-content {
    position: fixed;
    z-index: 200; /* 內容必須比遮罩高，才能顯示在上面 */
}
```

**⚠️ 專業陷阱：為什麼我的 `z-index: 9999` 沒效？**
因為 `z-index` 僅在具有 `position` (relative, absolute, fixed, sticky) 的元素上才生效。而且，它受限於 **「層疊上下文 (Stacking Context)」** $\rightarrow$ 如果父層被壓在下面，子層就算 z-index 一萬也沒用。

---

## 🚀 全量實作範例：帶有通知標籤的卡片

請建立以下檔案，觀察定位是如何運作的。

**檔案 1：`index.html`**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>定位實驗</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <nav class="navbar">我的專業作品集</nav>
    
    <div class="container">
        <div class="card">
            <span class="badge">New</span>
            <div class="card-img">圖片區域</div>
            <div class="card-info">
                <h3>作品名稱</h3>
                <p>使用 HTML/CSS 打造</p>
            </div>
        </div>
    </div>
</body>
</html>
```

**檔案 2：`style.css`**
```css
body { font-family: sans-serif; margin: 0; padding-top: 80px; }

/* 固定導航欄 */
.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    height: 60px;
    background: #2563eb;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
}

.container {
    display: flex;
    justify-content: center;
    padding: 20px;
}

/* 核心：父層 Relative */
.card {
    position: relative; 
    width: 250px;
    border: 1px solid #ddd;
    border-radius: 12px;
    overflow: hidden;
}

/* 核心：子層 Absolute */
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

.card-img {
    height: 150px;
    background: #eee;
    display: flex;
    align-items: center;
    justify-content: center;
}

.card-info { padding: 15px; }
```

---

## 🛠️ 主專案功能疊加

現在，請在你的主專案中實作精確定位：

1. **固定導航欄**：將你的導航欄設定為 `position: fixed` 並確保它在最頂端。
2. **作品標籤**：在你的作品集卡片右上角，實作一個 `position: absolute` 的「New」或「Featured」標籤。
3. **層級管理**：檢查你的 z-index，確保導航欄永遠在最上層，不會被內容遮擋。

---
<p align="center">
<a href="02-box-model-and-units.md">02-box-model-and-units ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/css/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-flexbox-practical.md">04-flexbox-practical ➡️</a>
</p>
