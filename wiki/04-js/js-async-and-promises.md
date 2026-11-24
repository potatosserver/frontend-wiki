---
id: 04-06
module: js
title: 異步與 Promise
status: published
tags: [#JS, #異步, #Async, #Await, #Promise, #fetch, #API]
summary: async/await 現代異步標準、fetch API 抓取數據、Loading 狀態與錯誤處理。
source: raw/06-async-and-promises.md
last_updated: 2026-11-24
related:
  - [[陣列與物件]]
  - [[Event Loop]]
  - [[MOC: 瀏覽器渲染與效能優化]]
---

# 異步與 Promise

> 同步代碼會卡死瀏覽器，異步機制讓網頁在等待伺服器數據時仍能回應使用者操作。

## 🎯 為什麼 (Why)

同步執行時，若某行代碼耗時較長，整個網頁會直接卡死。異步機制（如 `fetch`）讓瀏覽器在等待數據時繼續處理其他操作，`async/await` 則讓異步代碼看起來像同步一樣簡潔。

## 🧠 核心概念

### 同步 vs 異步類比

| 模式 | 類比 | 行為 |
|------|------|------|
| 同步 | 服務生站在廚房等菜 | 整個店鋪停止接單 → 瀏覽器卡死 |
| 異步 | 服務生給號碼牌 (Promise) | 繼續接單，菜好了通知使用者 → 瀏覽器保持回應 |

### async/await 現代標準

```javascript
async function getQuote() {
    try {
        const response = await fetch('https://api.quotable.io/random');
        const data = await response.json();
        document.querySelector('#quote').innerText = data.content;
    } catch (error) {
        console.error("獲取失敗:", error);
    }
}
getQuote();
```

### Loading 狀態優化

專業網頁在數據未回來前不會空白，會顯示「加載中...」：

1. `innerText = "加載中..."` → 顯示 Loading
2. `await fetch(...)` → 等待數據
3. `innerText = data.content` → 替換為真實數據

### 錯誤處理

使用 `try/catch` 捕捉 `fetch` 失敗，顯示友善錯誤訊息而非讓頁面崩潰。

## 💻 Code Snippet

```javascript
async function getQuote() {
    const quoteEl = document.querySelector('#quote');
    
    try {
        // 顯示 Loading
        quoteEl.innerText = "正在同步最新數據...";
        
        // 等待 API 回應 (不會卡死瀏覽器)
        const response = await fetch('https://api.quotable.io/random');
        const data = await response.json();
        
        // 顯示結果
        quoteEl.innerText = data.content;
    } catch (error) {
        // 錯誤處理
        quoteEl.innerText = "目前無法連線，請稍後再試";
        console.error("獲取失敗:", error);
    }
}

// 執行
getQuote();
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 用 `.then()` 鏈式呼叫 (舊標準) | 用 `async/await` (現代標準，可讀性更高) |
| `fetch` 失敗沒處理 | 用 `try/catch` 捕捉錯誤，顯示友善訊息 |
| 數據加載中頁面空白 | 顯示「加載中...」Loading 狀態 |
| 忘記 `await` 導致 race condition | 確保每個非同步操作都加 `await` |

## 🔗 關聯連結

- [[陣列與物件]]：將 API 數據渲染到頁面
- [[Event Loop]]：JS 異步底層運作原理
- [[MOC: 瀏覽器渲染與效能優化]]：跨模組效能主題

## 🏷️ 標籤

#JS #異步 #Async #Await #Promise #fetch #API
