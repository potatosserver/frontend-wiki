# 02. 掌控空間與間距 (Box Model and Units)

如果你想讓網頁上的元素精確地排列在某個位置，或者讓間距看起來舒服，你必須理解 CSS 的核心物理模型：**盒模型 (Box Model)**。

在瀏覽器眼中，網頁上的每一個元素 (不論是文字、圖片還是按鈕) 全都被包裹在一個**透明的矩形盒子**中。

---

## 1. 盒子的組成部分 (The Box Model)

從內到外，一個盒子由四層組成：

### A. Content (內容)
- 實際顯示文字或圖片的地方。
- 由 `width` 和 `height` 控制。

### B. Padding (內邊距)
- 內容與邊框之間的空間。
- **專業視角**：Padding 用於讓內容「呼吸」，避免文字直接貼在邊框上。

### C. Border (邊框)
- 包裹在內邊距外的線條。
- 可以設定粗細、樣式 (`solid`, `dashed`, `dotted`) 和顏色。

### D. Margin (外邊距)
- 盒子與盒子之間的距離。
- 用於推開鄰近的元素，創造佈局間距。

---

## 2. 致命陷阱：`content-box` vs `border-box`

這是所有初學者最常遇到的噩夢：**「為什麼我設定寬度 100%，加上 Padding 後網頁就出現水平滾動條？」**

### A. `box-sizing: content-box` (預設值)
- **邏輯**：設定的 `width` 僅指 **Content**。
- **計算公式**：`實際總寬度 = width + left/right padding + left/right border`。
- **結果**：如果你設定 `width: 100%` 並加上 `padding: 20px` $\rightarrow$ 總寬度變成了 `100% + 40px` $\rightarrow$ **佈局爆掉**。

### B. `box-sizing: border-box` (專業標準)
- **邏輯**：設定的 `width` 是 **整個盒子的總寬度**。
- **計算公式**：瀏覽器會自動壓縮 Content 的寬度，以確保總寬度等於你設定的 `width`。
- **結果**：`width: 100%` 永遠是 100% $\rightarrow$ **佈局穩固**。

**🚀 專業習慣：全域重設**
在每個專案的 CSS 最頂端，請務必加上這段代碼，強制所有元素使用 `border-box`：
```css
* {
  box-sizing: border-box;
}
```

---

## 3. 單位系統 (CSS Units)

不要只使用 `px`！專業工程師會根據不同場景選擇最合適的單位，以實現**響應式設計**。

### A. 絕對單位 $\rightarrow$ `px` (Pixels)
- **特點**：固定不變。
- **適用場景**：極小的邊框 (`border: 1px solid`)，或需要精確到像素的圖標大小。

### B. 相對單位 (基於字體) $\rightarrow$ `rem` vs `em`
- **`rem` (Root em)**：相對於 HTML 根元素的字體大小 (預設 1rem = 16px)。
  - **優點**：全站統一縮放。如果使用者在瀏覽器設定中調大字體，`rem` 會同步縮放 $\rightarrow$ **無障礙友好**。
- **`em`**：相於**父元素**的字體大小。
  - **適用場景**：希望某個元件的內邊距隨其字體大小按比例縮放時使用。

### C. 相對單位 (基於視窗) $\rightarrow$ `vw`, `vh` 與現代的 `dvh`
- **`vw` (Viewport Width)**：視窗寬度的 1%。`100vw` = 螢幕滿寬。
- **`vh` (Viewport Height)**：視窗高度的 1%。`100vh` = 螢幕滿高。

**⚠️ 現代開發陷阱：`100vh` 在手機上的失效**
在手機瀏覽器上，`100vh` 經常會包含「地址欄」的高度。這導致當你設定 `height: 100vh` 時，頁面底部的一部分會被地址欄遮住。

**🚀 專業解決方案：動態視口單位 (Dynamic Viewport)**
為了徹底解決這個問題，現代 CSS 引入了新的單位：
- **`dvh` (Dynamic Viewport Height)**：**動態視口高度**。它會根據地址欄的顯示/隱藏狀態，實時計算真正可見的區域。
- **`dvw` (Dynamic Viewport Width)**：**動態視口寬度**。

**實作建議**：在製作「全螢幕首頁」或「全螢屏 Modal」時，請優先使用 `100dvh` 而非 `100vh`。

### D. 百分比 `%`
- 相對於 **父元素** 的寬度或高度。

**🚀 單位選擇矩陣：**
| 需求 | 推薦單位 | 原因 |
| :--- | :--- | :--- |
| 基礎字體大小 | `rem` | 支援使用者縮放，符合 A11y 規範 |
| 佈局寬度 | `%` 或 `vw` | 隨螢幕寬度自適應 |
| 內外邊距 | `rem` 或 `px` | 保持一致的視覺節奏 |
| 滿屏背景 | `100dvh` | 確保在手機端也完美填滿可見區域 |

---

## 🛠️ 主專案功能疊加

現在，將視覺層次引入你的主專案：

1. ** Hero Section 尺寸**：設定 `padding` 與 `max-width`，並使其水平居中。
2. **建立卡片視覺**：為 About 區塊建立一個白色背景、帶圓角與輕微陰影的卡片容器。
3. **單位應用**：將標題字體改用 `rem` 單位，確保可縮放性。

---
<p align="center">
<a href="01-intro-and-selectors.md">01-intro-and-selectors ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/css/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-positioning-and-zindex.md">03-positioning-and-zindex ➡️</a>
</p>
