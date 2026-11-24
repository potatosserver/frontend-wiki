# 07. 引擎與事件循環 (Engine and Event Loop)

恭喜！你已經掌握了 JS 的基本語法與異步開發。但如果你想從「會寫代碼」晉升為「專業工程師」，你必須理解 JS 在底層是如何運行的。

---

## 1. JS 是單執行緒 (Single-threaded)

JS 一次只能做一件事。如果你寫了一個死迴圈 `while(true) {}` $\rightarrow$ 瀏覽器會立即崩潰 $\rightarrow$ 因為主執行緒被佔滿了，無法處理任何點擊或渲染。

**🚀 視覺實驗 (在 Playground 執行)：**
```javascript
// 警告：這會讓頁面短暫卡死
for(let i=0; i<1000000000; i++) {
    // 模擬大量計算
}
print("計算完成！");
```

---

## 2. 解決方案：Event Loop (事件循環)

既然一次只能做一件事，JS 是如何處理異步請求（如 `fetch`）而不會卡死的？
答案是：**任務隊列 (Task Queue)**。

- **Call Stack (調用棧)**：目前正在執行的任務。
- **Task Queue (任務隊列)**：等待執行的異步任務 (如 setTimeout)。
- **Event Loop**：不斷檢查 $\rightarrow$ 如果 Call Stack 空了 $\rightarrow$ 就從 Queue 裡拿一個任務進來執行。

---

## 3. 微任務 (Microtask) vs 宏任務 (Macrotask)

並非所有異步任務都一樣。`Promise` 的優先級高於 `setTimeout`。

**🚀 實作驗證：**
```javascript
console.log("1. 開始");

setTimeout(() => console.log("2. setTimeout (宏任務)"), 0);

Promise.resolve().then(() => console.log("3. Promise (微任務)"));

console.log("4. 結束");
```
**輸出結果**：`1 $\rightarrow$ 4 $\rightarrow$ 3 $\rightarrow$ 2`。
**原因**：微任務 (Promise) 在當前執行棧清空後優先執行 $\rightarrow$ 宏任務 (setTimeout) 最後執行。

---

## 🛠️ 主專案效能優化

現在，思考如何優化你的作品集效能：

1. **避免主執行緒阻塞**：將繁重的數據處理邏輯（如果有）拆分為小塊，使用 `setTimeout(..., 0)` 讓瀏覽器有時間渲染 UI。
2. **優化加載順序**：將不緊急的 JS 標籤加上 `defer` 屬性，確保 HTML 先渲染完成，再執行 JS。

---
<p align="center">
<a href="06-async-and-promises.md">06-async-and-promises ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/js/07-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="../05-The-Art-of-F12-and-API/01-f12-mastery.md">01-f12-mastery ➡️</a>
</p>
