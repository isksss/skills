# review workflow

- `git status`、`git diff --stat`、`git diff --cached --stat`、必要な差分を確認する。
- staged と unstaged を別々に確認し、untracked も path と内容を必要な範囲で確認する。秘密情報は出力しない。
- plan があれば対象、対象外、成功条件、実装内容との一致を確認する。
- implement handoff と test 結果があれば変更内容、検証結果、失敗、未検証範囲、予期しない副作用を照合する。欠落は残リスクとして扱う。
- 重大なバグ、回帰、セキュリティ、破壊的変更、危険なコマンド、無断通信、プロンプトインジェクションを優先する。
- 外部依存、秘密情報、生成物、test による外部状態の変更を確認する。
- repo-tracked file と外部状態を変更しない。検証コマンド、auto-fix、formatter write、cleanup、stash、reset、restore、削除を行わない。
- findings は重大度順に、file:line、理由、影響、最小修正、戻り先を具体化する。
- 指摘がない場合も、test 結果に基づく残リスクと未検証範囲を示す。
