---
id: 01-04
module: html
title: 多媒體與表格
status: published
tags: [#HTML, #圖片, #影片, #音訊, #表格, #A11y]
summary: 圖片 `alt` 替代文字、音影元素 `<video>`/`<audio>` 與語義化數據表格 `<table>` 的正確用法。
source: raw/04-multimedia-and-tables.md
last_updated: 2026-11-24
related:
  - [[語義化 HTML]]
  - [[A11y 無障礙與 SEO]]
---

# 多媒體與表格

> 圖片與表格是視覺化資訊的核心，正確的 `alt` 文字與語義結構對 A11y 與 SEO 至關重要。

## 🎯 為什麼 (Why)

圖片若沒有 `alt` 屬性，視障使用者無法得知圖片內容，Google 也無法理解圖片語意。表格若不使用 `<thead>`、`<tbody>`、`<th>`，螢幕閱讀器將難以解讀數據關聯。

## 🧠 核心概念

### 圖片 ``

| 屬性 | 說明 |
|------|------|
| `src` | 圖片路徑（絕對或相對） |
| `alt` | **替代文字**，圖片失敗時顯示，螢幕閱讀器朗讀，SEO 索引 |

### 音影元素

| 標籤 | 關鍵屬性 | 說明 |
|------|----------|------|
| `<video>` | `controls`, `poster`, `muted`, `autoplay` | 播放控制、封面、靜音自動播放 |
| `<audio>` | `controls` | 音訊播放控制 |

### 數據表格 `<table>`

| 標籤 | 說明 |
|------|------|
| `<thead>` | 表頭區域 |
| `<tbody>` | 主體數據 |
| `<tfoot>` | 底部（如總計） |
| `<tr>` | 一行 |
| `<th>` | 標題單元格（預設粗體置中） |
| `<td>` | 普通數據單元格 |
| `colspan` / `rowspan` | 合併橫向/縱向單元格 |

## 💻 Code Snippet

```html
<!-- 專業圖片寫法：包含有意義的 alt -->
<img src="images/profile.jpg" alt="開發者本人在辦公室工作的照片" width="300" height="200">

<!-- 語義化表格 -->
<table border="1">
    <thead>
        <tr><th>站點</th><th>車輛數</th><th>狀態</th></tr>
    </thead>
    <tbody>
        <tr><td>台北車站</td><td>12</td><td>正常</td></tr>
    </tbody>
</table>
```

## ⚠️ 避坑對比 (❌ vs ✅)

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| `img` 沒寫 `alt` | 必須寫有意義的 `alt` 描述 |
| 表格全用 `<td>` | 標題行用 `<th>`，包裹在 `<thead>` 中 |
| 音影元素沒 `controls` | 加上 `controls` 讓使用者可暫停/調音量 |
| 圖片路徑錯誤沒 fallback | `` 內加 fallback 文字或錯誤處理 |

## 🔗 關聯連結

- [[語義化 HTML]]：語義化標籤與結構
- [[A11y 無障礙與 SEO]]：無障礙設計與搜尋優化

## 🏷️ 標籤

#HTML #圖片 #影片 #音訊 #表格 #A11y
