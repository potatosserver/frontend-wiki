# 05. 陣列與物件剖析 (Array and Object Deep Dive)

在現實開發中，你處理的幾乎全部是**數據集 (Data Sets)**。例如：一個作品列表、一個使用者清單。如果你為每個項目都寫一個變數 (`work1`, `work2`...)，你的代碼會變成噩夢。

這時候我們需要 **物件 (Object)** 與 **陣列 (Array)**。

---

## 1. 數據建模：物件 (Object)

物件是用來描述一個「實體」的所有屬性。

**🚀 實作範例：定義一個作品**
```javascript
const project = {
    title: "個人品牌網站",
    category: "Frontend",
    year: 2026,
    isCompleted: true
};

print(project.title); // 輸出: 個人品牌網站
```

---

## 2. 數據集合：陣列 (Array)

陣列是用來儲存多個相同類型的物件。

**🚀 實作範例：作品清單**
```javascript
const projects = [
    { title: "網站 A", cat: "HTML" },
    { title: "網站 B", cat: "CSS" },
    { title: "網站 C", cat: "JS" },
];

print(projects[0].title); // 輸出: 網站 A
```

---

## 3. 數據加工：高階函數 (The Big Three)

專業工程師幾乎不使用 `for` 迴圈來處理陣列，而是使用這三個強大工具：

### A. `.filter()` $\rightarrow$ 篩選
只保留符合條件的元素。
```javascript
const jsProjects = projects.filter(p => p.cat === "JS");
```

### B. `.map()` $\rightarrow$ 轉換
將數據轉換成另一種格式 (例如：將物件轉成 HTML 字串)。
```javascript
const htmlList = projects.map(p => `<li>${p.title}</li>`);
```

### C. `.forEach()` $\rightarrow$ 執行動作
單純地對每個元素執行一次操作。

---

## 🚀 實戰：實作「作品集篩選器」

這是主專案的核心功能。

**邏輯路徑：**
1. **HTML** $\rightarrow$ 建立三個按鈕 (全部 / HTML / CSS)。
2. **JS** $\rightarrow$ 監聽按鈕點擊 $\rightarrow$ 獲取類別名稱。
3. **加工** $\rightarrow$ 使用 `.filter()` 篩選出對應類別的作品陣列。
4. **渲染** $\rightarrow$ 使用 `.map()` 將結果轉為 HTML $\rightarrow$ 注入到 `.works-grid` 容器。

---

## 🛠️ 主專案功能疊加

現在，請在你的主專案中實作動態篩選：

1. **建立數據源**：在 JS 中建立一個 `projects` 陣列，包含 6 個作品物件。
2. **實作篩選邏輯**：點擊分類按鈕 $\rightarrow$ 篩選陣列 $\rightarrow$ 更新網頁內容。
3. **動態渲染**：不要在 HTML 寫死作品，全部由 JS 根據數據動態生成。

---
<p align="center">
<a href="04-dom-manipulation-mastery.md">04-dom-manipulation-mastery ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/js/05-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="06-async-and-promises.md">06-async-and-promises ➡️</a>
</p>
