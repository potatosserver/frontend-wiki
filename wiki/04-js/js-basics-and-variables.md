---
id: 04-01
module: js
title: 基礎與變數
status: published
tags: [#JS, #變數, #let, #const, #資料型別, #JavaScript]
summary: JavaScript 變數宣告 (let/const)、資料型別 (String/Number/Boolean/null/undefined) 與實驗場使用方式。
source: raw/01-basics-and-variables.md
last_updated: 2026-11-24
related:
  - [[運算符與控制流程]]
  - [[函數與作用域]]
---

# 基礎與變數

> JavaScript 是網頁的「肌肉與神經」，讓網頁能對使用者操作做出反應。變數是儲存數據的「標籤盒子」。

## 🎯 為什麼 (Why)

在學習複雜邏輯前，必須先建立低壓力練習環境，專注於程式碼邏輯而不必擔心 HTML 標籤錯誤。變數是所有程式邏輯的起點，不理解變數就無法處理數據。

## 🧠 核心概念

### JS 實驗場 (Playground)

使用 `js-playground.html` 作為練習環境：
1. 找到底部 `<script>` 標籤
2. 撰寫 JS 代碼
3. 使用 `print("內容")` 將結果印在頁面黑盒子
4. 保存 → 刷新瀏覽器 → 查看結果

### 變數宣告 (`let` vs `const`)

| 關鍵字 | 特性 | 適用場景 |
|--------|------|----------|
| `let` | 可重新賦值 | 數據會改變（如使用者得分、頁碼） |
| `const` | 不可重新賦值 | 數據不會改變（如生日、網域名） |

**專業習慣**：除非確定變數需要修改，否則優先使用 `const`，防止大型專案中不小心改掉重要數據。

### 資料型別

| 型別 | 範例 | 用途 |
|------|------|------|
| String | `"Andrew"` | 文字內容，必須用引號 |
| Number | `42` 或 `3.14` | 所有數字 (整數、浮點數) |
| Boolean | `true` / `false` | 開關/對錯判斷，常用於 `if` |
| Null | `null` | 刻意設定為空 |
| Undefined | `undefined` | 尚未定義 |

## 💻 Code Snippet

```javascript
// 可變變數：分數會改變
let score = 0;
print("初始得分: " + score);
score = 10;
print("更新後得分: " + score);

// 不可變常量：生日不會改變
const birthYear = 1995;
// birthYear = 1996; // ❌ 報錯，const 不能修改

// 資料型別範例
const myName = "Andrew";      // String
let age = 25;                 // Number
let isStudent = true;         // Boolean

print("名稱: " + myName);
print("年齡: " + age);
print("是否為學生: " + isStudent);
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 全部用 `let` 宣告 | 優先用 `const`，只有會改變的才用 `let` |
| 字串不加引號 | 字串必須用 `""` 或 `''` 包裹 |
| 在 Playground 外寫 JS | 先在 `js-playground.html` 驗證邏輯 |
| 忽略資料型別差異 | 了解 `===` 與 `==` 的型別比較差異 |

## 🔗 關聯連結

- [[運算符與控制流程]]：運算符與 if/else 迴圈
- [[函數與作用域]]：函數定義與閉包

## 🏷️ 標籤

#JS #變數 #let #const #資料型別 #JavaScript
