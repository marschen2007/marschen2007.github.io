# Hexo 部落格發布與備份工作流程

## 發布流程

當需要發布新文章或更新網站內容時，需要執行以下兩個步驟：

### 1. 部署到 GitHub Pages

```bash
hexo clean && hexo generate && hexo deploy
```

這個指令會：
- 清理之前的生成檔案
- 重新生成網站內容
- 將生成的檔案部署到 GitHub Pages（main 分支）

### 2. 備份原始碼

```bash
git add . && git commit -m "更新：[相關文章標題]" && git push origin source
```

這個指令會：
- 將所有更改加入 git
- 提交更改並加上說明
- 將原始碼推送到 source 分支

## 分支說明

- `main` 分支：存放編譯後的網站檔案，由 hexo deploy 自動處理
- `source` 分支：存放網站原始碼，包含文章、主題設定等

## 故障排除

如果部署後網站沒有立即更新：

1. 等待 GitHub Pages 部署
   - GitHub Pages 可能需要幾分鐘來完成部署
   - 可以在 repository 的 Settings > Pages 中查看部署狀態

2. 清除瀏覽器快取
   - Windows/Linux：按 Ctrl+F5
   - macOS：按 Cmd+Shift+R
   - 或使用瀏覽器的開發者工具清除快取

3. 使用無痕視窗
   - 開啟無痕視窗測試，避免快取影響

4. 檢查部署日誌
   - 確認 hexo deploy 命令執行成功
   - 檢查 GitHub Actions（如果有設定）的執行狀態

## 最佳實踐

1. 總是執行完整的兩步驟流程，確保：
   - 網站內容正確部署
   - 原始碼完整備份

2. 定期檢查備份
   - 確認 source 分支的內容是最新的
   - 特別是在進行重要修改後

3. 保持良好的提交訊息
   - 清楚說明更新的內容
   - 方便日後追蹤變更

4. 在本地預覽
   - 使用 `hexo server` 在部署前預覽變更
   - 確保內容和格式正確
