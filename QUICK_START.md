# DIDI DADA 超級商城 - 快速開始指南

## 5 分鐘快速部署

### 步驟 1：準備檔案

所有檔案已準備就緒，位置在 `/home/ubuntu/DidiDadaSuper/`

### 步驟 2：本地測試

```bash
cd /home/ubuntu/DidiDadaSuper
python3 -m http.server 8000
```

然後在瀏覽器中訪問：`http://localhost:8000`

### 步驟 3：部署到 GitHub Pages（推薦）

#### 3.1 建立 GitHub 倉庫

1. 登入 GitHub（https://github.com）
2. 點擊「New repository」
3. 倉庫名稱：`DidiDadaSuper`
4. 選擇「Public」
5. 點擊「Create repository」

#### 3.2 推送程式碼

```bash
cd /home/ubuntu/DidiDadaSuper

# 初始化 Git
git init
git add .
git commit -m "Initial commit: DIDI DADA 超級商城"
git branch -M main

# 連接遠端倉庫（替換 YOUR_USERNAME）
git remote add origin https://github.com/YOUR_USERNAME/DidiDadaSuper.git
git push -u origin main
```

#### 3.3 啟用 GitHub Pages

1. 進入倉庫頁面
2. 點擊「Settings」
3. 左側選擇「Pages」
4. 「Source」選擇「Deploy from a branch」
5. 分支選擇「main」，目錄選擇「/ (root)」
6. 點擊「Save」

**網站將在 `https://YOUR_USERNAME.github.io/DidiDadaSuper/` 上線**

### 步驟 4：配置自訂域名（可選）

#### 4.1 在 GitHub 設定自訂域名

1. 進入倉庫 Settings → Pages
2. 在「Custom domain」欄位輸入：`www.DidiDadaSuper.com`
3. 點擊「Save」
4. GitHub 會自動建立 `CNAME` 檔案

#### 4.2 在域名提供商設定 DNS

根據域名提供商不同，設定方式略有差異。以下以常見的 DNS 設定為例：

**方案 A：使用 CNAME（推薦）**
```
主機名：www
類型：CNAME
值：YOUR_USERNAME.github.io
```

**方案 B：使用 A 記錄**
```
主機名：www
類型：A
值：185.199.108.153
      185.199.109.153
      185.199.110.153
      185.199.111.153
```

等待 DNS 生效（通常 24-48 小時）。

## 內容更新流程

### 更新最新項目

1. 編輯 `index.html` 或分類專頁（`a.html`、`b.html`、`c.html`）
2. 找到「最新項目」區塊
3. 修改或添加卡片內容
4. 保存檔案

### 推送更新到 GitHub

```bash
cd /home/ubuntu/DidiDadaSuper

# 檢查變更
git status

# 添加所有變更
git add .

# 提交變更
git commit -m "更新最新項目和穿著"

# 推送到 GitHub
git push origin main
```

GitHub Pages 會自動部署更新（通常需要 1-2 分鐘）。

## 常見部署問題

### Q：GitHub Pages 無法訪問？
A：
1. 檢查倉庫是否為 Public
2. 確認 Pages 設定已啟用
3. 等待 GitHub 完成部署（檢查 Actions 標籤）
4. 清除瀏覽器快取後重新訪問

### Q：自訂域名無法解析？
A：
1. 確認 DNS 記錄已正確設定
2. 使用 `nslookup` 或 `dig` 命令檢查 DNS：
   ```bash
   nslookup www.DidiDadaSuper.com
   ```
3. DNS 生效需要 24-48 小時
4. 檢查 GitHub 倉庫中的 `CNAME` 檔案是否存在

### Q：圖片無法顯示？
A：
1. 確認圖片檔案在 `assets/images/` 目錄中
2. 檢查 HTML 中的圖片路徑是否正確
3. 確認圖片檔案名稱大小寫正確

### Q：樣式無法載入？
A：
1. 確認 CSS 檔案在 `assets/css/` 目錄中
2. 檢查 HTML 中的 CSS 路徑：`<link rel="stylesheet" href="assets/css/style.css">`
3. 清除瀏覽器快取（Ctrl+Shift+Delete）

## 進階配置

### 使用 n8n 自動化更新

如果你使用 n8n 自動化工具，可以設定定時工作流程：

1. **觸發器**：Schedule（定時觸發，例如每週一次）
2. **資料來源**：HTTP 請求或 API 調用
3. **處理**：提取最新產品資訊
4. **更新**：修改 HTML 檔案中的相應區塊
5. **推送**：使用 Git 命令自動提交並推送到 GitHub

### 使用 Netlify 部署

1. 連接 GitHub 倉庫到 Netlify
2. 設定部署分支為 `main`
3. 自動部署完成
4. 在 Netlify 中設定自訂域名

### 使用 Vercel 部署

1. 連接 GitHub 倉庫到 Vercel
2. 選擇「Other」作為框架
3. 自動部署完成
4. 在 Vercel 中設定自訂域名

## 網站檔案清單

```
DidiDadaSuper/
├── index.html              # 首頁
├── a.html                  # A 類分類專頁
├── b.html                  # B 類分類專頁
├── c.html                  # C 類分類專頁
├── README.md               # 完整文檔
├── QUICK_START.md          # 本檔案
├── .gitignore              # Git 忽略檔案
├── CNAME                   # 自訂域名（GitHub 自動生成）
└── assets/
    ├── css/
    │   └── style.css       # 共用樣式表
    └── images/
        ├── logo.png        # 品牌 Logo
        ├── cat_a_banner.jpg # A 類 Banner
        ├── cat_b_banner.jpg # B 類 Banner
        └── cat_c_banner.jpg # C 類 Banner
```

## 下一步

1. **本地測試**：運行 `python3 -m http.server 8000` 並訪問網站
2. **推送到 GitHub**：按照上述步驟建立倉庫並推送程式碼
3. **啟用 GitHub Pages**：在 Settings 中啟用 Pages
4. **配置自訂域名**：設定 DNS 並連接自訂域名
5. **定期更新**：添加最新產品和穿著內容

## 支援資源

- GitHub Pages 文檔：https://docs.github.com/en/pages
- DNS 設定指南：https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site
- HTML 教學：https://www.w3schools.com/html/
- CSS 教學：https://www.w3schools.com/css/

---

**祝你部署順利！** 🚀

如有任何問題，請參考 `README.md` 中的常見問題部分。
