# 聯盟連結更新指南

本文件說明如何更新 A 類分類專頁（a.html）的聯盟行銷連結。

## 📋 商品清單與連結位置

### 美妝保養類（Amazon Associate）

| 序號 | 商品名稱 | 價格 | 平台 | 連結位置 |
|------|---------|------|------|---------|
| 1 | BIODANCE Bio-Collagen Real Deep Mask | $19.00 | Amazon | a.html 第 65 行 |
| 2 | Dr.Althea 345 Relief Cream | $26.50 | Amazon | a.html 第 78 行 |
| 3 | medicube Toner Pads Zero Pore | $28.24 | Amazon | a.html 第 91 行 |
| 4 | Anua 3-Step Glass Skin Set | $45.00 | Amazon | a.html 第 104 行 |
| 10 | eos Shea Better Body Lotion | $9.97 | Amazon | a.html 第 169 行 |
| 11 | CeraVe Skin Renewing Night Cream | $15.44 | Amazon | a.html 第 182 行 |
| 12 | e.l.f. SKIN Holy Hydration Kit | $21.00 | Amazon | a.html 第 195 行 |

### 穿搭類（Shopee Affiliate）

| 序號 | 商品名稱 | 價格 | 平台 | 連結位置 |
|------|---------|------|------|---------|
| 5 | NIKE AIR FORCE 1 07 男女款運動休閒鞋 | $2,520 | Shopee | a.html 第 117 行 |
| 6 | 比奇堡居民搞怪中筒襪 | $317 | Shopee | a.html 第 130 行 |

### 減肥類（Amazon Associate）

| 序號 | 商品名稱 | 價格 | 平台 | 連結位置 |
|------|---------|------|------|---------|
| 7 | Orgain Organic Nutritional Protein Shake | $48.00 | Amazon | a.html 第 143 行 |
| 8 | SlimFast Meal Replacement Powder | $12.82 | Amazon | a.html 第 156 行 |
| 9 | Glucerna Diabetes Care Shake | $44.96 | Amazon | a.html 第 169 行 |

---

## 🔧 更新步驟

### 方法 1：手動更新（推薦新手）

1. **開啟檔案**
   ```bash
   # 使用文字編輯器開啟 a.html
   nano /home/ubuntu/DidiDadaSuper/a.html
   # 或使用 VS Code、Sublime Text 等編輯器
   ```

2. **搜尋連結位置**
   - 使用 `Ctrl+F` 搜尋商品名稱（例如：`BIODANCE`）
   - 找到對應的 `<a href="#"` 標籤

3. **替換連結**
   ```html
   <!-- 原始碼 -->
   <a href="#" target="_blank" class="item-card-link" data-platform="Amazon">在 Amazon 查看</a>
   
   <!-- 更新後 -->
   <a href="https://amzn.to/YOUR_AFFILIATE_LINK" target="_blank" class="item-card-link" data-platform="Amazon">在 Amazon 查看</a>
   ```

4. **儲存檔案**
   - Nano：`Ctrl+O` → `Enter` → `Ctrl+X`
   - VS Code：`Ctrl+S`

### 方法 2：批次更新（推薦進階使用者）

建立 JSON 檔案儲存所有連結：

```json
{
  "products": [
    {
      "id": 1,
      "name": "BIODANCE Bio-Collagen Real Deep Mask",
      "platform": "Amazon",
      "link": "https://amzn.to/YOUR_LINK_1"
    },
    {
      "id": 2,
      "name": "Dr.Althea 345 Relief Cream",
      "platform": "Amazon",
      "link": "https://amzn.to/YOUR_LINK_2"
    }
  ]
}
```

使用 Python 腳本批次替換：

```python
import json
import re

# 讀取連結資料
with open('affiliate_links.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# 讀取 HTML 檔案
with open('a.html', 'r', encoding='utf-8') as f:
    html = f.read()

# 批次替換連結
for product in data['products']:
    # 搜尋商品名稱並替換連結
    pattern = f'(<h3 class="item-card-title">{product["name"]}</h3>.*?<a href=")#(")'
    replacement = f'\\1{product["link"]}\\2'
    html = re.sub(pattern, replacement, html, flags=re.DOTALL)

# 儲存更新後的檔案
with open('a.html', 'w', encoding='utf-8') as f:
    f.write(html)

print("✓ 連結更新完成")
```

