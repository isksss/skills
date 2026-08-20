# merge-request workflow

- 現在 branch、未コミット差分、remote、ホスティングを確認する。
- main、master、develop など主要 branch からの作成は止める。
- GitHub は `gh`、GitLab は `glab` を使う。
- 派生元 branch を履歴から推定し、不明なら確認する。
- PR/MR 本文はテンプレートがあれば尊重する。
- コミット履歴と変更内容を要約して作成する。
- 外部スキルを含む場合は、取得元、更新内容、ライセンス、実行リスクを本文に明記する。
- push が必要なら対象 remote と branch を確認して `git push --set-upstream` を実行する。
- GitHub は `gh pr create`、GitLab は `glab mr create` で作成する。
- 作成後に URL、番号、base、head を確認し、作成結果を報告する。
- 作成できない場合は、実行したコマンド、原因、未完了の作業を明示する。
