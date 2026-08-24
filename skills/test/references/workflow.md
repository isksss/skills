# test workflow

- plan、既存の package scripts / build 設定、現在の差分を確認する。plan がない場合はユーザー指定の検証範囲を確認する。
- plan に記載された検証を優先し、リポジトリ固有の標準コマンドを使う。
- 実行前に script / hook / build 設定と検証コマンドの副作用を評価する。通信、認証情報、DB、container、daemon、port、cache、生成物への影響が不明または危険なものは実行しない。
- 外部 DB 等の状態変更は、対象と before/after が plan に明記されている場合だけ行う。認証情報は収集・送信・出力しない。
- 各コマンドには有限の timeout を設定し、共有資源の競合が不明な検証は並列化しない。
- 変更範囲に対する局所検証から始め、必要な場合だけ全体検証へ広げる。
- auto-fix、formatter write、migration、データ変更など tracked file や外部状態を変更するコマンドは実行しない。
- cleanup は test 実行中に作成した隔離済みの一時資源だけに限定し、既存資源や Git 状態は復元・削除しない。
- 実行前後に `git status --short`、`git diff --cached --stat`、`git diff --stat` を確認し、予期しない変更を報告する。
- 失敗を「変更起因」「計画不足」「既存問題」「環境問題」「未特定」に分類し、変更起因は `implement`、計画不足は `plan`、既存問題は `review`、環境問題は `test`、未特定は `research` に戻す。
- 実行結果、未実行の検証、外部状態、残リスクを `review` が利用できる形で報告する。
