# Claude Session Reader

一個純前端、可離線使用的 Claude Code session 閱讀器。將 Claude session 的 `.jsonl` 檔案拖進網頁，即可用聊天室形式閱讀對話歷程。

## 功能

- 拖放或選擇 Claude Code session `.jsonl` 檔案
- 只顯示真正的使用者輸入與 Claude 完整回覆
- Claude 回覆僅保留 `stop_reason: "end_turn"` 的訊息
- 將 `AskUserQuestion` 還原成一般問答內容
- 隱藏 thinking、tool use、指令輸出與其他內部事件
- 支援 Markdown、程式碼區塊與全文搜尋
- 使用 Clawd 聊天圖示與左右聊天氣泡呈現
- 所有資料只在瀏覽器本機處理，不會上傳

## 使用方式

### GitHub Pages

開啟部署完成的 GitHub Pages 網址，將 Claude session `.jsonl` 檔拖曳到畫面中央即可。

### 離線使用

直接用瀏覽器開啟 `index.html`，再拖入 session 檔案。favicon、標題圖示與 Claude 頭像都已內嵌在 HTML 中，不需要網路或額外套件。

## Session 顯示規則

閱讀器專注於適合展示給專案成員的對話內容：

- 使用者訊息會移除 Claude Code 的 command 包裝標記。
- Claude 訊息只顯示 `message.stop_reason === "end_turn"` 的文字區塊。
- `AskUserQuestion` 是例外：問題、選項與使用者答案會依原順序呈現。
- `thinking`、一般 `tool_use`、`tool_result`、system event、attachment 與 sidechain 不會顯示。

## 隱私

此專案沒有後端服務。讀取、解析、搜尋與渲染都在目前的瀏覽器分頁內完成，session 內容不會由本專案傳送到任何伺服器。

> Session 仍可能包含專案名稱、提示內容或原始碼。分享 session 檔案前，請自行確認其中沒有不應公開的資訊。

## 專案結構

```text
.
├── index.html       # 完整的離線閱讀器
├── clawd.png        # Claude 對話頭像來源
├── clawd-chat.png   # favicon 與標題列圖示來源
├── LICENSE
└── README.md
```

## 授權

本專案採用 [MIT License](LICENSE)。
