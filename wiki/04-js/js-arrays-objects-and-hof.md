---
id: 04-05
module: js
title: 陣列與物件
status: published
tags:
  - "#JS"
  - "#陣列"
  - "#物件"
  - "#Object"
  - "#Array"
  - "#map"
  - "#filter"
  - "#forEach"
  - "#高階函數"
summary: 物件與陣列資料結構、.filter()/.map()/.forEach() 三大高階函數，實作作品集篩選器。
source: raw/05-array-and-object-deep-dive.md
last_updated: 2026-11-24
related:
  - "[[DOM 操作]]"
  - "[[異步與 Promise]]"
  - "[[MOC: 現代前端避坑指南]]"
---

# 陣列與物件

> 現實開發幾乎全部處理數據集 (Data Sets)。物件描述單一實體，陣列儲存多個物件，高階函數則高效加工數據。

## 🎯 為什麼 (Why)

若為每個項目都寫一個變數 (`work1`, `work2`...)，代碼會變成噩夢。物件與陣列能結構化儲存數據，高階函數（`.map`/`.filter`/`.forEach`）則取代冗長的 `for` 迴圈。

## 🧠 核心概念

### 物件 (Object)

描述單一實體的所有屬性。

```javascript
const project = {
    title: "個人品牌網站",
    category: "Frontend",
    year: 2026,
    isCompleted: true
};
print(project.title); // 個人品牌網站
```

### 陣列 (Array)

儲存多個相同類型的物件。

```javascript
const projects = [
    { title: "網站 A", cat: "HTML" },
    { title: "網站 B", cat: "CSS" },
    { title: "網站 C", cat: "JS" },
];
print(projects[0].title); // 網站 A
```

### 三大高階函數 (The Big Three)

| 方法 | 作用 | 範例 |
|------|------|------|
| `.filter()` | 篩選符合條件的元素 | `projects.filter(p => p.cat === "JS")` |
| `.map()` | 轉換為另一種格式 | `projects.map(p => \`<li>\${p.title}</li>\`)` |
| `.forEach()` | 對每個元素執行操作 | `projects.forEach(p => print(p.title))` |

### 作品集篩選器邏輯

1. HTML：建立分類按鈕 (全部 / HTML / CSS)
2. JS：監聽按鈕點擊，獲取類別名稱
3. 加工：`.filter()` 篩選對應類別陣列
4. 渲染：`.map()` 轉為 HTML，注入到容器

## 💻 Code Snippet

```javascript
// 建立數據源
const projects = [
    { title: "網站 A", cat: "HTML", year: 2025 },
    { title: "網站 B", cat: "CSS", year: 2026 },
    { title: "網站 C", cat: "JS", year: 2026 },
];

// .filter() 篩選
const jsProjects = projects.filter(p => p.cat === "JS");

// .map() 轉換為 HTML
const htmlList = projects.map(p => `<li>${p.title} (${p.cat})</li>`);

// .forEach() 執行動作
projects.forEach(p => print(p.title));

// 綜合範例：作品集篩選器
function filterByCategory(category) {
    const filtered = projects.filter(p => p.cat === category);
    const container = document.querySelector('.works-grid');
    container.innerHTML = filtered.map(p => `
        <div class="work-card">
            <h3>${p.title}</h3>
            <p>${p.cat}</p>
        </div>
    `).join('');
}
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 每個項目用獨立變數 `work1`, `work2` | 用陣列儲存，統一管理 |
| 用 `for` 迴圈處理陣列 | 優先用 `.map()`/`.filter()`/`.forEach()` |
| 直接修改原陣列 | 用 `.filter()`/`.map()` 回傳新陣列 (不可變) |
| 在 HTML 寫死所有作品 | 全部由 JS 根據數據動態生成 |

## 🔗 關聯連結

- [[DOM 操作]]：將渲染結果注入頁面
- [[異步與 Promise]]：從 API 抓取真實數據
- [[MOC: 現代前端避坑指南]]：跨模組避坑對比

## 🏷️ 標籤

#JS #陣列 #物件 #Object #Array #map #filter #forEach #高階函數
