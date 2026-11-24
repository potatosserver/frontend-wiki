# 02. 運算符與控制流程 (Operators and Control Flow)

如果你能儲存數據，但不能處理數據，那程式就只是一個記事本。要讓程式具備「邏輯」，我們需要 **運算符 (Operators)** 與 **控制流程 (Control Flow)**。

本章的所有練習請繼續在 `js-playground.html` 中完成。

---

## 1. 數據加工：運算符 (Operators)

### A. 算術運算符 (算術計算)
最基礎的數學運算：`+`, `-`, `*`, `/`, `%` (取餘數)。

**🚀 實作範例：**
```javascript
let a = 10;
let b = 3;
print("加法: " + (a + b)); // 13
print("餘數: " + (a % b)); // 1 (10除以3餘1)
```

### B. 比較運算符 (對錯判斷)
結果永遠是 `true` 或 `false` (布林值)。
- `===` $\rightarrow$ **嚴格相等** (數值與型別都必須一樣 $\rightarrow$ 專業推薦)。
- `!==` $\rightarrow$ **不相等**。
- `>`, `<`, `>=`, `<=` $\rightarrow$ 大小比較。

**💡 陷阱：為什麼不用 `==`？**
`==` 會嘗試自動轉換型別 (例如 `"5" == 5` 是 true)，這會導致莫名其妙的 Bug。**永遠使用 `===`。**

---

## 2. 邏輯控制：if / else (抉擇)

`if` 就像是程式的「分叉路口」。

**🚀 視覺化實作：年齡檢查器**
```javascript
let age = 18;

if (age >= 18) {
    print("✅ 你已成年，可以進入本網站。");
} else if (age >= 12) {
    print("⚠️ 你是青少年，部分內容受限。");
} else {
    print("❌ 你太小了，請先詢問家長。");
}
```

---

## 3. 自動化重複：迴圈 (Loops)

如果你想印出 1 到 100，你不會寫 100 行 `print`，而會使用迴圈。

### A. `for` 迴圈 (已知次數)
最常用的迴圈，適合明確知道要執行幾次的情況。
```javascript
// 結構：(起始值 ; 結束條件 ; 每次增加多少)
for (let i = 1; i <= 5; i++) {
    print("這是第 " + i + " 次重複執行");
}
```

### B. `while` 迴圈 (條件達成才停止)
適合不知道要跑幾次，只知道「只要條件成立就繼續」的情況。
```javascript
let energy = 3;
while (energy > 0) {
    print("正在工作... 能量剩餘: " + energy);
    energy--; // 記得減少能量，否則會變成「死迴圈」導致瀏覽器崩潰！
}
print("能量耗盡，休息時間！");
```

---

## 🛠️ 實驗場實作挑戰

請在 `js-playground.html` 中完成以下任務：

1. **偶數過濾器**：使用 `for` 迴圈印出 1 到 20 之間的所有 **偶數** (提示：使用 `% 2 === 0`)。
2. **成績分級系統**：
   - 建立變數 `score = 85`。
   - 使用 `if/else` 判斷：$\ge 90$ (優秀), $\ge 60$ (及格), $< 60$ (不及格) $\rightarrow$ 印出對應結果。
3. **倒數計時**：使用 `while` 迴圈實作一個從 5 倒數到 1 的程式，最後印出 "發射！"。

---
<p align="center">
<a href="01-basics-and-variables.md">01-basics-and-variables ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/js/02-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="03-functions-and-scope.md">03-functions-and-scope ➡️</a>
</p>
