# 04. DOM 操作精通 (DOM Manipulation Mastery)

恭喜！你已經掌握了 JS 的基礎邏輯。現在，我們要將這些邏輯從「黑盒子 (Playground)」搬到「真實網頁」中。

**這就是 DOM (Document Object Model) $\rightarrow$ 讓 JS 能夠控制 HTML 標籤的橋樑。**

---

## 1. 視覺化目標：讓網頁「活」起來

想像一下，使用者點擊一個按鈕 $\rightarrow$ 頁面背景變色 $\rightarrow$ 文字內容改變。這就是 DOM 操作。

### ⚡️ 步驟 1：選中元素 (querySelector)
要修改元素，必須先「抓住」它。
```javascript
// 抓取 ID 為 main-title 的元素
const title = document.querySelector('#main-title');

// 抓取類名為 description 的第一個元素
const desc = document.querySelector('.description');
```

### ⚡️ 步驟 2：修改內容與樣式
```javascript
title.innerText = "歡迎來到我的新網站！"; // 修改文字
title.style.color = "red";                // 修改 CSS 樣式
```

### ⚡️ 步驟 3：監聽事件 (addEventListener)
讓程式在「特定時間」執行 $\rightarrow$ 例如點擊按鈕時。
```javascript
const btn = document.querySelector('#my-btn');
btn.addEventListener('click', () => {
    alert("按鈕被點擊了！");
});
```

---

## 2. 實作案例：主題切換 (Dark Mode)

這是每個專業作品集必備的功能。

**HTML 部分：**
```html
<button id="theme-toggle">切換模式</button>
```

**CSS 部分：**
```css
body.dark-mode {
    background-color: #1a1a1a;
    color: white;
}
```

**JS 部分：**
```javascript
const toggleBtn = document.querySelector('#theme-toggle');
toggleBtn.addEventListener('click', () => {
    // toggle 如果有就移除，沒有就加上
    document.body.classList.toggle('dark-mode');
});
```

---

## 3. 動態創建元素 (createElement)

除了修改現有元素，JS 還能從無到有創造新標籤。

**🚀 實作流程：**
1. `document.createElement('li')` $\rightarrow$ 創造一個列表項。
2. `li.innerText = "新項目"` $\rightarrow$ 填入文字。
3. `container.appendChild(li)` $\rightarrow$ 把新項目掛到頁面上。

---

## 🛠️ 主專案功能疊加

現在，請在你的主專案中實作互動功能：

1. **主題切換按鈕**：在頂部導航欄增加按鈕 $\rightarrow$ 點擊後切換 `<body>` 的 `.dark-mode` 類名。
2. **動態問候**：選取 Hero Section 的 `<h1>` $\rightarrow$ 建立一個按鈕，點擊後將標題改為「你好，[你的名字]！」。
3. **表單攔截**：監聽聯絡表單的 `submit` 事件 $\rightarrow$ 使用 `event.preventDefault()` 阻止跳頁 $\rightarrow$ 在 Console 印出表單數據。

---
<p align="center">
<a href="03-functions-and-scope.md">03-functions-and-scope ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/js/04-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="05-array-and-object-deep-dive.md">05-array-and-object-deep-dive ➡️</a>
</p>
