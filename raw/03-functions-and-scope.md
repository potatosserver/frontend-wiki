# 03. 函數與作用域 (Functions and Scope)

在之前的章節中，我們的代碼是「線性的」$\rightarrow$ 從第一行執行到最後一行。但專業工程師會將重複使用的邏輯封裝在 **函數 (Functions)** 之中。

函數就像是一個「加工廠」：你給它一些原材料 (參數)，它幫你處理後回傳一個成品 (回傳值)。

---

## 1. 函數的定義與呼叫

### A. 傳統函數 (Function Declaration)
最基礎的定義方式。
```javascript
function greet(name) {
    return "你好, " + name + "！歡迎來到我的作品集。";
}

// 呼叫函數
let message = greet("Andrew");
print(message); // 你好, Andrew！歡迎來到我的作品集。
```

### B. 箭頭函數 (Arrow Function) $\rightarrow$ 現代標準
在現代 JS 中，我們更傾向於使用簡潔的箭頭函數。
```javascript
const add = (a, b) => a + b;
print(add(5, 10)); // 15
```

---

## 2. 作用域 (Scope)：變數能被誰看到？

變數並非在任何地方都能被存取。

### A. 全域作用域 (Global Scope)
定義在函數之外的變數，整個程式任何地方都能讀到它。

### B. 區域作用域 (Local/Block Scope)
定義在函數內部或 `{ }` 區塊內的變數，只能在該區塊內使用。

**🚀 實作對比：**
```javascript
let globalVar = "我是全域變數";

function testScope() {
    let localVar = "我是區域變數";
    print(globalVar); // ✅ 成功：能看到全域變數
    print(localVar);  // ✅ 成功：能看到自己的區域變數
}

testScope();
// print(localVar); // ❌ 報錯：在函數外面找不到 localVar
```

---

## 3. 閉包 (Closure)：記憶能力

閉包是 JS 最強大但也最難理解的概念。簡單來說，就是**一個函數可以記住它被創建時周圍的環境。**

**🚀 實作範例：私有計數器**
```javascript
function createCounter() {
    let count = 0; // 私有變數，外部無法直接修改
    return function() {
        count++;
        return count;
    };
}

const myCounter = createCounter();
print(myCounter()); // 1
print(myCounter()); // 2
print(myCounter()); // 3
```
這讓我們可以建立「私有數據」，防止外部代碼隨意篡改。

---

## 🛠️ 實驗場實作挑戰

請在 `js-playground.html` 中完成以下任務：

1. **計算機函數**：建立一個函數 `calculatePrice(price, tax)` $\rightarrow$ 接收價格與稅率 $\rightarrow$ 回傳總金額。
2. **箭頭函數練習**：將上述函數改寫為箭頭函數。
3. **實作私有狀態**：建立一個閉包函數 `createGreeting(name)` $\rightarrow$ 每次呼叫時印出「你好 [name], 歡迎回來！」。

---
<p align="center">
<a href="02-operators-and-control-flow.md">02-operators-and-control-flow ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/js/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-dom-manipulation-mastery.md">04-dom-manipulation-mastery ➡️</a>
</p>
