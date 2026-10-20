---
name: antigravity-lazy-packs
description: AntiGravity 懶人包 — 服務連接與工作流程設定。說「AntiGravity 懶人包」「安裝 Antigravity 設定」時載入。
---

# AntiGravity 懶人包 — AI Agent 自動安裝入口

當使用者要求安裝 AntiGravity 懶人包或指定此安裝入口時，請依以下流程執行。

## 步驟一：認識可用懶人包

| 編號 | Skill 名稱 | 說明 |
|:---:|:---|:---|
| 01 | `01-notebooklm` | 連接 NotebookLM MCP |
| 02 | `02-github` | 連接 GitHub CLI |
| 03 | `03-firebase` | 連接 Firebase MCP |
| 04 | `04-draw` | 生圖指引 |
| 05 | `05-workflow` | 開工 / 收工 / 新專案初始化 |
| 06 | `06-obsidian` | 連接 Obsidian 專案筆記（直接讀寫 vault，不裝 MCP） |
| 00 | `00-install-all` | 一次安裝全部 |

## 步驟二：讓使用者選擇

列出上表給使用者看，並詢問要安裝哪些技能（支援多選或輸入 `00` 一次安裝全部）。

## 步驟三：依序安裝（具備無 Node/npx 回退機制）

AntiGravity 2 的專案技能目錄為 `.agents/skills/`。

### 策略 A（環境有 npx）
對選取的每個 skill 執行：
```bash
npx skills add mathruffian-dot/antigravity-lazy-pack --skill <skill名稱> -y
```

### 策略 B（環境無 npx / 離線回退）
若本機未安裝 Node.js / npx，自動改用 Git 進行本機複製：
1. 複製儲存庫至暫存區：
   ```powershell
   git clone https://github.com/mathruffian-dot/antigravity-lazy-pack.git "$env:TEMP\antigravity-lazy-pack"
   ```
2. 將選取的技能資料夾複製至專案：
   ```powershell
   Copy-Item -Path "$env:TEMP\antigravity-lazy-pack\skills\<名稱>" -Destination ".agents\skills\<名稱>" -Recurse -Force
   ```
3. 清理暫存資料夾：
   ```powershell
   Remove-Item -Path "$env:TEMP\antigravity-lazy-pack" -Recurse -Force
   ```
4. 依序讀取所選技能的 `SKILL.md`，並執行該技能的先備檢查與初始化設定。

## 步驟四：回報結果

以 Markdown 表格回報每項安裝狀態（✅ 已就緒 / ⚠️ 待設定 / ❌ 失敗），並附上後續設定步驟。
