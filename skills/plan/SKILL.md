---
name: plan
description: 変更要件と調査結果を実装可能な計画へ整理する。コード、設定、ドキュメントの変更前に使う。
---

# plan

repo-tracked file、既存未追跡ファイル、Git index、外部永続状態を変更せず、implement が追加判断なしで着手できる計画を作る。計画中はファイルを書き換えるコマンドや検証コマンドを実行しない。

## Workflow

`references/workflow.md` を読む。

## Output

- 目的と成功条件
- 必須入力と、不足・矛盾時に `research` / `grilling` へ戻す判断
- 変更対象ファイルと変更内容
- 対象外
- test へ渡す実装契約（対象、対象外、受入条件、既存差分の扱い）
- 実装順序と既存パターン
- test で実行する検証（コマンド、対象、期待結果、副作用。必要なら timeout や外部アクセスも記載）
- 互換性、セキュリティ、残リスク
- 未確定事項。事実確認は `research`、意思決定は `grilling` に戻す
