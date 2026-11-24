---
id: moc-03
module: cross
title: 瀏覽器渲染與效能優化
status: published
tags:
  - "#MOC"
  - "#Performance"
  - "#渲染"
  - "#EventLoop"
  - "#BoxModel"
  - "#效能"
summary: 跨 CSS/JS 的瀏覽器渲染原理與效能優化，含盒模型、事件循環、clamp 流體字體與 Mobile-First 策略。
last_updated: 2026-11-24
---

# 瀏覽器渲染與效能優化 (Map of Content)

## 📋 模組索引

| 模組 | 相關卡片 | 狀態 |
|------|---------|------|
| CSS | [[css-box-model-and-units]] | published |
| CSS | [[css-responsive-design]] | published |
| JS | [[js-async-and-promises]] | published |
| JS | [[js-engine-and-event-loop]] | published |

## 🧩 概念交叉索引

| 概念 | 涉及模組 | 關鍵卡片 |
|------|---------|---------|
| 盒模型 (Box Model) | CSS | [[css-box-model-and-units]] |
| 事件循環 (Event Loop) | JS | [[js-engine-and-event-loop]] |
| 流體字體 (clamp) | CSS | [[css-responsive-design]] |
| 動態視口 (dvh) | CSS | [[css-box-model-and-units]] |
| 異步非阻塞 | JS | [[js-async-and-promises]] |
| Mobile-First | CSS | [[css-responsive-design]] |

## ❌ vs ✅ 避坑速查

| ❌ 錯誤做法 | ✅ 正確做法 |
|------------|------------|
| 未設 `box-sizing: border-box` → 佈局爆掉 | `* { box-sizing: border-box; }` 全域重設 |
| 手機端用 `100vh` → 地址欄遮擋 | 改用 `100dvh` 動態視口高度 |
| 字體固定 `px` → 無法縮放 | 使用 `rem` 做基礎字體，支援 A11y |
| 主執行緒大量計算 → 瀏覽器卡死 | 用 `setTimeout(..., 0)` 或 Web Workers 拆分任務 |
| 誤以為 `setTimeout(0)` 立即執行 | 它是宏任務，在微任務 (Promise) 之後執行 |
| 字體固定大小 → 跨裝置不友善 | 用 `clamp(1.5rem, 5vw, 3rem)` 流體縮放 |
| 先寫 PC 版再覆蓋手機 | 採用 Mobile-First，從 `min-width` 漸進增強 |

## 🔗 相關 MOC

- [[moc-a11y-and-seo]]
- [[moc-frontend-pitfalls]]
- [[moc-layout-and-rwd]]
