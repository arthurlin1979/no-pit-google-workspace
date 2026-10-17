# 30 秒 Quick Start

給人跟 AI：三步確認環境，再決定要不要往下做。

## 人用：先確認三件事是分開的

1. 裝 CLI：依 [上游安裝說明](https://github.com/googleworkspace/cli#installation) 裝好 `gws`。
2. 裝 skills：依 [skills 說明](https://github.com/googleworkspace/cli#ai-agent-skills)選需要的，先讀 `gws-shared`，再讀 `gws-drive`／`gws-sheets`／`gws-docs`。
3. 走完 OAuth：跑一次最小唯讀檢查，確認帳號、看得到的檔案、實際授權三者一致。

實際命令以你裝的版本的 `--help` 及 `gws schema` 為準，不同版本行為可能不同。

## AI 用：開工前讀這三頁

1. [PITFALLS.md](PITFALLS.md)：24 個速查主題，只作入口。
2. [catalogue/INDEX.md](catalogue/INDEX.md)：183 筆完整索引（108 主紀錄＋75 維修／延伸）。
3. [SOURCES.md](SOURCES.md)：哪些是自家案例、哪些是官方規則、哪些沒驗證過。

## 最小安全順序

1. 唯讀檢查（帳號、目標資源、實際授權）。
2. 小批寫入，核對內容與 mapping 後再擴大。
3. 結果不明先讀回，不重播建立或 append。

完整原則見 [README.md](README.md) 的「最小操作方式」。
