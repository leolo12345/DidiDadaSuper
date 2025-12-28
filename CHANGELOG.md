# DIDI DADA 超級商城 - 更新日誌

## v2.0 (2025-01-01)

### 新增功能

**Hero Section 背景圖片**
- 首頁添加全寬 Hero Section，展示「簡約穿搭」主題
- 彩色漸層背景（粉紅→青綠→紫色），融合三大分類色彩
- 浮動裝飾元素（口紅、手機、筆電、購物袋、星星、愛心）
- 時尚模特兒展示簡約穿搭風格

**分類專頁 Hero Section**
- A 類（美妝保養｜穿搭｜減肥）：粉紅色調平鋪攝影背景
- B 類（3C小物｜居家｜露營）：青綠色調科技生活背景
- C 類（線上課程｜軟體｜旅遊）：紫色調學習旅遊背景
- 所有分類專頁替換原有 Banner 為 Hero Section

### 視覺優化

**響應式設計**
- 桌面版：Hero Section 高度 500px（首頁）/ 400px（分類專頁）
- 平板版：Hero Section 高度 350px / 300px
- 手機版：Hero Section 高度 250px / 200px
- 文字大小自動適配不同螢幕尺寸

**樣式改進**
- Hero Section 添加漸層遮罩，提升文字可讀性
- 標題與副標題添加陰影效果
- 分類專頁標題文字改為白色，與背景形成對比

### 技術改進

**CSS 結構**
- 新增 `.hero-section` 樣式類別
- 新增 `.hero-content` 內容容器
- 新增 `.hero-title` 和 `.hero-subtitle` 文字樣式
- 優化響應式斷點設計

**HTML 結構**
- 首頁添加 Hero Section（`<section class="hero-section hero-home">`）
- 分類專頁移除舊版 `<img>` Banner
- 分類專頁添加 Hero Section（`hero-cat-a`、`hero-cat-b`、`hero-cat-c`）

### 檔案變更

**新增檔案**
- `assets/images/hero_home.jpg` - 首頁背景圖片（彩色版本）
- `assets/images/hero_cat_a.jpg` - A 類分類背景圖片
- `assets/images/hero_cat_b.jpg` - B 類分類背景圖片
- `assets/images/hero_cat_c.jpg` - C 類分類背景圖片
- `CHANGELOG.md` - 本檔案

**修改檔案**
- `assets/css/style.css` - 添加 Hero Section 樣式
- `index.html` - 添加首頁 Hero Section
- `a.html` - 替換 Banner 為 Hero Section
- `b.html` - 替換 Banner 為 Hero Section
- `c.html` - 替換 Banner 為 Hero Section

### 效能影響

**檔案大小**
- 首頁背景圖片：5.2 MB
- A 類背景圖片：5.9 MB
- B 類背景圖片：5.4 MB
- C 類背景圖片：5.5 MB
- 總計新增圖片：約 22 MB

**建議優化**
- 考慮使用 WebP 格式減少檔案大小
- 實現圖片懶加載提升首屏載入速度
- 使用 CDN 加速圖片載入

---

## v1.0 (2025-01-01)

### 初始版本

**核心功能**
- 首頁與三個分類專頁（A、B、C 類）
- 響應式設計（桌面、平板、手機）
- 卡片式布局
- 三色系統（粉紅、青綠、紫色）
- 聯盟行銷連結整合

**頁面結構**
- 固定頁頭導航
- 分類卡片區塊
- 最新項目展示
- 最新穿著展示
- 頁尾導航與版權資訊

**技術特性**
- 純 HTML/CSS 靜態網站
- 無外部依賴
- GitHub Pages 部署支援
- SEO 優化

---

**維護者**：DIDI DADA 團隊  
**最後更新**：2025 年 1 月
