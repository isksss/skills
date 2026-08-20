# commit workflow

- `git status --short --branch`、diff、未追跡ファイルを確認する。
- 秘密情報、個人情報、生成物、無関係差分を除外する。
- 外部スキルの変更では、source、ref、lock、ライセンス、内容の差分を確認する。
- 必要なら commit 範囲を分割する。
- メッセージは `[prefix] 日本語の要約` と本文にする。
- 既定 prefix は add、fix、update、remove、refactor、docs、test、chore、perf、ci。
- `git add .` は避け、対象パスだけ stage する。
- stage 後に `git diff --cached` と `git diff --cached --check` を確認する。
- 確認済みの対象だけを stage し、`git commit` を実行する。
- commit 後に SHA、`git status --short --branch`、意図的に残した差分を確認する。
- 変更内容、実行済み・未実行の検証、残リスクを報告する。
