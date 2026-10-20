# 期中教案 - AGENTS.md

## 專案入口

專案名稱：期中教案
專案用途：期中教學教案與教材規劃、雲端部署與公開發布
主要工作目錄：c:\Users\USER\OneDrive\Desktop\Antigravity\期中教案
GitHub repo：https://github.com/Ho-yu-chiao/midterm-lesson-plan
公開線上網頁：https://ho-yu-chiao.github.io/midterm-lesson-plan/
預設 branch：main

## 服務連接與對應

Firebase：MCP 已註冊於 .agents/mcp_config.json（待安裝 Node.js 啟用 npx）
NotebookLM：已連線（帳號已登入，MCP 已註冊於 ~/.gemini/antigravity/mcp_config.json）
GitHub CLI：已連線（帳號 Ho-yu-chiao 已登入）
GitHub Pages：已啟用（main 分支根目錄靜態網站）
Obsidian vault：未設定
專案駕駛艙：未設定

## 已安裝技能

- `antigravity-lazy-packs`：懶人包自動安裝與管理入口（支援無 Node.js Git 回退）
- `01-notebooklm`：NotebookLM MCP 連接
- `02-github`：GitHub CLI 連接
- `03-firebase`：Firebase MCP 連接
- `04-draw`：生圖指引（使用內建工具）
- `05-workflow`：開工 / 收工 / 新專案初始化工作流程
- `06-obsidian`：Obsidian 專案筆記連接（直接讀寫 vault）

## 工作規則

- 回應使用繁體中文。
- 涉及檔案操作時回報完整產出位置。
- 使用 PowerShell 語法。
- 開工時讀本檔、檢查 Git 狀態。
- 收工時檢查是否有敏感資料、檢查 diff 後只提交相關檔案。
- 不把每日流水帳寫進本檔。

## 不要做

- 不要 commit API key、token、密碼、Firebase Admin 憑證。
- 不要 commit 學生真名或個人隱私資料；正式資料只用班級代號與座號。
- 不要自動納入無關 git 變更。
