# 06. 異步與 Promise (Async and Promises)

在之前的章節中，所有的 JS 代碼都是「同步」執行的 $\rightarrow$ 只要有一行代碼執行時間很長，整個網頁就會直接卡死。

為了處理需要時間的操作（例如：從伺服器下載數據），JS 引入了 **異步 (Asynchronous)** 機制。

---

## 1. 視覺問題：為什麼頁面會卡死？

想像你在餐廳點餐。
- **同步**：服務生接單後，站在廚房等菜做好 $\rightarrow$ 期間不接任何新單 $\rightarrow$ 店鋪崩潰。
- **異步**：服務生接單 $\rightarrow$ 給你一個「號碼牌 (Promise)」 $\rightarrow$ 他繼續接單 $\rightarrow$ 菜好了通知你。

---

## 2. 現代標準：`async` 與 `await`

以前我們使用 `.then()`，現在專業標準是使用 `async/await` $\rightarrow$ 讓異步代碼看起來像同步代碼一樣簡潔。

**🚀 實作範例：獲取隨機金句**
```javascript
async function getQuote() {
    try {
        // 1. 發送請求 (await 會在這裡等待，但不會卡死瀏覽器)
        const response = await fetch('https://api.quotable.io/random');
        
        // 2. 將結果轉為 JSON
        const data = await response.json();
        
        // 3. 顯示在頁面上
        document.querySelector('#quote').innerText = data.content;
    } catch (error) {
        console.error("獲取失敗:", error);
    }
}

// 執行
getQuote();
```

---

## 3. 異步體驗優化：Loading 狀態

專業的網頁在數據還沒回來前，不會讓頁面空白，而會顯示「加載中...」。

**實作邏輯：**
1. `innerText = "加載中..."` $\rightarrow$ 顯示 Loading。
2. `await fetch(...)` $\rightarrow$ 等待數據。
3. `innerText = data.content` $\rightarrow$ 替換為真實數據。

---

## 🛠️ 主專案功能疊加

現在，為你的主專案加入真實數據：

1. **隨機金句區塊**：在 Hero Section 下方增加一個 `div` $\rightarrow$ 實作 `async` 函數從 API 抓取金句並顯示。
2. **加載狀態**：在數據回來前顯示「正在同步最新數據...」。
3. **錯誤處理**：如果 API 失效，顯示「目前無法連線，請稍後再試」。

---
<p align="center">
<a href="05-array-and-object-deep-dive.md">05-array-and-object-deep-dive ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/js/06-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="07-engine-and-event-loop.md">07-engine-and-event-loop ➡️</a>
</p>