### 方法 3：使用 n8n 自動化（推薦長期維護）

建立 n8n 工作流程：

1. **觸發器**：定期執行（每週一次）
2. **HTTP Request**：從 Google Sheets 或 Notion 讀取最新連結
3. **Code Node**：批次替換 HTML 連結
4. **Git Push**：自動推送至 GitHub 倉庫
5. **通知**：發送更新完成通知

---

## 🔍 連結格式說明

### Amazon Associate 連結格式

```
https://amzn.to/XXXXXXX
或
https://www.amazon.com/dp/PRODUCT_ID?tag=YOUR_ASSOCIATE_TAG
```

**獲取方式**：
1. 登入 [Amazon Associates](https://affiliate-program.amazon.com/)
2. 搜尋商品
3. 點擊「Get Link」
4. 複製短連結（推薦）或完整連結

### Shopee Affiliate 連結格式

```
https://shope.ee/XXXXXXX
或
https://shopee.tw/product/SHOP_ID/PRODUCT_ID?af_siteid=YOUR_SITE_ID
```

**獲取方式**：
1. 登入 [Shopee Affiliate](https://affiliate.shopee.tw/)
2. 搜尋商品
3. 點擊「生成連結」
4. 複製推廣連結

### Affiliate One 連結格式

```
https://www.affiliateone.com.tw/redirect.php?k=XXXXXXX
```

**獲取方式**：
1. 登入 [Affiliate One](https://www.affiliateone.com.tw/)
2. 搜尋商品
3. 複製推廣連結

---

## ✅ 更新檢查清單

更新連結後，請確認以下事項：

- [ ] 所有連結已替換為實際聯盟連結
- [ ] 連結格式正確（包含聯盟標籤）
- [ ] 連結可正常開啟（測試每個連結）
- [ ] `target="_blank"` 屬性存在（新分頁開啟）
- [ ] `data-platform` 屬性正確（用於追蹤）
- [ ] 商品資訊與連結對應正確
- [ ] 價格資訊已更新為最新價格
- [ ] 推送至 GitHub 並部署至 GitHub Pages

---

## 📊 追蹤與優化

### 建議追蹤指標

1. **點擊率（CTR）**：使用 Google Analytics 追蹤連結點擊
2. **轉化率**：各平台後台查看實際購買數
3. **收益**：定期檢查聯盟行銷收入
4. **熱門商品**：分析哪些商品點擊率最高

### 優化建議

- 每月更新一次商品清單（替換低銷量商品）
- 根據季節調整推薦商品（例如夏季推防曬、冬季推保濕）
- A/B 測試不同商品描述與圖片
- 定期檢查連結有效性（避免失效連結）

---

## 🆘 常見問題

**Q1：連結更新後沒有顯示怎麼辦？**
- 檢查瀏覽器快取，嘗試硬重新整理（Ctrl+Shift+R）
- 確認 GitHub Pages 已重新部署（通常需要 1-5 分鐘）

**Q2：如何確認連結是否包含聯盟標籤？**
- Amazon：連結中應包含 `tag=YOUR_TAG`
- Shopee：連結中應包含 `af_siteid=YOUR_ID`

**Q3：可以混用不同平台的連結嗎？**
- 可以，本網站支援 Amazon、Shopee、Affiliate One 三個平台
- 建議在商品描述中註明平台，方便用戶選擇

**Q4：如何批次更新所有頁面的連結？**
- 使用方法 2 或方法 3 的自動化腳本
- 或使用 VS Code 的「在檔案中尋找並取代」功能

---

**維護者**：DIDI DADA 團隊  
**最後更新**：2025 年 1 月  
**聯絡方式**：透過 GitHub Issues 或專案討論區
