---
title: 我找不到 Pocket 的 Chrome 擴充功能，卻意外發現了更簡單的替代方案
date: 2025-04-30 16:54:35
tags:
  - Pocket
  - Chrome
  - 擴充功能
  - 替代方案
categories:
  - 工具心得
---

我原本只是想要一個快速儲存網頁到 Pocket 的方式，但當我在 Chrome 擴充功能商店搜尋時，卻發現居然沒有官方的「Save to Pocket」擴充工具（或它已經下架了）。這讓我開始尋找替代方案。

我發現一個更簡潔、原生、不佔資源的方法：**使用書籤列上的 JavaScript 程式碼（bookmarklet）**。這段小小的程式碼放在書籤列上，點一下就能把當前網頁直接存入 Pocket，完全不需要安裝任何擴充功能。

## 最簡單的 Pocket 書籤碼（Bookmarklet）

```javascript
javascript:(function(){
  var url = encodeURIComponent(window.location.href);
  var pocketUrl = 'https://getpocket.com/save?url=' + url;
  location.href = pocketUrl; // 若想在同一分頁中開啟
})();
```

這段程式碼做了什麼：
1. 把當前網頁網址抓出來。
2. 編碼成安全的 URL 格式。
3. 導向到 Pocket 的儲存連結（在目前頁面中）。

## 使用方式

### 步驟

1. 將上方程式碼複製。
2. 在 Chrome 書籤列上新增一個書籤。
3. 將「網址」欄位貼上這段 `javascript:` 程式。
4. 命名為「儲存到 Pocket」或任何你喜歡的名稱。

現在只要你在瀏覽任何文章或網站，只要點一下這個書籤，就會自動跳轉到 Pocket 並完成儲存。

## 為什麼我反而喜歡這個方法？

### 重點

* 沒有背景常駐的擴充功能，更輕量
* 不需要登入第三方擴充工具
* 所有動作都在 Pocket 官方網頁內完成
* 不會產生額外資源消耗或追蹤

這種方式看似原始，但卻更穩定、更簡單、更透明，也不容易被瀏覽器政策或安全限制阻擋。

如果你也曾因為找不到擴充功能而苦惱，不妨嘗試這種方式。簡單一行程式碼，直接讓你的書籤列變成 Pocket 儲存神器。