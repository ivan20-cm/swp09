# SWP09 英文聽讀 APP

## 使用方式

1. 先從單字清單選一題。本頁包含 24 個日常、校園與生活英文單字／片語。
2. 按「聽示範」或「慢速播放」，以 SpeechSynthesis 播放英文。
3. 按「開始跟讀」，允許麥克風後念出上方英文。SpeechRecognition 會將語音轉成文字。
4. 念完會自動比對，也可按「結束收音」。頁面顯示辨識文字、「念對／念錯」與統計。

建議使用最新版桌面 Chrome，從 GitHub Pages 的 HTTPS 網址開啟，並保持網路連線。使用其他瀏覽器時，實際支援仍取決於瀏覽器與辨識服務。本頁會偵測 API 支援並顯示提示。直接雙擊本機檔案適合查看畫面，但不能作為線上語音辨識的驗收方式。

## 判定與統計

- 比對第一個最終辨識候選文字與題目，忽略英文大小寫、標點和重複空白。
- 最終文字相同顯示「念對」，不同顯示「念錯」。沒有收到語音或服務錯誤不計入統計。
- 正確率＝念對次數 ÷ 完成辨識的練習次數 × 100%。重試同一題也會計入。
- 記錄只保留在目前頁面記憶體中，重新整理或按「重置統計」會清空。
- 這是語音辨識文字比對，不是專業音素、重音或口音評分。辨識引擎誤判也可能導致顯示念錯。
- 頁面切換到背景時會停止朗讀、取消收音。沒有另存錄音，但瀏覽器可能將音訊送往其辨識服務處理。

## GitHub Pages 部署：只需要一個 HTML 檔

1. 下載 `SWP09-english-practice.html`，改名為 **`index.html`**。不要保留其他前綴，也不要變成 `index.html.html`。
2. 在 GitHub 新建 Public repository，例如 `swp09-english-practice`。使用新 repository 可避免覆蓋上一份作業。
3. 進入 repository，點 **Add file → Upload files**，上傳 `index.html` 到最外層，然後按 **Commit changes**。
4. 開啟 **Settings → Pages**：
   - Source：**Deploy from a branch**
   - Branch：**main**（或你實際存放檔案的分支）
   - Folder：**/(root)**
   - 按 **Save**。
5. 等待發布，最多可能需要約 10 分鐘。在 **Actions** 確認 `pages build and deployment` 成功，再回到 **Settings → Pages → Visit site**。
6. 作業繳交網址應為 `https://你的帳號.github.io/swp09-english-practice/`，不要繳交 repository 網址或 HTML 原始碼頁。

HTML 內含全部 CSS、JavaScript 與題庫，沒有本機相依檔案、外部字型或套件。不需上傳 vendor 資料夾，也不需要 npm、API Key 或後端。語音功能使用瀏覽器提供的 Web Speech API，辨識服務仍可能需要網路。

官方部署說明：https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## 部署後驗收

- 點「聽示範」有英文聲音；慢速播放的語速較慢。
- 點「開始跟讀」能要求麥克風權限，說出題目後顯示實際辨識文字。
- 正確念出 `Hello`，若引擎辨識為 `hello`，結果應是念對。
- 在 `Hello` 題說出 `Good morning`，若引擎辨識為該文字，結果應是念錯。
- 上述兩次完成辨識後：練習 2 次、念對 1 次、正確率 50%。
- 拒絕麥克風權限時，頁面顯示提示且統計不增加。
- 可以切換題目及重置統計，手機畫面可操作。

## 常見問題

- **404／找不到網站**：先看 Actions 是否成功，再檢查 `index.html` 的名稱與 Pages 的分支、資料夾。
- **網頁有顯示，但無法跟讀**：這是語音功能問題。確認 HTTPS、支援的瀏覽器、麥克風權限和網路。請依頁面顯示的錯誤處理。
- **麥克風被拒絕**：到瀏覽器該網站的權限設定允許麥克風；Mac 也要在系統設定 → 隱私權與安全性 → 麥克風允許該瀏覽器，之後重新整理。
- **聽不到示範**：確認音量與瀏覽器英文語音可用，再重新按播放。切換題目也會停止目前朗讀。
- **辨識文字和實際講的不同**：在安靜環境靠近麥克風重新試一次；服務辨識結果可能受口音、雜音及網路影響。

## 完成範圍與驗證

已完成前端網站與單檔封裝。已檢查 JavaScript 語法、相依資源及以模擬語音事件驗證比對、統計、錯誤、重複事件與清理流程；模擬驗證不代表已通過真人麥克風測試。實際裝置朗讀、真人收音與瀏覽器視覺驗收仍須依上方清單測試。

本次尚未發布到 GitHub Pages：目前沒有可操作的 GitHub repository 或帳號存取。完成部署後，才能繳交上線網址。

參考：
- https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition
- https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis
