---
id: 01-03
module: html
title: 表單與輸入
status: published
tags: ["#HTML", "#表單", "#輸入", "#驗證", "#A11y""]
summary: HTML 表單結構、輸入元件類型、label 綁定與 HTML5 原生驗證屬性。
source: raw/03-forms-and-inputs.md
last_updated: 2026-11-24
related:
  - [[語義化 HTML]]
  - [[DOM 操作]]
---

# 表單與輸入

> 表單是網頁獲取使用者輸入的核心方式，必須具備可用性與基礎客戶端驗證。

## 🎯 為什麼 (Why)

專業表單不僅要能運作，還必須讓使用者好填、讓螢幕閱讀器能正確朗讀。缺少 `<label>` 綁定會導致視障使用者無法理解輸入欄位；缺少 `required` 則會增加無效請求。

## 🧠 核心概念

### 表單結構 (`<form>`)

| 屬性 | 說明 | 適用場景 |
|------|------|----------|
| `action` | 數據提交目的地 URL | `/submit-form` |
| `method="GET"` | 數據附加在 URL | 搜尋、篩選 |
| `method="POST"` | 數據放在請求體 | 登入、上傳、私密資料 |

### 輸入元件 `<input>` 常用類型

| 類型 | 用途 | 專業特性 |
|------|------|----------|
| `text` | 普通文字 | 最基礎單行輸入 |
| `password` | 密碼 | 輸入顯示為星號 |
| `email` | 電子郵件 | 行動裝置彈出 `@` 鍵盤，內建格式檢查 |
| `number` | 數字 | 限制數字輸入，可設 `min`/`max`/`step` |
| `date` | 日期 | 彈出原生日期選擇器 |
| `checkbox` | 複選框 | 可多選，需設定 `name` 分組 |
| `radio` | 單選鈕 | 只能單選，必須相同 `name` |
| `file` | 檔案上傳 | 選擇本地檔案 |

### `<label>` 綁定（可用性關鍵）

必須使用 `<label>` 與 `<input>` 的 `for`/`id` 綁定，點擊標籤文字即可聚焦輸入框，且螢幕閱讀器能正確朗讀。

### HTML5 原生驗證屬性

- `required`：必填，不填不能提交
- `minlength` / `maxlength`：文字長度限制
- `min` / `max`：數字範圍限制
- `pattern`：正則表達式格式檢查

## 💻 Code Snippet

```html
<form action="/register" method="POST">
    <div style="margin-bottom: 15px;">
        <label for="username">使用者名稱：</label>
        <input type="text" id="username" name="username" required minlength="3" placeholder="至少 3 個字">
    </div>
    <div style="margin-bottom: 15px;">
        <label for="email">電子郵件：</label>
        <input type="email" id="email" name="email" required>
    </div>
    <button type="submit">立即註冊</button>
</form>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 只用 `<div>` 寫標題 | 使用 `<label>` 綁定 `for`/`id` |
| 沒設定 `required` | 必填欄位加上 `required` |
| 密碼用 `type="text"` | 使用 `type="password"` 隱藏輸入 |
| 郵件欄位不做格式檢查 | 使用 `type="email"` 內建格式驗證 |

## 🔗 關聯連結

- [[語義化 HTML]]：語義化標籤與 A11y
- [[DOM 操作]]：JS 監聽表單 submit 事件

## 🏷️ 標籤

#HTML #表單 #輸入 #驗證 #A11y
