# 常見問題（先看這個）

從現有 183 筆濃縮的入口，完整脈絡請點連結回去看。狀態與數字是歷史記載，未重跑 live 驗證。

## 授權／登入卡住

- 登入一次就以為永遠有效？先看 Testing 模式的 7 天規則有條件與例外，不是所有 token 都一樣。→ [GP-45](catalogue/records.md#gp-45)、[GW-003](PITFALLS.md)
- OAuth 成功就能動所有檔案？不行。scope、看得到的檔案、能不能編輯是三件事，要分開查。→ [GW-005](PITFALLS.md)、[GP-50](catalogue/records.md#gp-50)
- 內嵌瀏覽器授權失敗？換受支援的一般瀏覽器走完整流程，不要中途切 session。→ [GW-002](PITFALLS.md)、[GP-47](catalogue/records.md#gp-47)
- 背景工作突然斷線？先檢查離線授權與 refresh token 保存，不要直接認定被撤銷。→ [GP-44](catalogue/records.md#gp-44)

## 限流／重試：403 不等於不能 retry

- 403 要連 reason 一起看：`rateLimitExceeded`／`userRateLimitExceeded` 可以退避，真正權限不足才停。→ [GW-009](PITFALLS.md)、[GP-36](catalogue/records.md#gp-36)
- Sheets 超額可能回 429，按分鐘補充額度＋指數退避，不要無限重試。→ [GP-43](catalogue/records.md#gp-43)
- 批次做大不一定快，还要看 payload、處理時間與 batch 計數邊界。→ [GW-012](PITFALLS.md)、[GP-42](catalogue/records.md#gp-42)

## 寫入後讀不到／重複寫入

- 結果不明先查原操作或 session，再按 ID／marker／mapping 核對，不要直接再 create／append。→ [GW-010](PITFALLS.md)、[GP-09](catalogue/records.md#gp-09)
- 建立後用名稱搜尋找不到？名稱只用來顯示，持久保存 file ID，名稱只作輔助。→ [GW-013](PITFALLS.md)、[GP-88](catalogue/records.md#gp-88)
- 大檔上傳失敗就整支重傳？用 resumable 規則續傳，chunk 需為 256 KiB 倍數（最後一塊例外），不要公開 session URI。→ [GW-016](PITFALLS.md)、[GP-39](catalogue/records.md#gp-39)

## Sheets 常見誤判

- 只算檔案數、沒算讀回與權限檢查？讀寫有分開配額，要分開估。→ [GW-011](PITFALLS.md)、[GP-40](catalogue/records.md#gp-40)、[GP-41](catalogue/records.md#gp-41)
- 新值存在就以為舊資料消失？讀回新值、列數與清除範圍一起看。→ [GW-020](PITFALLS.md)

還沒解決？去 [完整索引](catalogue/INDEX.md) 用編號找，或開 issue 附上：版本、哪一步、看到的狀態／reason、已做過的唯讀檢查。數字對不上有出入也歡迎回報。
