---
id: moc-01
module: cross
title: A11y 無障礙與 SEO 實務
status: published
tags:
  - "#MOC"
  - "#A11y"
  - "#SEO"
  - "#無障礙"
  - "#語義化"
summary: 跨 HTML/CSS/JS 的無障礙設計與搜尋引擎優化實務，含語義化標籤、alt 文字與 label 綁定。
last_updated: 2026-11-24
---

# A11y 無障礙與 SEO 實務 (Map of Content)

## 📋 模組索引

| 模組 | 相關卡片 | 狀態 |
|------|---------|------|
| HTML | [[html-semantics-and-a11y]] | published |
| HTML | [[html-text-links-and-lists]] | published |
| HTML | [[html-multimedia-and-tables]] | published |
| CSS | [[css-box-model-and-units]] | published |

## 🧩 概念交叉索引

| 概念 | 涉及模組 | 關鍵卡片 |
|------|---------|---------|
| 語義化標籤 | HTML | [[html-semantics-and-a11y]] |
| 圖片替代文字 (alt) | HTML | [[html-multimedia-and-tables]] |
| 輸入框標籤綁定 | HTML | [[html-forms-and-validation]] |
| 頁面語言設定 | HTML | [[html-skeleton-and-encoding]] |
| 字體縮放 (rem) | CSS | [[css-box-model-and-units]] |

## ❌ vs ✅ 避坑速查

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 所有區塊都用 `<div>` (Div Soup) | 使用 `<header>`、`<nav>`、`<main>`、`<footer>` 等語義化標籤 |
| `img` 沒寫 `alt` | 必須寫有意義的 `alt` 描述，讓螢幕閱讀器朗讀 |
| 輸入框只有 `<div>` 標題 | 使用 `<label for="id">` 與 `<input id="id">` 綁定 |
| `lang` 屬性缺失 | `<html lang="zh-Hant">` 讓 Google 與螢幕閱讀器正確識別語言 |
| 字體只用 `px` | 使用 `rem` 支援瀏覽器字體縮放 (A11y) |

## 🔗 相關 MOC

- [[moc-frontend-pitfalls]]
- [[moc-browser-rendering-and-perf]]
- [[moc-layout-and-rwd]]
