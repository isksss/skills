---
name: review
description: plan、Git 差分、test結果を読み取り専用でレビューし、不具合、回帰、セキュリティ、破壊的変更、検証不足を重大度順に指摘する。実装後の最終確認に使う。
---

# review

変更せず、findings first で具体的な修正方針を示す。plan、implement handoff、test 結果があれば差分と照合し、ない場合は未検証範囲として報告する。検証コマンドは `test` に委譲する。

## Workflow

`references/workflow.md` を読む。

## Output

- findings を重大度順に、`file:line`、理由、影響、最小修正、戻り先つきで報告する
- 指摘がない場合も、検証結果、残リスク、未検証範囲を示す
