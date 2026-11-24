---
id: 04-03
module: js
title: 函數與作用域
status: published
tags: ["#JS", "#函數", "#箭頭函數", "#作用域", "#閉包", "#Closure""]
summary: 函數定義與呼叫、箭頭函數、全域與區域作用域、閉包私有計數器。
source: raw/03-functions-and-scope.md
last_updated: 2026-11-24
related:
  - [[運算符與控制流程]]
  - [[DOM 操作]]
  - [[Event Loop]]
---

# 函數與作用域

> 函數就像「加工廠」：給它參數 (原材料)，回傳結果 (成品)。作用域決定變數能被誰看見，閉包讓函數能記住創建時的環境。

## 🎯 為什麼 (Why)

線性執行的代碼難以重複使用。函數將邏輯封裝，可重複呼叫；作用域防止變數污染；閉包建立私有數據，防止外部篡改。

## 🧠 核心概念

### 函數定義方式

| 方式 | 語法 | 特點 |
|------|------|------|
| 函數宣告 | `function greet(name) {}` | 可被提升 (hoisting) |
| 箭頭函數 | `const add = (a, b) => a + b` | 現代標準，語法簡潔，沒有自己的 `this` |

### 作用域 (Scope)

| 類型 | 說明 | 可見範圍 |
|------|------|----------|
| 全域作用域 | 函數外定義 | 整個程式皆可存取 |
| 區域/區塊作用域 | 函數或 `{ }` 內定義 | 僅限該區塊內 |

### 閉包 (Closure)

閉包是一個函數能記住它被創建時周圍的環境，即使外部函數已執行完畢。常用於建立私有計數器。

```javascript
function createCounter() {
    let count = 0; // 私有變數
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

## 💻 Code Snippet

```javascript
// 函數宣告
function greet(name) {
    return "你好, " + name + "！歡迎來到我的作品集。";
}
let message = greet("Andrew");
print(message);

// 箭頭函數 (現代標準)
const add = (a, b) => a + b;
print(add(5, 10)); // 15

// 作用域範例
let globalVar = "我是全域變數";
function testScope() {
    let localVar = "我是區域變數";
    print(globalVar); // ✅ 能看到全域
    print(localVar);  // ✅ 能看到區域
}
testScope();
// print(localVar); // ❌ 報錯：函數外找不到 localVar

// 閉包：私有計數器
function createCounter() {
    let count = 0;
    return function() {
        count++;
        return count;
    };
}
const counter = createCounter();
print(counter()); // 1
print(counter()); // 2
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 全域變數濫用導致命名衝突 | 用閉包或模組模式封裝私有狀態 |
| 在迴圈中用 `var` 建立閉包 | 用 `let` 或 IIFE 捕捉迴圈變數 |
| 不理解 `this` 指向 | 優先使用箭頭函數避免 `this` 綁定問題 |
| 函數過長難維護 | 拆分為單一職責的小函數 |

## 🔗 關聯連結

- [[運算符與控制流程]]：if/else 與迴圈
- [[DOM 操作]]：JS 控制 HTML 元素
- [[Event Loop]]：JS 單執行緒與事件循環
- [[陣列與物件]]：高階函數常回調函數作為參數

## 🏷️ 標籤

#JS #函數 #箭頭函數 #作用域 #閉包 #Closure
