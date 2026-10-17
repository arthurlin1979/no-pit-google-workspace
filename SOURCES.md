# 來源與致謝

核對日期：2026-10-17

感謝 Google Workspace CLI、Google API 文件及社群討論的維護者與參與者。
列為來源不代表合作、背書、共同作者，或我們使用過其程式碼。

## 來源種類

- **完整目錄**：[catalogue/INDEX.md](catalogue/INDEX.md) 保留來源表的 108 個 GP 主紀錄與 75 個 GP-T 維修／延伸項；沒有把它們當成 183 個獨立事故，也沒有拿 24 個 GW 速查主題取代原紀錄。
- **整合案例／實作紀錄**：來自我們既有的私人紀錄，公開的是去識別化摘要；不公開原始客戶資料、log、主機及資源 ID。
- **本次官方佐證**：現在可讀取且支持相關規則的文件，不假裝是當時 AI 搜尋採用的同一個網頁。
- **新增上游補充**：GW-001、GW-006、GW-007；它們沒有被冒充成原私人事故。
- **背景回報**：他人的 issue，未在本次重現，不拿來證明私人事故根因。

完整目錄逐條分清自家案例、內部參數／契約、交付與測試問題、原表已有的外部規則及待確認推論。
原表外部規則的數字若保留，僅代表歷史記載；本輪沒有新增網路研究，不以今天的文件整理日期冒充官方額度已重新核對。
原紀錄中的已修／待排是歷史狀態，不代表本次實際執行、仍待使用者處理，或目前正式環境狀態。

## 實際收錄的第三方內容

僅有 [gws README 摘錄](third_party/gws-cli/README-excerpts.md) 及其 Apache-2.0 授權副本。
具體來源、版本、修改方式與適用範圍見 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。
三段摘錄分別補足 schema 查詢、分頁與憑證優先序；不複製整份 skills，也不把摘錄當成目前所有版本的保證。

## 官方與上游參考

| 來源 | 適用主題 | 使用方式 |
|---|---|---|
| [gws 固定版本 README](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/README.md) | GW-001、GW-006、GW-007；CLI 前提 | 三段明示的原文摘錄另附 Apache-2.0；其餘連結及摘要。 |
| [gws 固定版本 shared skill](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-shared/SKILL.md) | 認證、旗標、shell 說明比較 | 參考連結，沒有搬入 skill 檔案。README 與 skill 引號說明有差異，需用實際 shell 驗證。 |
| [OAuth expiration](https://developers.google.com/identity/protocols/oauth2?hl=en#expiration) | GW-003 | 技術事實的自行整理。 |
| [Drive scopes](https://developers.google.com/workspace/drive/api/guides/api-specific-auth?hl=en) | GW-005 | 技術事實的自行整理。 |
| [Shared drives](https://developers.google.com/workspace/drive/api/guides/enable-shareddrives?hl=en) | GW-005 | 通用補充，不宣稱已測完所有情境。 |
| [Drive errors](https://developers.google.com/workspace/drive/api/guides/handle-errors?hl=en) | GW-009 | status／reason 與退避規則摘要。 |
| [Sheets limits](https://developers.google.com/workspace/sheets/api/limits?hl=en) | GW-011、GW-012 | 讀寫配額、payload 與處理時間規則摘要。 |
| [Sheets batch](https://developers.google.com/workspace/sheets/api/guides/batch?hl=en) | GW-012 | batch 計數及原子性摘要。 |
| [Drive search](https://developers.google.com/workspace/drive/api/guides/search-files?hl=en) | GW-013 | ID／marker 查詢的官方佐證。 |
| [Drive custom properties](https://developers.google.com/workspace/drive/api/guides/properties?hl=en) | GW-013 | appProperties 的官方佐證。 |
| [Drive fields](https://developers.google.com/workspace/drive/api/guides/fields-parameter?hl=en) | GW-014 | partial response 的官方佐證。 |
| [Drive uploads](https://developers.google.com/workspace/drive/api/guides/manage-uploads?hl=en) | GW-010、GW-016 | resumable upload／chunk 規則摘要。 |

Google Developers 頁面通常標示文字 CC BY 4.0、程式範例 Apache-2.0，仍以各頁例外為準，見 [Site Policies](https://developers.google.com/terms/site-policies)。本批沒有搬入其原始段落、翻譯或程式片段。

## 可辨識的歷史外部參考

- [googleapis/google-api-nodejs-client #3426](https://github.com/googleapis/google-api-nodejs-client/issues/3426)：resumable session URI 的歷史參考。該 repo 程式碼為 Apache-2.0；此處僅連結，不宣稱使用其程式或採用該 issue 的修法。
- [rclone/rclone #7384](https://github.com/rclone/rclone/issues/7384)：Drive 請求限制的歷史討論。該 repo 程式碼為 MIT；此處不複製程式，也不把舊額度當成現行規則。
- [Stack Overflow 34339500](https://stackoverflow.com/questions/34339500/what-are-the-consistency-guarantees-of-the-google-drive-api)：歷史一致性討論。本次 API 讀回問題及現存回答為 CC BY-SA 3.0；只保留連結，不收錄回答、翻譯或程式。將來若使用特定 revision，須另核對該 revision。

GitHub issue／留言不能一律假設受該 repo 程式碼授權涵蓋。

## 新增背景回報，未重現

- [gws #572](https://github.com/googleworkspace/cli/issues/572)：憑證切換與 token cache。
- [gws #878](https://github.com/googleworkspace/cli/issues/878)：特定缺少 project_id 設定與 quota project 的關係。
- [gws #777](https://github.com/googleworkspace/cli/issues/777)：錯誤輸出的 Retry-After。

這些是本次整理時的背景提醒，沒有被認定為我們既有事故的根因。

## 尚未核實與未收錄的內容

部分歷史紀錄只留網站名稱或 issue 編號，沒有保留完整搜尋鏈。無法讀取實際內容或辨識原文章的來源，不作已驗證佐證，不猜填作者，不搬原文。
目前收錄方式為自主摘要、明示的 Apache 摘錄及來源連結；沒有將 CC BY-SA 或無授權內容改標 MIT。

每次新增第三方資料都要記錄：檔案、來源、固定版本、授權、修改方式及必要聲明。這份來源表不是法律意見，也不宣稱所有歷史內容權利均已查明。
