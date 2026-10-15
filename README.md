# MarkFlow 考卷數位批閱工具 - 部署說明

本專案為零打包建置依賴的單一靜態檔案（Single-file SPA），可直接託管於 Cloudflare Pages。

---

## 1. 建立本機專案與推送至 GitHub

請在您的終端機（Terminal）執行以下指令：

```bash
# 建立專案資料夾並進入
mkdir markflow-grader && cd markflow-grader

# 將 index.html 複製至此目錄，並初始化 Git
git init
git add index.html README.md
git commit -m "feat: initial commit of single-file MarkFlow exam grader"

# 建立 main 分支並關聯您的 GitHub 遠端儲存庫（請替換 your-username/repo-name）
git branch -M main
git remote add origin https://github.com/your-username/markflow-grader.git
git push -u origin main
```

---

## 2. Cloudflare Pages 部署設定

1. 登入 [Cloudflare Dashboard](https://www.google.com/search?q=https%3A%2F%2Fdash.cloudflare.com%2F)。
2. 進入側邊欄的 **Workers & Pages** > 點擊 **Create application** > 切換至 **Pages** 分頁。
3. 選擇 **Connect to Git** 並授權存取剛才建立的 `markflow-grader` 儲存庫。
4. 在 **Set up builds and deployments** 頁面填寫以下參數：
   - **Project name**: `markflow-grader`（或自訂名稱）
   - **Production branch**: `main`
   - **Framework preset**: `None`
   - **Build command**: *(留空，不需任何打包指令)*
   - **Build output directory**: `/` *(或留空表示根目錄)*
5. 點擊 **Save and Deploy**。
6. Cloudflare Pages 會在數秒內完成靜態發布，並提供 `https://markflow-grader.pages.dev` 的專屬網址。日後只要執行 `git push`，Cloudflare 即會自動觸發更新。
