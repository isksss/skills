---
name: test
description: 実装済み変更に対する検証コマンドを実行し、結果と未検証範囲を報告する。implement 完了後のテスト、lint、typecheck、build に使う。
---

# test

repo-tracked file を変更せず、plan またはユーザーが指定した検証を実行して、結果と残リスクを `review` へ引き渡す。

## Workflow

`references/workflow.md` を読む。

## Output

- 実行したコマンドと結果
- 予期しない Git 状態や外部状態の変更
- 失敗したコマンドの原因分類と戻り先
- 未実行の検証と理由
- review が判断に使う残リスク
