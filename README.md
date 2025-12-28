# DIDI DADA 超級商城 - 靜態網站

## 專案概述

DIDI DADA 超級商城是一個現代化的靜態網站，展示三大產品分類：

- **A 類**：美妝保養｜穿搭｜減肥（粉紅色調）
- **B 類**：3C小物｜居家｜露營（青綠色調）
- **C 類**：線上課程｜軟體｜旅遊（紫色調）

## 網站結構

```
DidiDadaSuper/
├── index.html              # 首頁
├── a.html                  # A 類分類專頁
├── b.html                  # B 類分類專頁
├── c.html                  # C 類分類專頁
├── assets/
│   ├── css/
│   │   └── style.css       # 共用樣式表（響應式設計）
│   └── images/
│       ├── logo.png        # DIDI DADA 品牌 Logo
│       ├── cat_a_banner.jpg # A 類 Banner 圖片
│       ├── cat_b_banner.jpg # B 類 Banner 圖片
│       └── cat_c_banner.jpg # C 類 Banner 圖片
└── README.md               # 本檔案
```

## 技術特性

### 響應式設計
- **桌面版**（1200px 以上）：3 欄網格布局
- **平板版**（768px - 1199px）：2 欄網格布局
- **手機版**（480px 以下）：1 欄單列布局

### 設計元素
- **卡片式布局**：圓角卡片（12px）+ 輕微陰影
- **色彩系統**：
  - A 類：粉紅色（#FF6B9D）
  - B 類：青綠色（#4ECDC4）
  - C 類：紫色（#9B59B6）
- **字體**：系統預設字體（-apple-system, BlinkMacSystemFont, 'Segoe UI'）

### 功能特性
- 全站導航（固定頁頭）
- 分類卡片快速導航
- 最新項目展示區
- 最新穿著展示區
- 聯盟行銷連結整合（Shopee、Amazon、自訂連結）
- 頁尾導航與版權資訊

## 部署指南

### 方案 1：GitHub Pages（推薦）

1. **建立 GitHub 倉庫**
   ```bash
   # 在 GitHub 上建立新倉庫，命名為 DidiDadaSuper
   ```

2. **初始化 Git 並推送**
   ```bash
   cd /home/ubuntu/DidiDadaSuper
   git init
   git add .
   git commit -m "Initial commit: DIDI DADA 超級商城"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/DidiDadaSuper.git
   git push -u origin main
   ```

3. **啟用 GitHub Pages**
   - 進入倉庫設定（Settings）
   - 找到 "Pages" 選項
   - 選擇 "Deploy from a branch"
   - 分支選擇 `main`，目錄選擇 `/ (root)`
   - 儲存設定

4. **配置自訂域名**
   - 在倉庫根目錄建立 `CNAME` 檔案
   - 檔案內容：`www.DidiDadaSuper.com`
   - 在域名提供商設定 DNS 記錄指向 GitHub Pages

### 方案 2：自架伺服器

1. **使用 Python HTTP 伺服器**
   ```bash
   cd /home/ubuntu/DidiDadaSuper
   python3 -m http.server 8000
   ```
   訪問：`http://localhost:8000`

2. **使用 Node.js HTTP 伺服器**
   ```bash
   npm install -g http-server
   cd /home/ubuntu/DidiDadaSuper
   http-server -p 8000
   ```

3. **使用 Nginx**
   ```nginx
   server {
       listen 80;
       server_name www.DidiDadaSuper.com;
       root /home/ubuntu/DidiDadaSuper;
       index index.html;
   }
   ```

### 方案 3：Netlify / Vercel

1. 將專案推送至 GitHub
2. 在 Netlify/Vercel 連接 GitHub 倉庫
3. 設定部署分支為 `main`
4. 自動部署完成

## 內容更新指南

### 更新最新項目

編輯 `index.html` 中的「最新項目」區塊：

