---
name: merge-request
description: 現在 branch の差分と履歴を確認し、GitHub PR または GitLab MR を作成する。ユーザーが PR/MR 作成を明示的に依頼したときに使う。
---

# merge-request

ユーザーの明示的な依頼がある場合だけ、対象 repository、base、head を確認して GitHub PR または GitLab MR を作成する。push/create 前に安全性を確認し、確認できない場合は停止して理由を報告する。

## Workflow

`references/workflow.md` を読む。
