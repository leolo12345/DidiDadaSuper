# 響應式設計文檔

本文件說明 DIDI DADA 超級商城的響應式設計系統，以 **1920x1080 (Full HD)** 為預設基準。

## 📐 設計原則

### 核心理念
- **流式布局（Fluid Layout）**：使用百分比與相對單位，而非固定像素
- **彈性網格（Flexible Grid）**：自動調整欄位數量與間距
- **媒體查詢（Media Queries）**：針對不同解析度優化顯示
- **相對字體大小**：使用 `rem`、`em`、`clamp()` 實現動態縮放

### 預設基準
- **目標解析度**：1920x1080 (Full HD)
- **容器最大寬度**：1400px
- **基礎字體大小**：16px（在 1920px 寬度下為 18px）

---

## 🎯 支援的解析度

### 完整斷點系統

| 斷點名稱 | 解析度範圍 | 容器寬度 | Hero 高度 | 字體大小 | 網格欄位 |
|---------|-----------|---------|----------|---------|---------|
| **4K 超高清** | 2560px+ | 1800px | 600px | 18px | 4-5 欄 |
| **Full HD** | 1920px - 2559px | 1400px | 500px | 18px | 3-4 欄 |
| **HD** | 1366px - 1919px | 1200px | 450px | 15px | 3 欄 |
| **筆電** | 1024px - 1365px | 960px | 400px | 14px | 3 欄 |
| **平板** | 768px - 1023px | 100% | 350px | 14px | 2 欄 |
| **大型手機** | 481px - 767px | 100% | 300px | 14px | 2 欄 |
| **手機** | 480px 以下 | 100% | 250px | 14px | 1 欄 |

---

## 🔧 技術實現

### 1. 基礎字體大小動態調整

```css
html {
  font-size: 16px;  /* 預設 */
}

@media (min-width: 1920px) {
  html {
    font-size: 18px;  /* Full HD 及以上 */
  }
}

@media (max-width: 1366px) {
  html {
    font-size: 15px;  /* HD 及以下 */
  }
}

@media (max-width: 1024px) {
  html {
    font-size: 14px;  /* 平板及以下 */
  }
}
```

### 2. 容器寬度自適應

```css
.container {
  max-width: 1400px;  /* 預設 Full HD */
  margin: 0 auto;
  padding: 0 2rem;
  width: 100%;
}

@media (min-width: 2560px) {
  .container {
    max-width: 1800px;  /* 4K */
  }
}

@media (min-width: 1366px) and (max-width: 1919px) {
  .container {
    max-width: 1200px;  /* HD */
  }
}

@media (min-width: 1024px) and (max-width: 1365px) {
  .container {
    max-width: 960px;  /* 筆電 */
  }
}
```

### 3. 動態字體大小（clamp）

```css
h1 {
  font-size: clamp(2rem, 4vw, 2.5rem);
  /* 最小 2rem，理想 4vw，最大 2.5rem */
}

h2 {
  font-size: clamp(1.75rem, 3.5vw, 2rem);
}

h3 {
  font-size: clamp(1.1rem, 2vw, 1.25rem);
}
```

### 4. Hero Section 高度調整

```css
.hero-section {
  height: 500px;  /* 預設 Full HD */
}

@media (min-width: 2560px) {
  .hero-section {
    height: 600px;  /* 4K */
  }
}

@media (min-width: 1366px) and (max-width: 1919px) {
  .hero-section {
    height: 450px;  /* HD */
  }
}

@media (min-width: 1024px) and (max-width: 1365px) {
  .hero-section {
    height: 400px;  /* 筆電 */
  }
}

@media (min-width: 768px) and (max-width: 1023px) {
  .hero-section {
    height: 350px;  /* 平板 */
  }
}

@media (max-width: 767px) {
  .hero-section {
    height: 300px;  /* 手機 */
  }
}
```

### 5. 彈性網格系統

```css
.items-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

@media (min-width: 2560px) {
  .items-grid {
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  }
}

@media (min-width: 1024px) and (max-width: 1365px) {
  .items-grid {
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  }
}

@media (max-width: 767px) {
  .items-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1.25rem;
  }
}

@media (max-width: 480px) {
  .items-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
}
```

---

## 🧪 測試方法

### 1. 使用響應式測試頁面

訪問 `responsive-test.html` 查看即時解析度資訊：

```
http://localhost:8000/responsive-test.html
```

測試頁面顯示：
- 目前視窗寬度與高度
- 螢幕解析度
- 裝置像素比
- 當前斷點
- 容器寬度
- 字體大小

### 2. 瀏覽器開發者工具

