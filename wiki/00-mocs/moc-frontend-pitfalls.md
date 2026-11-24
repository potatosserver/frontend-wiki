---
id: moc-02
module: cross
title: 現代前端避坑指南
status: published
tags: ["#MOC", "#Pitfalls", "#避坑", "#Cross-Module""]
summary: 跨 HTML/CSS/JS 的常見錯誤與正確做法對比表，初學者必讀。
last_updated: 2026-11-24
---

# 現代前端避坑指南 (❌ vs ✅)

## 📋 模組索引

| 模組 | 相關卡片 | 狀態 |
|------|---------|------|
| HTML | [[html-skeleton-and-encoding]] | published |
| HTML | [[html-text-links-and-lists]] | published |
| HTML | [[html-semantics-and-a11y]] | published |
| CSS | [[css-selectors-and-specificity]] | published |
| CSS | [[css-box-model-and-units]] | published |
| CSS | [[css-positioning-and-zindex]] | published |
| JS | [[js-basics-and-variables]] | published |
| JS | [[js-operators-and-control-flow]] | published |
| JS | [[js-functions-scope-and-closures]] | published |

## 🧩 概念交叉索引

| 概念 | 涉及模組 | 關鍵卡片 |
|------|---------|---------|
| Quirks Mode | HTML | [[html-skeleton-and-encoding]] |
| 亂碼 (Mojibake) | HTML | [[html-skeleton-and-encoding]] |
| CSS 特異度 | CSS | [[css-selectors-and-specificity]] |
| 盒模型爆掉 | CSS | [[css-box-model-and-units]] |
| z-index 沒效 | CSS | [[css-positioning-and-zindex]] |
| `==` 型別轉換 | JS | [[js-operators-and-control-flow]] |
| 死迴圈 | JS | [[js-operators-and-control-flow]] |

## ❌ vs ✅ 避坑速查

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 缺少 `<!DOCTYPE html>` → 進入 Quirks Mode | 第一行必須寫 `<!DOCTYPE html>` |
| 中文頁面沒 UTF-8 → 亂碼 | `<meta charset="UTF-8">` 放在 `<head>` 第一行 |
| 每頁多個 `<h1>` → SEO 受影響 | 每頁僅限一個 `<h1>`，層級遞減 |
| 用 `==` 比較 → 型別轉換 Bug | 永遠用 `===` 嚴格相等 |
| `z-index: 9999` 沒效 | 檢查元素是否有 `position`，且無層疊上下文限制 |
| `while` 迴圈忘記改變條件 → 瀏覽器卡死 | 確保迴圈內修改條件變數 |
| 手機端用 `100vh` → 地址欄遮擋 | 改用 `100dvh` 動態視口高度 |
| 全部用 `<div>` (Div Soup) | 使用語義化標籤 `<header>` `<main>` `<footer>` 等 |

## 🔗 相關 MOC

- [[moc-a11y-and-seo]]
- [[moc-browser-rendering-and-perf]]
- [[moc-layout-and-rwd]]
