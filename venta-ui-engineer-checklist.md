# Venta 新站 — UI 工程師 SEO/AEO 施工清單

> Mickey 會提供每頁的文案內容，工程師根據此清單把技術面做到位。
> 文案內容 = Mickey 負責｜技術實作 = 工程師負責

---

## 一、每一頁都要做的事（通用）

### HTML head
- [ ] `<title>` 用 Mickey 給的標題，格式 `頁面主題 | GoWarehouse`，不超過 60 字元
- [ ] `<meta name="description">` 用 Mickey 給的描述，不超過 155 字元
- [ ] `<link rel="canonical">` 指向該頁自己的 URL（不要全站指向首頁）
- [ ] `<link rel="alternate" hreflang="...">` 每頁要列出所有語系互指 + `x-default`
  - 目前已列：`zh-TW`（繁中，預設）｜`en`（英文）｜`ja`（日文）｜`vi`（越南文）｜`th`（泰文）｜`es`（西班牙文）
  - `x-default` 指向 `zh-TW` 版本
- [ ] Open Graph 標籤（og:title / og:description / og:image）— 分享到社群時的預覽

### 圖片
- [ ] 全站圖片用 WebP 格式
- [ ] 每張 `<img>` 都要有 `alt` 屬性，用 Mickey 給的描述文字填入
- [ ] 非首屏圖片加 `loading="lazy"`

### 內部連結
- [ ] 每頁至少 2-3 個連結指向站內其他相關頁面（Mickey 會標註哪些頁面要互連）

### CTA 按鈕
- [ ] 每頁至少放一個「預約 Demo」或「免費試用」按鈕，位置由 Mickey 指定

---

## 二、結構化資料 Schema.org（寫在 HTML 裡，消費者看不到）

以下用 `<script type="application/ld+json">` 埋入：

### 全站共用
- [ ] **Organization** — 公司名稱、Logo URL、官網、聯絡電話、社群連結（LINE / FB / LinkedIn）
- [ ] **BreadcrumbList** — 每頁的麵包屑導航路徑

### 首頁
- [ ] **SoftwareApplication** — 產品名 GoWarehouse / Venta、類別 BusinessApplication、價格（Mickey 提供）、作業系統 Cloud/Android

### 功能頁 / 產業頁
- [ ] **FAQPage** — Mickey 會提供每頁底部的 FAQ 問答（問題 + 答案），工程師包成 FAQPage schema
- [ ] **HowTo**（教學類頁面）— Mickey 提供步驟文字，工程師包成 HowTo schema

### 部落格 / 知識庫
- [ ] **Article** — 標題、作者、發布日期、修改日期、描述

### 客戶評價頁（有評價內容後）
- [ ] **AggregateRating** — 總評分、評論數
- [ ] **Review** — 每則評價的作者、評分、內容

---

## 三、技術 SEO 基礎建設

### 多國語系（i18n）
- [ ] 支援多國語系，目前已列：**繁中（zh-TW，預設）／英文（en）／日文（ja）／越南文（vi）／泰文（th）／西班牙文（es）**（後續可再擴充）
- [ ] 語系切換 UI：header 右上角放語系 dropdown，顯示該語言的原文名稱（中文 / English / 日本語 / Tiếng Việt / ภาษาไทย / Español）
- [ ] URL 結構用子路徑：`/zh-TW/` `/en/` `/ja/` `/vi/` `/th/` `/es/`（不要用 query string `?lang=en`）
- [ ] 根網域 `/` 自動依瀏覽器 `Accept-Language` 302 導向對應語系，未命中則預設 `zh-TW`
- [ ] 切換語系時停留在當前頁（例：從 `/zh-TW/pricing` 切到 `/ja/pricing`，不要回首頁）
- [ ] 每個語系版本都要完整翻譯（Mickey 會提供各語系文案 CSV），不要只翻首頁讓內頁留中文
- [ ] 日期 / 數字 / 價格格式依語系 locale 顯示（例：日文用「¥」｜泰文用「฿」｜西文用千分位「.」）

### URL 結構
- [ ] 全小寫、用 `-` 分隔，如 `/features/batch-picking`，不要用 `.html` 結尾
- [ ] 中文頁面也用英文 URL slug（不要 `/功能/波次揀貨`）

### Sitemap & Robots
- [ ] 自動產生 `sitemap.xml`，涵蓋所有公開頁面
- [ ] `robots.txt` 允許爬取公開頁、Disallow 後台與感謝頁、引用 sitemap 路徑

### 301 Redirect（舊站 → 新站）
- [ ] Mickey 會提供舊站 URL 對照表，工程師逐條設定 301 redirect
- [ ] 至少要包含：
  - `gowarehouse.asia/index.html` → 新站首頁
  - `gowarehouse.asia/support.html` → 新站支援頁
  - `gowarehouse.asia/en/support.html` → 新站英文支援頁
  - 其他舊站已索引的 12 頁全部對應

### 效能
- [ ] PageSpeed Insights 分數 ≥ 85（桌機 + 手機都要）
- [ ] LCP < 2.5 秒
- [ ] INP < 200ms
- [ ] CLS < 0.1
- [ ] HTTPS 無 mixed content

### RWD 響應式
- [ ] Google Mobile-Friendly Test 通過
- [ ] 手機版所有 CTA 按鈕可點擊、表單可填寫

---

## 四、上線當天工程師要做

- [ ] 部署 301 redirect 規則，用 `curl -I` 逐條驗證
- [ ] 提交新 sitemap.xml 到 Google Search Console
- [ ] 提交新 sitemap.xml 到 Bing Webmaster Tools
- [ ] 確認 GA4 追蹤碼在每頁都有正常發送（用 GA4 DebugView 驗證）
- [ ] 確認 Schema.org 結構化資料通過 Google Rich Results Test
- [ ] 用 PageSpeed Insights 跑一次全站主要頁面，截圖存檔

---

## 附註：Mickey 會提供什麼給你

| 項目 | 格式 |
|---|---|
| 每頁 title 標題 | 純文字，60 字內 |
| 每頁 meta description | 純文字，155 字內 |
| 每頁 FAQ 問答 | 問題 + 答案，每頁 3-5 組 |
| 圖片 alt 描述 | 每張圖一句話 |
| 頁面互連指示 | 「A 頁連到 B 頁」清單 |
| 舊站 URL 對照表 | 舊 URL → 新 URL |
| 定價資訊 | 方案名稱 + 價格 |
| 多國語系文案 | CSV（key + zh-TW / en / ja / vi / th / es 各欄，可再擴充） |
