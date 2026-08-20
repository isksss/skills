---
name: test
description: 実装済み変更に対する検証コマンドを実行し、結果と未検証範囲を報告する。implement 完了後のテスト、lint、typecheck、build に使う。
---

# test

repo-tracked file を変更せず、plan に定めた検証を実行して review に引き渡す。

## Workflow

`references/workflow.md` を読む。

## Output

- 実行したコマンドと結果
- 失敗したコマンドの原因分類
- 未実行の検証と理由
- review が判断に使う残リスク