```html
<div class="item-card">
  <img src="https://via.placeholder.com/300x200?text=產品名稱" alt="產品名稱" class="item-card-image">
  <div class="item-card-content">
    <div>
      <span class="item-card-category">分類名稱</span>
      <h3 class="item-card-title">產品標題</h3>
      <p class="item-card-description">產品描述文案</p>
    </div>
    <a href="https://affiliate-link.com" target="_blank" class="item-card-link">在平台查看</a>
  </div>
</div>
```

### 更新最新穿著

編輯 `index.html` 中的「最新穿著」區塊，方法同上。

### 更新分類專頁

編輯對應的 `a.html`、`b.html` 或 `c.html` 檔案，使用相同的卡片結構。

### 自動化更新（使用 n8n）

可配合 n8n 自動化工具，定期更新最新項目與穿著區塊：

1. 在 n8n 中建立工作流程
2. 使用 HTTP 請求節點獲取最新內容
3. 使用正則表達式或 HTML 解析器提取資訊
4. 使用 Git 節點自動提交並推送更新
5. 設定定時觸發器（例如每週更新）

## 聯盟行銷連結管理

### 支援的平台

- **Shopee Affiliate**：`https://shopee.tw` 或 `https://shopee.com`
- **Amazon Associate**：`https://amazon.com` 或 `https://amazon.tw`
- **Affiliate One**：自訂連結
- **其他平台**：自訂連結

### 推薦最佳實踐

1. **誠實推薦**：優先考慮用戶需求，而非佣金
2. **自然嵌入**：將聯盟連結自然融入內容，避免強迫推銷
3. **透明揭露**：在頁尾說明推薦來源
4. **定期審核**：檢查連結有效性，移除過時產品

## SEO 優化建議

1. **Meta 標籤**：已在各頁面設定 title 和 description
2. **結構化資料**：可考慮添加 Schema.org 標記
3. **圖片優化**：使用適當的 alt 文本和圖片壓縮
4. **內部連結**：已設定完整的導航結構
5. **行動優化**：已實現完整的響應式設計

## 瀏覽器相容性

- Chrome/Edge：完全相容
- Firefox：完全相容
- Safari：完全相容
- IE 11：不支援（使用現代 CSS）

## 效能優化建議

1. **圖片優化**
   - 使用 WebP 格式減少檔案大小
   - 實現圖片懶加載

2. **CSS 優化**
   - 考慮使用 CSS 預處理器（SASS/LESS）
   - 最小化 CSS 檔案

3. **JavaScript**
   - 目前不需要 JavaScript，保持輕量
   - 如需互動功能，使用原生 JS 或輕量框架

## 常見問題

### Q：如何修改分類色彩？
A：編輯 `assets/css/style.css` 中的 `:root` 部分：
```css
:root {
  --color-pink: #FF6B9D;      /* 修改 A 類色彩 */
  --color-teal: #4ECDC4;      /* 修改 B 類色彩 */
  --color-purple: #9B59B6;    /* 修改 C 類色彩 */
}
```

### Q：如何添加新的分類？
A：複製現有的分類頁面（如 `a.html`），修改內容後重新命名。

### Q：如何在手機上預覽？
A：使用本地 IP 地址訪問（例如 `http://192.168.1.100:8000`）。

### Q：如何提高網站速度？
A：
- 壓縮圖片
- 使用 CDN 加速
- 啟用瀏覽器快取
- 考慮使用靜態網站生成器（如 Hugo、Jekyll）

## 技術支援

如有問題，請檢查：
1. 檔案路徑是否正確
2. 圖片檔案是否存在
3. 連結是否有效
4. 瀏覽器開發者工具（F12）中的控制台錯誤

## 版本記錄

- **v1.0** (2025-01-01)：初始版本
  - 完成首頁與三個分類專頁
  - 實現響應式設計
  - 整合聯盟行銷連結

## 授權

本專案為 DIDI DADA 超級商城所有。

---

**最後更新**：2025 年 1 月
**維護者**：DIDI DADA 團隊
