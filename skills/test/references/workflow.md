# test workflow

- plan、既存の package scripts / build 設定、現在の差分を確認する。
- plan に記載された検証を優先し、リポジトリ固有の標準コマンドを使う。
- formatter check、対象テスト、lint、typecheck、build の順を基本に、依存しない検証は並列実行する。
- 変更範囲に対する局所検証から始め、必要な場合だけ全体検証へ広げる。
- auto-fix、formatter write、migration、データ変更など tracked file や外部状態を変更するコマンドは実行しない。
- 失敗を「変更起因」「既存問題」「環境問題」「未特定」に分類し、ログから判断できる根拠を示す。
- 失敗時は原因修正のため `implement` に戻し、修正後に同じ検証を再実行する。
- 実行結果、未実行の検証、残リスクを review が利用できる形で報告する。
