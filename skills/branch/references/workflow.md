# branch workflow

- `git rev-parse --is-inside-work-tree` が `true` を返すこと、および有効な HEAD を確認する。
- 現在の branch と `git status --porcelain` を確認する。dirty worktree は既定で停止し、明示承認がある場合だけ引き継ぐ。自動 commit、stash、restore、破棄は行わない。
- 作業目的を2、3語の短い英語またはローマ字にする。
- 形式は `{gitflow}/{summary}_{yyyymmdd}` を基本にする。
- gitflow は feature、bugfix、hotfix、release から選ぶ。
- 作成する branch 名を `git check-ref-format --branch "${branch}"` で検証する。
- `git branch -a` でローカル branch と remote-tracking ref の重複を確認する。ref が競合する場合は branch 名を調整して再検証し、解消できなければ作成を停止する。
- remote の最新状態が必要な場合だけ、外部通信を確認して `git ls-remote` で確認する。失敗時は確認できた範囲と通信失敗を報告する。
- 既存 branch と重複する場合は要約を調整する。
- 現在の HEAD から `git switch -c "${branch}"` で branch を作成する。
- `git branch --show-current` と `git rev-parse --verify HEAD` で作成結果を検証する。
- 作成した branch 名、worktree の確認結果、remote 確認の有無、通信失敗の有無を報告する。
