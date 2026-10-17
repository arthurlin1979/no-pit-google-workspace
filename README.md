# 不踩坑：Google Workspace

更新日期：2026-10-17

給 AI agents 與開發者使用的 Google Workspace 整合經驗：先讀上游 gws skills，再讀這裡的實務補充。

本專案整理實際遭遇的整合問題、已有的實作紀錄及可核對的外部規則。解法可能結合自行實驗、官方文件與社群資料，部分由 AI 協助搜尋及編輯，不宣稱所有方法皆由我們發明。
這是獨立整理，與 Google 或 gws 上游無隸屬或背書關係。

## 為什麼有這個專案

說句實話，vibe coding 我最怕的就是碰到 Google。

只要有 Google 在，每個步驟都是陷阱。寫一段、錯一段，重試、再重來，帳單跟時間一起燒。後來我才發現 Google 有自己的 gws skills 可以用，先讀它，確實能少踩很多坑，你一定要試試看。

但坦白說，光靠 skills 還是不夠。實務上，Google Drive、試算表、圖片同步，一路還是會冒出各種問題，有些是官方規則，有些是接線方式，有些純粹是我當初沒想清楚。

所以我把自己踩破的坑全部整理出來，做成一個資料庫，方便 AI 查詢。出事的時候查一下：這個問題我們是不是遇過？開工之前先讀一下：有哪些東西可能會影響？

這裡 108 個主紀錄加 75 個維修延伸，總共 183 筆，另有 24 個速查主題當入口。很多是個人經驗，加上 AI 幫忙整理。數字都是當時的記載，不是現在的保證，如果你覺得哪裡不對、要微調，歡迎通知我，感謝。

## 先從這裡讀

- [給 AI agents 的入口](AGENTS.md)：先讀上游 skills，再查 PITFALLS 與 183 筆索引。
- [30 秒 Quick Start](QUICKSTART.md)：人用三步確認、AI 用三頁開工。
- [常見問題](TROUBLESHOOTING.md)：從 183 筆濃縮的先看入口，完整脈絡連回原編號。
- [完整紀錄索引](catalogue/INDEX.md)：逐條保留 108 個主紀錄與 75 個維修／延伸項的原編號。
- [108 個主紀錄](catalogue/records.md)：連線、重試、批次、SHA、測試、排程、mapping 等，逐條寫問題／參數、處理及驗證界線。
- [維修紀錄 GP-T-01 至 GP-T-38](catalogue/repairs-01-38.md) 及 [GP-T-40 至 GP-T-76](catalogue/repairs-40-76.md)：實際整合與交付過程的處理紀錄，包含原紀錄的已解、部分處理或待核實界線。
- [PITFALLS.md](PITFALLS.md)：24 個快速查閱主題，只作入口，不取代完整紀錄。
- [SOURCES.md](SOURCES.md)：來源、版本、證據邊界與致謝。
- [gws 上游摘錄](third_party/gws-cli/README-excerpts.md)：schema、分頁及憑證優先序的原文摘錄，採 Apache-2.0。
- [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)：第三方內容的授權範圍。

完整目錄共 183 筆來源紀錄，保留重複與延伸的關聯，不宣稱是 183 個獨立 Google 缺陷。
主紀錄也包含內部參數、契約和原表已有的外部規則參考，逐條標示類型；不把每一列包裝成一次親身實驗。
這輪以既有自有紀錄為主，沒有再擴充外部材料。外部原文摘錄保留在附錄，不作主要內容。

## 使用前提

使用 gws CLI 的讀者，先依 [上游安裝說明](https://github.com/googleworkspace/cli#installation) 安裝 CLI，再依 [skills 說明](https://github.com/googleworkspace/cli#ai-agent-skills) 選擇需要的 skills。
先讀 `gws-shared`，再讀對應的 `gws-drive`、`gws-sheets`、`gws-docs` 等服務說明。

安裝 CLI、安裝 skills、完成 OAuth 是不同步驟。實際命令以所用版本的 `--help` 及 `gws schema` 為準。
如果直接使用 SDK／API，也可參考本專案的通用整合經驗。gws 上游明示它並非 Google 正式支援的產品。
閱讀本專案或安裝任何 skill 都不代表取得帳號、檔案或正式環境的操作授權。

## 最小操作方式

1. 確認帳號、環境、目標資源及當前授權，先做唯讀檢查。
2. 只做已獲授權的小批寫入，核對 Google 內容及 mapping 後再擴大。
3. 結果不明先讀回，不立即重播建立或 append。
4. 記錄版本、stage、status 與 reason，不記錄 token、續傳 session URI 或客戶資料。
5. 將模擬、live、人工驗收與未測範圍分開標示。

## 授權

除明確標示的第三方內容外，本專案有權授權的原創文字、編排與範例採 [MIT License](LICENSE)。
第三方內容依各自授權；本專案的 MIT 不取代 Apache-2.0、Creative Commons 或其他適用條件。

目前實際收錄的第三方資料僅限 `third_party/gws-cli/`：摘錄檔與所附授權副本適用 Apache-2.0，詳見 [第三方聲明](THIRD_PARTY_NOTICES.md)。
其他 Google 文件、社群回答及 repo 目前只作參考連結與自行摘要，沒有整份搬入。

## 範圍與維護

這是既有來源表的逐條整理，不是所有 Google 問題的完整清單，也不保證其他版本或環境會得到相同結果。
條目中的狀態與參數是原紀錄的歷史描述；本次文件整理沒有重新跑 live 驗證，不能據此判斷目前正式環境的狀態。
歷史搜尋鏈未完整保留的地方會揭露，不以今天找到的官方文件冒充當年採用解法的確切出處。

新增內容時，先判斷是 Google 規則、gws／SDK 行為或應用程式整合問題；同類問題更新原條目。
收錄第三方原文或程式前，要確認具體檔案的來源、固定版本及授權，保留必要聲明與修改標示；無法確認就只留可核對的連結或暫不收錄。
私人原始紀錄、客戶資料、環境設定、對話紀錄與 Git 歷史不屬於這份文件包。
