# 03. 表單與輸入元件 (Forms and Inputs)

在之前的章節中，我們學習了如何「展示」內容。但真正的網頁應用需要能與使用者「互動」。**表單 (Forms)** 是網頁獲取使用者輸入、處理數據提交的最核心方式。

一個專業的表單不僅要能運作，還必須具備**極佳的可用性 (Usability)** 和**基礎的客戶端驗證 (Validation)**。

---

## 1. 表單的基本結構 `<form>`

所有的輸入元件都應該被包裹在 `<form>` 標籤中。

### 核心屬性
- `action`：數據提交的目的地 (URL)。例如 `/submit-form`。
- `method`：提交數據的方式。
  - `GET`：將數據附加在 URL 後面 (例如 `?name=John`)。適用於搜尋、篩選。
  - `POST`：將數據放在請求體中。適用於登入、上傳檔案、提交私密資料。

**🚀 基礎構造範例：**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>03-forms-and-inputs</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <form action="/submit" method="POST">
    <!-- 這裡放置輸入元件 -->
    <button type="submit">提交</button>
</form>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 2. 輸入元件 `<input>`：萬能的變色龍

`<input>` 標籤透過 `type` 屬性來決定它要變成什麼樣的輸入框。

### 常用的 Input 類型
| 類型 (`type`) | 用途 | 專業特性 |
| :--- | :--- | :--- |
| `text` | 普通文字 | 最基礎的單行輸入。 |
| `password` | 密碼 | 輸入內容會變成星號或圓點 $\bullet$。 |
| `email` | 電子郵件 | 行動裝置會自動彈出 `@` 鍵盤 $\rightarrow$ 內建格式檢查。 |
| `number` | 數字 | 限制只能輸入數字 $\rightarrow$ 可設定 `min`, `max`, `step`。 |
| `date` | 日期選擇 | 彈出原生日期選擇器。 |
| `checkbox` | 複選框 | 可多選 $\rightarrow$ 需設定 `name` 屬性以分組。 |
| `radio` | 單選鈕 | 只能單選 $\rightarrow$ 必須設定相同的 `name` 屬性。 |
| `file` | 檔案上傳 | 讓使用者選擇本地檔案。 |

---

## 3. 標籤綁定 `<label>`：可用性的關鍵

**絕對不要**只用 `<div>` 或 `<span>` 來寫輸入框的標題。必須使用 `<label>`。

### 為什麼要用 `<label>`？
1. **點擊範圍擴大**：點擊 Label 的文字，輸入框會自動獲取焦點 (Focus)。
2. **無障礙支持**：螢幕閱讀器能精確告訴視障人士這個輸入框是用來做什麼的。

**🚀 專業綁定方式 (使用 `for` 與 `id`)：**
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>03-forms-and-inputs</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <!-- label 的 for 必須等於 input 的 id -->
<label for="user-email">電子郵件：</label>
<input type="email" id="user-email" name="email" required>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 4. 其他重要輸入元件

### A. 下拉選單 `<select>` 與 `<option>`
適用於提供固定選項，且希望節省空間的場景。
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>03-forms-and-inputs</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <label for="city">選擇城市：</label>
<select id="city" name="city">
    <option value="tpe">台北</option>
    <option value="ckg" selected>台中</option> <!-- selected 為預設選項 -->
    <option value="ksg">高雄</option>
</select>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

### B. 多行文字區 `<textarea>`
適用於留言、詳細描述等長文本。
```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>03-forms-and-inputs</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <label for="bio">個人簡介：</label>
<textarea id="bio" name="bio" rows="5" cols="30" placeholder="請介紹你自己..."></textarea>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 5. HTML5 原生驗證 (Validation)

在將數據送往伺服器之前，我們可以使用 HTML 屬性快速進行初步檢查，減少無效請求。

- `required`：該欄位必填，不填不能提交。
- `minlength` / `maxlength`：限制文字長度。
- `min` / `max`：限制數字範圍。
- `pattern`：使用 **正則表達式 (Regex)** 定義精確格式 (例如：手機號碼必須是 10 位數字)。

---

## 🚀 綜合實作：專業註冊表單

請嘗試將以下代碼複製到你的 `index.html` 中，觀察其運作方式：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>03-forms-and-inputs</title>
</head>
<body>
    <!-- ⚡️ 本章重點實作開始 -->
    <section>
    <h2>加入會員</h2>
    <form action="/register" method="POST">
        <!-- 文本輸入 -->
        <div style="margin-bottom: 15px;">
            <label for="username">使用者名稱：</label>
            <input type="text" id="username" name="username" required minlength="3" placeholder="至少 3 個字">
        </div>

        <!-- 密碼輸入 -->
        <div style="margin-bottom: 15px;">
            <label for="pwd">密碼：</label>
            <input type="password" id="pwd" name="pwd" required>
        </div>

        <!-- 郵件輸入 -->
        <div style="margin-bottom: 15px;">
            <label for="email">電子郵件：</label>
            <input type="email" id="email" name="email" required>
        </div>

        <!-- 單選鈕 -->
        <div style="margin-bottom: 15px;">
            <p>請選擇你的主要興趣：</p>
            <input type="radio" id="web" name="interest" value="web" checked>
            <label for="web">網頁開發</label>
            <input type="radio" id="app" name="interest" value="app">
            <label for="app">App 開發</label>
            <input type="radio" id="data" name="interest" value="data">
            <label for="data">數據分析</label>
        </div>

        <!-- 複選框 -->
        <div style="margin-bottom: 15px;">
            <input type="checkbox" id="terms" name="terms" required>
            <label for="terms">我同意使用者服務條款</label>
        </div>

        <!-- 提交按鈕 -->
        <button type="submit">立即註冊</button>
    </form>
</section>
    <!-- ⚡️ 本章重點實作結束 -->
</body>
</html>
```

---

## 🛠️ 主專案功能疊加

現在，在你的主專案中加入『聯絡我』功能：

1. **表單建立**：建立一個 `<form>` 並設定 `method="POST"`。
2. **輸入欄位**：實作 姓名、電子郵件 (type="email") 與訊息內容 (textarea)。
3. **可用性優化**：為每個輸入框加上正確的 `<label>` 綁定。
4. **驗證**：設定必填項 `required` 並限制名稱最少 2 個字。

---
<p align="center">
<a href="02-text-and-basic-tags.md">02-text-and-basic-tags ⬅️</a> &nbsp; | &nbsp; <a href="../solutions/html/03-sol.md">🎯 本章解答</a> &nbsp; | &nbsp; <a href="04-multimedia-and-tables.md">04-multimedia-and-tables ➡️</a>
</p>
