# GSC実績ダッシュボード

GSC（グッドスマイルカンパニー）の売上実績・計画を可視化するシングルファイルHTMLダッシュボード。

- **公開URL**: https://buntakawamura-design.github.io/gsc-dashboard/
- GSCは**9月決算**（FYは10月開始〜9月終了。FY26 = 2025年10月〜2026年9月）

## フォルダ構成

```
ダッシュボード/
├── index.html       ← 公開用（dashboard.html と同一内容。コミット前に必ず同期）
├── dashboard.html   ← ダッシュボード本体（データはJS内に埋め込み）
├── data/            ← データ原本Excel（git管理外）
│   ├── 【FY26】企画部_月次報告.xlsx   ← ★正式ソース（売上実績・地域・FY26月次）
│   ├── IP毎全実績_過去5年.xlsx        ← IP×ブランド×地域ドリルダウンの元データ
│   ├── GSCラインナップ.xlsx           ← 今後の売上予定・案内予定（パイプライン）
│   └── archive/                       ← 旧版・役目を終えたファイル
└── docs/            ← 議事録・作業ログ・参考資料（git管理外）
```

## 更新手順

1. `data/` 配下のExcelを最新版に差し替える
2. Claude Code に「最新Excelを反映して」と依頼（`dashboard.html` 内の `DATA` / `DRILL` / `FY26_8M` / `PIPELINE` 定数が更新対象）
3. `dashboard.html` → `index.html` に同期: `cp dashboard.html index.html`
4. コミット & push で GitHub Pages に反映

## データソースと埋め込み先の対応

| dashboard.html 内の定数 | 出典 |
|---|---|
| `DATA.sales`（年度別実績/計画） | 【FY26】企画部_月次報告.xlsx |
| `DATA.brands` / `DATA.ips` / `DRILL` | IP毎全実績_過去5年.xlsx |
| `DATA.regions` | 【FY26】企画部_月次報告.xlsx 地域シート |
| `FY26_8M`（FY26月次実績） | 【FY26】企画部_月次報告.xlsx（受注締め月基準） |
| `PIPELINE`（今後の売上予定） | GSCラインナップ.xlsx 締め月基準 |