**Chrome DevTools**
1. 按 `F12` 開啟開發者工具
2. 點擊「Toggle device toolbar」（`Ctrl+Shift+M`）
3. 選擇預設裝置或自訂解析度
4. 測試以下解析度：
   - 2560x1440 (4K)
   - 1920x1080 (Full HD) ⭐ 預設
   - 1366x768 (HD)
   - 1024x768 (筆電)
   - 768x1024 (平板)
   - 375x667 (手機)

**Firefox Responsive Design Mode**
1. 按 `Ctrl+Shift+M`
2. 選擇裝置或輸入自訂解析度
3. 測試橫向與直向顯示

### 3. 實際裝置測試

建議在以下裝置上測試：
- ✓ 桌面電腦（1920x1080、2560x1440）
- ✓ 筆記型電腦（1366x768、1920x1080）
- ✓ 平板（iPad、Android Tablet）
- ✓ 手機（iPhone、Android）

---

## 📊 效能優化

### 圖片響應式

**使用 `srcset` 提供多解析度圖片**

```html
<img 
  src="image-1920.jpg" 
  srcset="
    image-480.jpg 480w,
    image-768.jpg 768w,
    image-1024.jpg 1024w,
    image-1920.jpg 1920w,
    image-2560.jpg 2560w
  "
  sizes="(max-width: 768px) 100vw, (max-width: 1920px) 80vw, 1400px"
  alt="商品圖片"
>
```

### CSS 優化

**使用 CSS 變數減少重複**

```css
:root {
  --container-max-width: 1400px;
  --hero-height: 500px;
  --grid-gap: 2rem;
}

@media (min-width: 2560px) {
  :root {
    --container-max-width: 1800px;
    --hero-height: 600px;
  }
}
```

### 載入優化

**延遲載入非關鍵 CSS**

```html
<link rel="preload" href="assets/css/style.css" as="style">
<link rel="stylesheet" href="assets/css/style.css">
```

---

## 🔍 常見問題

### Q1：為什麼選擇 1920x1080 作為預設基準？

**A**：根據 2024 年統計，1920x1080 是最常見的桌面解析度（約 22% 市占率），適合作為預設基準。網站在此解析度下顯示效果最佳。

### Q2：如何調整預設基準解析度？

**A**：修改 CSS 中的容器最大寬度與字體大小：

```css
.container {
  max-width: 1400px;  /* 調整此值 */
}

html {
  font-size: 18px;  /* 調整基礎字體大小 */
}
```

### Q3：網站在 4K 螢幕上顯示太小怎麼辦？

**A**：已針對 4K 解析度優化，容器寬度增加至 1800px，字體大小自動放大。如需進一步調整，修改 `@media (min-width: 2560px)` 斷點。

### Q4：手機橫向顯示異常？

**A**：檢查 viewport 設定：

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

確保未禁用縮放功能。

### Q5：如何測試特定解析度？

**A**：使用 `responsive-test.html` 或瀏覽器開發者工具的響應式模式。

---

## 📝 維護指南

### 添加新斷點

1. 在 `style.css` 中添加新的 `@media` 查詢
2. 調整容器寬度、字體大小、網格欄位
3. 在 `responsive-test.html` 中更新斷點列表
4. 測試所有頁面在新斷點下的顯示

### 更新現有斷點

1. 修改對應的 `@media` 查詢
2. 測試相鄰斷點是否受影響
3. 更新本文檔中的斷點表格

### 檢查清單

更新響應式設計後，請確認：
- [ ] 所有解析度下容器寬度正確
- [ ] 字體大小在各斷點下可讀
- [ ] 網格布局不會過於擁擠或稀疏
- [ ] Hero Section 高度適中
- [ ] 圖片不會變形或模糊
- [ ] 導航列在手機上可正常使用
- [ ] 所有互動元素（按鈕、連結）可點擊

---

## 🎨 設計建議

### 最佳實踐

1. **優先行動裝置**：先設計手機版，再擴展至桌面版
2. **觸控友善**：按鈕與連結至少 44x44px
3. **可讀性**：行寬不超過 75 字元
4. **留白**：適當的間距提升可讀性
5. **一致性**：各解析度下保持視覺一致

### 避免的錯誤

- ❌ 使用固定像素寬度
- ❌ 忽略極端解析度（超小或超大）
- ❌ 過度依賴斷點（應使用流式布局）
- ❌ 圖片未優化導致載入緩慢
- ❌ 文字過小或過大

---

**維護者**：DIDI DADA 團隊  
**最後更新**：2025 年 1 月  
**版本**：v4.0
