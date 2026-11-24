---
id: 01-01
module: html
title: 骨架與編碼
status: published
tags:
  - "#HTML"
  - "#骨架"
  - "#編碼"
  - "#UTF-8"
  - "#SEO"
summary: HTML5 基礎骨架結構、<!DOCTYPE> 聲明、lang 屬性與 UTF-8 編碼設定，避免亂碼與 Quirks Mode。
source: raw/01-skeleton-and-encoding.md
last_updated: 2026-11-24
related:
  - "[[語義化 HTML]]"
  - "[[Viewport 設定]]"
---

# 骨架與編碼

> 一個網頁檔案本質上是純文字檔，透過標準 HTML5 骨架與 UTF-8 編碼，讓瀏覽器正確解析與顯示內容。

## 🎯 為什麼 (Why)

在學習任何華麗特效前，必須先理解網頁的「地基」。錯誤的骨架設定會導致瀏覽器進入 **Quirks Mode（怪異模式）**，造成跨瀏覽器佈局崩潰；缺少 UTF-8 則會導致中文顯示為亂碼。

## 🧠 核心概念

### HTML5 基礎骨架

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <title>頁面標題</title>
</head>
<body>
    <h1>你好，世界！</h1>
    <p>這是頁面內容。</p>
</body>
</html>
```

### 各區塊作用

| 標籤 | 作用 | 說明 |
|------|------|------|
| `<!DOCTYPE html>` | 文檔類型聲明 | 告訴瀏覽器使用 HTML5 標準解析，避免 Quirks Mode |
| `<html lang="zh-Hant">` | 根元素 | 定義頁面語言，影響 SEO 與螢幕閱讀器 |
| `<head>` | 元數據區 | 給瀏覽器看的資訊（編碼、標題、CSS、SEO 標籤） |
| `<body>` | 內容區 | 給使用者看的內容（文字、圖片、按鈕） |

### `<meta charset="UTF-8">` 的重要性

UTF-8 是全球統一的字符編碼標準。若未設定，瀏覽器可能使用舊編碼（如 Windows-1252、Big5）讀取，導致中文顯示為 `??` 或 `SòSò`（亂碼 / Mojibake）。

**專業習慣**：永遠在 `<head>` 的第一行寫上 `<meta charset="UTF-8">`。

## 💻 Code Snippet

```html
<!-- 最簡單 HTML5 骨架，複製即用 -->
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的網頁</title>
</head>
<body>
    <h1>你好，世界！</h1>
    <p>這是我學習前端的第一步。</p>
</body>
</html>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 缺少 `<!DOCTYPE html>` | 必須寫在第一行，觸發標準模式 |
| 中文頁面沒設定 `lang` | 設定 `lang="zh-Hant"` 利於 SEO 與 A11y |
| `<meta charset>` 放在 `<head>` 後半段 | 放在 `<head>` 第一行，優先生效 |
| 直接用 `<div>` 堆疊所有內容 | 後續改用語義化標籤（見 [[語義化 HTML]]） |

## 🔗 關聯連結

- [[語義化 HTML]]：HTML5 語義化標籤詳解
- [[Viewport 設定]]：響應式設計的基礎設定

## 🏷️ 標籤

#HTML #骨架 #編碼 #UTF-8 #SEO
