# 01. 基礎與變數 (Basics and Variables)

歡迎來到 JavaScript (JS) 的世界！如果 HTML 是骨架，CSS 是皮膚，那麼 JavaScript 就是**「肌肉與神經」**。它讓網頁能夠「思考」並對使用者的操作做出「反應」。

在學習任何複雜邏輯之前，我們必須先建立一個**低壓力**的練習環境，讓你專注於程式碼邏輯，而不需要擔心 HTML 標籤是否寫錯。

---

## 1. 搭建你的 JS 實驗室 (Playground)

我們為你準備了一個專屬的 `js-playground.html`。這個檔案就像一個簡易的 IDE，讓你可以直接在瀏覽器中寫 JS 並立刻看到結果。

**⚡️ 如何使用實驗場？**
1. 開啟 `js-playground.html` $\rightarrow$ 找到底部的 `<script>` 標籤。
2. 在標籤內撰寫你的 JS 代碼。
3. 使用 `print("內容")` 將結果印在頁面的黑盒子中。
4. 保存 $\rightarrow$ 刷新瀏覽器 $\rightarrow$ 查看結果。

**🚀 第一次實驗：**
請在 `<script>` 內寫下這行：
```javascript
print("你好, JS 實驗場！我準備好學習編程了。");
```

---

## 2. 儲存數據：變數 (Variables)

想像變數就像是一個**「標籤盒子」**。你想儲存一段文字或一個數字，就把它放進盒子裡，並在盒子上面貼一個名字，方便以後找回來。

### A. `let` $\rightarrow$ 可變的盒子 (變數)
如果你儲存的東西之後會改變（例如：使用者得分、目前的頁碼），請使用 `let`。
```javascript
let score = 0;
print("初始得分: " + score);

score = 10; // 更新數值
print("更新後得分: " + score);
```

### B. `const` $\rightarrow$ 不可變的盒子 (常量)
如果你儲存的東西永遠不會改變（例如：你的生日、網站的主域名），請使用 `const`。
```javascript
const birthYear = 1995;
// birthYear = 1996; // ❌ 這樣寫會報錯，因為 const 不能被修改
print("出生年份: " + birthYear);
```

**💡 專業習慣：** 除非確定這個變數需要被修改，否則**優先使用 `const`**。這能防止你在大型專案中不小心改掉重要數據。

---

## 3. 數據的種類 (Data Types)

JS 會根據你放入盒子裡的內容，自動判斷它的「類型」。

| 類型 | 名稱 | 範例 | 用途 |
| :--- | :--- | :--- | :--- |
| **字串 (String)** | `String` | `"Andrew"` | 文字內容，必須用引號包裹 |
| **數字 (Number)** | `Number` | `42` 或 `3.14` | 所有的數字 (整數、浮點數) |
| **布林值 (Boolean)** | `Boolean` | `true` 或 `false` | 開關/對錯判斷 (最常用於 `if` 判斷) |
| **空值 (Null/Undefined)** | `Null` | `null` | 代表「刻意設定為空」或「尚未定義」 |

**🚀 綜合練習：**
```javascript
const myName = "Andrew"; // String
let age = 25;             // Number
let isStudent = true;     // Boolean

print("名稱: " + myName);
print("年齡: " + age);
print("是否為學生: " + isStudent);
```

---

## 🛠️ 實驗場實作挑戰

請在 `js-playground.html` 中完成以下任務：

1. **建立變數**：定義一個常量 `myCity` (你的城市) 和一個變數 `currentTemp` (目前溫度)。
2. **更新數據**：將 `currentTemp` 的值增加 5 度。
3. **視覺輸出**：使用 `print()` 將這兩個資訊組合起來印出，例如：「我住在台北，今天溫度是 28 度」。

---
<p align="center">
<a href="../03-Design-Systems-M3/04-animation-physics.md">第4 animation physics ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/js/01-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="02-operators-and-control-flow.md">02-operators-and-control-flow ➡️</a>
</p>
