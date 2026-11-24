---
id: 04-07
module: js
title: 引擎與事件循環
status: published
tags: ["#JS", "#EventLoop", "#單執行緒", "#CallStack", "#TaskQueue", "#Microtask", "#Macrotask""]
summary: JavaScript 單執行緒本質、Call Stack、Task Queue、Event Loop、微任務與宏任務優先級。
source: raw/07-engine-and-event-loop.md
last_updated: 2026-11-24
related:
  - [[異步與 Promise]]
  - [[MOC: 瀏覽器渲染與效能優化]]
---

# 引擎與事件循環

> JS 一次只能做一件事 (單執行緒)，Event Loop 是讓異步不卡死瀏覽器的底層機制。

## 🎯 為什麼 (Why)

從「會寫代碼」晉升為「專業工程師」，必須理解 JS 底層運行方式。知道 Event Loop 才能避免主執行緒阻塞、優化加載順序、理解 `Promise` 與 `setTimeout` 的執行順序。

## 🧠 核心概念

### JS 是單執行緒 (Single-threaded)

JS 一次只能執行一個任務。若寫死迴圈 `while(true) {}`，瀏覽器會立即卡死，因為主執行緒被佔滿，無法處理點擊或渲染。

### Event Loop 三大要素

| 元素 | 說明 |
|------|------|
| **Call Stack** | 目前正在執行的任務堆疊 |
| **Task Queue** | 等待執行的異步任務 (如 `setTimeout`) |
| **Event Loop** | 不斷檢查：若 Call Stack 空了，就從 Task Queue 拿任務執行 |

### 微任務 (Microtask) vs 宏任務 (Macrotask)

並非所有異步任務優先級相同：

| 類型 | 範例 | 優先級 |
|------|------|--------|
| 微任務 | `Promise.then()`, `queueMicrotask()` | **較高** |
| 宏任務 | `setTimeout`, `setInterval`, I/O | 較低 |

**執行順序**：同步代碼 → 微任務 → 宏任務

### 實作驗證

```javascript
console.log("1. 開始");

setTimeout(() => console.log("2. setTimeout (宏任務)"), 0);

Promise.resolve().then(() => console.log("3. Promise (微任務)"));

console.log("4. 結束");
```

**輸出結果**：`1 → 4 → 3 → 2`

**原因**：微任務 (Promise) 在當前執行棧清空後優先執行，宏任務 (setTimeout) 最後執行。

## 💻 Code Snippet

```javascript
// 避免主執行緒阻塞：將繁重處理拆分
function processLargeData(data) {
    // 不要一次處理全部，用 setTimeout(..., 0) 讓瀏覽器有時間渲染 UI
    setTimeout(() => {
        data.forEach(item => {
            // 繁重計算...
        });
    }, 0);
}

// 優化加載順序：非緊急 JS 加上 defer
// <script src="app.js" defer></script>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 在主執行緒做大量計算 | 用 `setTimeout(..., 0)` 或 Web Workers 拆分任務 |
| 誤以為 `setTimeout(..., 0)` 會立即執行 | 它會進入宏任務隊列，在微任務之後執行 |
| 所有 `<script>` 都在 `<head>` 且無 defer | 非緊急 JS 加上 `defer`，確保 HTML 先渲染 |
| 以為 Promise 與 setTimeout 同時完成 | Promise (微任務) 優先於 setTimeout (宏任務) |

## 🔗 關聯連結

- [[異步與 Promise]]：async/await 與 fetch
- [[MOC: 瀏覽器渲染與效能優化]]：跨模組效能主題

## 🏷️ 標籤

#JS #EventLoop #單執行緒 #CallStack #TaskQueue #Microtask #Macrotask
