# AGENTS.md

給 AI agents：先讀上游 skills，再查本專案的實務坑。

1. 先讀 `gws-shared`（[直連](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-shared/SKILL.md)），再讀對應服務的 skill（[`gws-drive`](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-drive/SKILL.md)、[`gws-sheets`](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-sheets/SKILL.md)、[`gws-docs`](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-docs/SKILL.md)）。安裝、skills、OAuth 是三件不同的事，以 `--help` 與 `gws schema` 為準。
2. 開工前讀 [PITFALLS.md](PITFALLS.md) 24 個速查主題，判斷是 Google 規則、gws／SDK 行為，還是應用程式整合問題。
3. 出事時查 [catalogue/INDEX.md](catalogue/INDEX.md)：108 個主紀錄＋75 個維修／延伸，共 183 筆，保留原編號。不要把 183 筆說成 183 個獨立 Google 缺陷。
4. 寫入前只做小批唯讀檢查，核對 ID／mapping 再擴大；結果不明先讀回，不重播建立或 append。
5. 不記錄 token、續傳 session URI、客戶資料。狀態與參數是歷史記載，未重跑 live 驗證，不能當成現行保證。

範圍與授權見 [README.md](README.md)、[SOURCES.md](SOURCES.md)、[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。
