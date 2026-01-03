# 穿搭頁面建立指南

本文件說明如何為 DIDI DADA 超級商城建立專屬穿搭頁面。

## 📋 頁面結構

### 紅白撞色羅紋毛衣穿搭頁面

**檔案名稱**：`outfit-red-sweater.html`

**頁面 URL**：`https://www.DidiDadaSuper.com/outfit-red-sweater.html`

---

## 🎨 頁面區塊

### 1. 導航列
- 品牌 Logo（連結至首頁）
- 導航連結：首頁、A 類、B 類、C 類

### 2. 頁面標題區
- 分類標籤（A 類 - 穿搭）
- 穿搭名稱（紅白撞色羅紋毛衣穿搭）
- 簡短描述（適合場合、風格特色）

### 3. 完整穿搭展示區
**左側：完整穿搭圖**
- 圖片：`assets/images/outfits/full_outfit.png`
- 尺寸：最大 500px 寬度
- 樣式：圓角、陰影

**右側：影片展示**
- 影片：`assets/videos/red_sweater_outfit.mp4`
- 控制項：播放、暫停、音量、全螢幕
- 穿搭亮點列表（5-6 個重點）

### 4. 穿搭單品推薦區
**5 個單品卡片**：
1. 紅白撞色羅紋毛衣
2. 藍色直筒牛仔褲
3. 紅色復古帆布鞋
4. 紅色菱格紋鏈條包
5. 幾何造型耳環

**每個卡片包含**：
- 商品圖片
- 分類標籤
- 商品名稱
- 價格（待更新）
- 詳細描述（特色、材質、尺寸、適合場合）
- 購買連結（Shopee/Amazon）

### 5. 搭配建議區
**6 個建議卡片**：
1. 🎨 色彩搭配
2. 👗 版型選擇
3. ✨ 配件點綴
4. 🌟 場合適配
5. ❄️ 季節調整
6. 💡 穿搭技巧

**每個卡片包含**：
- 標題（emoji + 主題）
- 詳細建議文字
- 實用技巧

### 6. 相關穿搭推薦區
**3 個相關穿搭卡片**：
- 運動風穿搭
- 日常穿搭
- 通勤穿搭

**連結至**：首頁「最新穿著」區塊

### 7. 頁尾
- 導航連結
- 版權資訊
- 聯盟行銷聲明

---

## 📂 資源檔案結構

```
DidiDadaSuper/
├── outfit-red-sweater.html          # 穿搭頁面
├── assets/
│   ├── images/
│   │   └── outfits/                 # 穿搭圖片目錄
│   │       ├── full_outfit.png      # 完整穿搭圖
│   │       ├── red_sweater.png      # 毛衣單品圖
│   │       ├── jeans.png            # 牛仔褲單品圖
│   │       ├── red_shoes.png        # 鞋子單品圖
│   │       ├── red_bag.png          # 包包單品圖
│   │       └── earrings.png         # 耳環單品圖
│   └── videos/
│       └── red_sweater_outfit.mp4   # 穿搭影片
```

---

## 🔗 頁面連結整合

### 首頁整合

**位置**：`index.html` → 最新穿著區塊 → 第一個卡片

**修改內容**：
```html
<!-- 穿著 1：紅白撞色羅紋毛衣穿搭 -->
<div class="item-card">
  <img src="assets/images/outfits/full_outfit.png" alt="紅白撞色羅紋毛衣穿搭" class="item-card-image">
  <div class="item-card-content">
    <div>
      <span class="item-card-category">A類 - 穿搭</span>
      <h3 class="item-card-title">紅白撞色羅紋毛衣穿搭</h3>
      <p class="item-card-description">現代感十足的撞色設計，搭配經典牛仔褲與復古帆布鞋。適合約會、逛街、咖啡廳聚會。</p>
    </div>
    <a href="outfit-red-sweater.html" class="item-card-link">查看完整穿搭</a>
  </div>
</div>
```

### A 類分類頁整合

**位置**：`a.html` → 最新穿著區塊

**建議**：添加相同的卡片結構，連結至 `outfit-red-sweater.html`

---

## 🎯 建立新穿搭頁面步驟

### 步驟 1：準備資源

1. **收集圖片**
   - 完整穿搭圖（1 張）
   - 單品圖片（5-8 張）
   - 建議尺寸：300x200px 或更高

2. **準備影片**（可選）
   - 穿搭展示影片
   - 格式：MP4
   - 時長：30 秒 - 2 分鐘

3. **複製資源到網站目錄**
   ```bash
   cp outfit_images/*.png /home/ubuntu/DidiDadaSuper/assets/images/outfits/
   cp outfit_video.mp4 /home/ubuntu/DidiDadaSuper/assets/videos/
   ```

### 步驟 2：複製頁面模板

```bash
cd /home/ubuntu/DidiDadaSuper
cp outfit-red-sweater.html outfit-new-style.html
```

### 步驟 3：修改頁面內容

**需要修改的部分**：

1. **頁面標題**
   ```html
   <title>新穿搭名稱 | DIDI DADA 超級商城</title>
   ```

2. **頁面描述**
   ```html
   <meta name="description" content="新穿搭描述">
   ```

3. **穿搭名稱與描述**
   - 修改 `<h1>` 標籤內容
   - 修改簡短描述段落

4. **圖片路徑**
   - 更新完整穿搭圖路徑
   - 更新單品圖片路徑

5. **影片路徑**（如有）
   ```html
   <source src="assets/videos/new_outfit.mp4" type="video/mp4">
   ```

6. **單品詳情**
   - 修改商品名稱
   - 修改商品描述
   - 更新價格
   - 更新購買連結

7. **搭配建議**
   - 根據新穿搭調整建議內容

### 步驟 4：整合到首頁

