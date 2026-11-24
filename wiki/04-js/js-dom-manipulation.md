---
id: 04-04
module: js
title: DOM 操作
status: published
tags:
  - "#JS"
  - "#DOM"
  - "#querySelector"
  - "#addEventListener"
  - "#DarkMode"
  - "#createElement"
summary: DOM 選中元素、修改內容與樣式、監聽事件、動態創建元素，含主題切換實作範例。
source: raw/04-dom-manipulation-mastery.md
last_updated: 2026-11-24
related:
  - "[[函數與作用域]]"
  - "[[陣列與物件]]"
  - "[[MOC: 現代前端避坑指南]]"
---

# DOM 操作

> DOM (Document Object Model) 是 JS 控制 HTML 標籤的橋樑，讓網頁從靜態變動態。

## 🎯 為什麼 (Why)

將 JS 邏輯從「黑盒子 (Playground)」搬到真實網頁，才能實作「點擊按鈕改變背景顏色」等互動功能。這是前端開發從「會寫語法」到「能建立應用」的關鍵一步。

## 🧠 核心概念

### 三步驟 DOM 操作

| 步驟 | 動作 | 範例 |
|------|------|------|
| 1. 選中元素 | `document.querySelector()` | `document.querySelector('#main-title')` |
| 2. 修改內容/樣式 | `.innerText`、`.style` | `title.innerText = "新標題"` |
| 3. 監聽事件 | `.addEventListener()` | `btn.addEventListener('click', () => {})` |

### 主題切換 (Dark Mode) 完整範例

```javascript
const toggleBtn = document.querySelector('#theme-toggle');
toggleBtn.addEventListener('click', () => {
    document.body.classList.toggle('dark-mode');
});
```

```css
body.dark-mode {
    background-color: #1a1a1a;
    color: white;
}
```

### 動態創建元素

```javascript
const li = document.createElement('li');
li.innerText = "新項目";
container.appendChild(li);
```

## 💻 Code Snippet

```javascript
// 步驟 1：選中元素
const title = document.querySelector('#main-title');
const desc = document.querySelector('.description');

// 步驟 2：修改內容與樣式
title.innerText = "歡迎來到我的新網站！";
title.style.color = "red";

// 步驟 3：監聽點擊事件
const btn = document.querySelector('#my-btn');
btn.addEventListener('click', () => {
    alert("按鈕被點擊了！");
});

// 主題切換
const toggleBtn = document.querySelector('#theme-toggle');
toggleBtn.addEventListener('click', () => {
    document.body.classList.toggle('dark-mode');
});

// 動態創建元素
const li = document.createElement('li');
li.innerText = "新項目";
document.querySelector('ul').appendChild(li);
```

```html
<button id="theme-toggle">切換模式</button>
<h1 id="main-title">原標題</h1>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 在 HTML 中用 `onclick` 內聯事件 | 使用 `addEventListener` 分離結構與行為 |
| 每次點擊都重新查詢 DOM | 將元素存到變數，複用查詢結果 |
| 忘記 `event.preventDefault()` | 表單 submit 時加上 `preventDefault()` 阻止跳頁 |
| 直接修改 `innerHTML` 可能導致 XSS | 優先用 `innerText` 或 `textContent` |

## 🔗 關聯連結

- [[函數與作用域]]：箭頭函數與閉包
- [[陣列與物件]]：`.map()` 動態渲染列表
- [[MOC: 現代前端避坑指南]]：跨模組避坑對比

## 🏷️ 標籤

#JS #DOM #querySelector #addEventListener #DarkMode #createElement
