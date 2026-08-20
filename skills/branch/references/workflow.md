# branch workflow

- Git リポジトリ内であることを確認する。
- 現在の branch と `git status --porcelain` を確認する。
- 作業目的を2、3語の短い英語またはローマ字にする。
- 形式は `{gitflow}/{summary}_{yyyymmdd}` を基本にする。
- gitflow は feature、bugfix、hotfix、release から選ぶ。
- `git branch -a` でローカルと remote-tracking branch の重複を確認する。最新状態が必要なら `git fetch --prune` を実行し、実行できない場合は確認範囲を明示する。
- 既存 branch と重複する場合は要約を調整する。
- 現在の HEAD から `git switch -c "${branch}"` で branch を作成する。
- `git branch --show-current` で作成した branch に切り替わったことを検証する。
- 作成した branch 名を伝える。
