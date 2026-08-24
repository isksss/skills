---
name: commit
description: 現在の Git 差分を確認して安全な対象だけを stage し、日本語 prefix 付きメッセージで commit する。ユーザーが commit を明示的に依頼したときに使う。
---

# commit

ユーザーが commit を明示的に依頼した場合だけ使う。開始時点の staged baseline を保護し、秘密情報、生成物、無関係差分、非信頼入力を commit に持ち込まない。確認できない副作用がある場合は停止する。

## Workflow

`references/workflow.md` を読む。
