---
id: moc-04
module: cross
title: 版面佈局與響應式設計
status: published
tags: ["#MOC", "#Layout", "#RWD", "#Flexbox", "#Grid", "#響應式""]
summary: 跨 CSS 的版面佈局與響應式設計，含 Flexbox、Grid、Media Query、Mobile-First 與自適應列數。
last_updated: 2026-11-24
---

# 版面佈局與響應式設計 (Map of Content)

## 📋 模組索引

| 模組 | 相關卡片 | 狀態 |
|------|---------|------|
| CSS | [[css-selectors-and-specificity]] | published |
| CSS | [[css-box-model-and-units]] | published |
| CSS | [[css-positioning-and-zindex]] | published |
| CSS | [[css-flexbox-layout]] | published |
| CSS | [[css-grid-layout]] | published |
| CSS | [[css-responsive-design]] | published |

## 🧩 概念交叉索引

| 概念 | 涉及卡片 | 說明 |
|------|---------|------|
| 一維佈局 | [[css-flexbox-layout]] | 適合單一方向對齊 (水平或垂直) |
| 二維佈局 | [[css-grid-layout]] | 同時控制行與列，適合作品集牆 |
| 絕對定位 | [[css-positioning-and-zindex]] | 卡片標籤、固定導航欄 |
| 盒模型 | [[css-box-model-and-units]] | 所有佈局的基礎，`border-box` 專業標準 |
| 響應式斷點 | [[css-responsive-design]] | `@media (min-width: ...)` Mobile-First |
| 流體字體 | [[css-responsive-design]] | `clamp()` 跨裝置平滑縮放 |

## ❌ vs ✅ 避坑速查

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 用 Flexbox 強行做每行 3 卡 | 用 Grid `repeat(auto-fill, minmax(250px, 1fr))` |
| 為每個斷點寫 Media Query | 用 `auto-fill` 自動適應螢幕寬度，無需 Media Query |
| 垂直居中用大量 `padding` 猜測 | 用 `display: flex; align-items: center` |
| 固定寬度 `1200px` 佈局 | 用 `width: 90%; max-width: 1200px` 流體寬度 |
| 字體固定 `24px` | 用 `clamp(1.5rem, 5vw, 3rem)` 流體縮放 |
| 忽略 `100vh` 手機問題 | 改用 `100dvh` 動態視口高度 |

## 🔗 相關 MOC

- [[moc-a11y-and-seo]]
- [[moc-frontend-pitfalls]]
- [[moc-browser-rendering-and-perf]]