**修改 `index.html`**：

在「最新穿著」區塊添加新卡片：

```html
<div class="item-card">
  <img src="assets/images/outfits/new_outfit.png" alt="新穿搭名稱" class="item-card-image">
  <div class="item-card-content">
    <div>
      <span class="item-card-category">A類 - 穿搭</span>
      <h3 class="item-card-title">新穿搭名稱</h3>
      <p class="item-card-description">簡短描述...</p>
    </div>
    <a href="outfit-new-style.html" class="item-card-link">查看完整穿搭</a>
  </div>
</div>
```

### 步驟 5：測試頁面

```bash
cd /home/ubuntu/DidiDadaSuper
python3 -m http.server 8000
# 訪問 http://localhost:8000/outfit-new-style.html
```

**檢查項目**：
- [ ] 頁面正常載入
- [ ] 所有圖片正常顯示
- [ ] 影片可正常播放
- [ ] 所有連結可正常點擊
- [ ] 響應式設計正常運作
- [ ] 導航列連結正確

### 步驟 6：部署上線

```bash
cd /home/ubuntu/DidiDadaSuper
git add .
git commit -m "新增穿搭頁面：新穿搭名稱"
git push origin main
```

---

## 📊 頁面效能優化

### 圖片優化

1. **壓縮圖片**
   ```bash
   # 使用 ImageMagick 壓縮
   convert input.png -quality 85 -resize 800x output.png
   ```

2. **轉換為 WebP 格式**
   ```bash
   cwebp input.png -q 85 -o output.webp
   ```

3. **使用響應式圖片**
   ```html
   <picture>
     <source srcset="image.webp" type="image/webp">
     <img src="image.png" alt="描述">
   </picture>
   ```

### 影片優化

1. **壓縮影片**
   ```bash
   ffmpeg -i input.mp4 -vcodec h264 -acodec aac -b:v 1M output.mp4
   ```

2. **生成縮圖**
   ```bash
   ffmpeg -i video.mp4 -ss 00:00:01 -vframes 1 thumbnail.png
   ```

3. **使用 poster 屬性**
   ```html
   <video poster="thumbnail.png" controls>
     <source src="video.mp4" type="video/mp4">
   </video>
   ```

---

## 🎨 樣式自訂

### 修改分類顏色

**位置**：`assets/css/style.css`

```css
/* A 類 - 粉紅色 */
.item-card-category {
  background-color: var(--color-pink);
}

/* B 類 - 青綠色 */
.cat-b .item-card-category {
  background-color: var(--color-teal);
}

/* C 類 - 紫色 */
.cat-c .item-card-category {
  background-color: var(--color-purple);
}
```

### 調整卡片布局

```css
/* 桌面：4 欄 */
.items-grid {
  grid-template-columns: repeat(4, 1fr);
}

/* 平板：2 欄 */
@media (max-width: 768px) {
  .items-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* 手機：1 欄 */
@media (max-width: 480px) {
  .items-grid {
    grid-template-columns: 1fr;
  }
}
```

---

## 📝 內容撰寫建議

### 穿搭名稱

**格式**：`[主要單品] + [風格/場合] + 穿搭`

**範例**：
- 紅白撞色羅紋毛衣穿搭
- 清爽運動風穿搭
- 專業通勤穿搭
- 海灘度假穿搭

### 簡短描述

**長度**：50-100 字

**內容**：
- 風格特色
- 適合場合
- 穿搭亮點

**範例**：
> 現代感十足的撞色設計，搭配經典牛仔褲與復古帆布鞋，打造時尚又舒適的日常穿搭。適合約會、逛街、咖啡廳聚會等各種場合。

### 單品描述

**結構**：
1. **特色**：設計亮點、材質、版型
2. **材質**：面料成分
3. **尺寸**：可選尺寸
4. **適合場合**：使用情境

**範例**：
> **特色**：獨特的紅白撞色設計，羅紋針織材質柔軟保暖。寬鬆版型適合各種身材，圓領設計修飾臉型。白色縫線裝飾增添設計感。  
> **材質**：羊毛混紡  
> **尺寸**：均碼（適合 S-L）  
> **適合場合**：日常、約會、咖啡廳、逛街

### 搭配建議

**類型**：
1. 色彩搭配
2. 版型選擇
3. 配件點綴
4. 場合適配
5. 季節調整
6. 穿搭技巧

**撰寫技巧**：
- 具體實用
- 避免空泛
- 提供多種選擇
- 考慮不同身材

---

## 🔄 維護與更新

### 定期檢查

- [ ] 所有圖片正常顯示
- [ ] 影片可正常播放
- [ ] 購買連結有效
- [ ] 價格資訊最新
- [ ] 商品庫存充足

### 內容更新

**更新頻率**：每月 1-2 次

**更新內容**：
- 新增當季穿搭
- 更新商品價格
- 替換售罄商品
- 調整搭配建議

### SEO 優化

1. **頁面標題**
   - 包含關鍵字
   - 長度 50-60 字元

2. **Meta 描述**
   - 吸引點擊
   - 長度 150-160 字元

3. **圖片 Alt 文字**
   - 描述性文字
   - 包含關鍵字

4. **內部連結**
   - 連結至相關穿搭
   - 連結至商品分類頁

---

## 📊 數據追蹤

### Google Analytics

**追蹤指標**：
- 頁面瀏覽量
- 平均停留時間
- 跳出率
- 轉化率（點擊購買連結）

### 熱力圖分析

**工具**：Hotjar、Crazy Egg

**分析重點**：
- 用戶滾動深度
- 點擊熱區
- 影片觀看率
- 購買連結點擊率

---

**維護者**：DIDI DADA 團隊  
**最後更新**：2025 年 1 月  
**版本**：v6.0
