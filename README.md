# dotagents

`~/.agents` に配置して使う個人用 agent 設定と skills のリポジトリです。

## 構成

- `AGENTS.md`: 共通の agent 指示
- `skills/`: 自作スキルと `npx skills add -g` で導入した外部スキル

## 汎用 skills

| Skill | 用途 | 利用契機 |
|---|---|---|
| `branch` | 規約に沿う branch の作成 | branch 作成を依頼されたとき |
| `commit` | 安全な対象だけを commit | commit を明示的に依頼されたとき |
| `plan` | 実装内容と検証方針の計画 | 変更を実装する前 |
| `implement` | 計画に沿った最小変更の実装 | plan 完了後 |
| `test` | 検証コマンドの実行 | implement 完了後 |
| `research` | 事実確認と方針整理 | 調査・診断・実装前の確認時 |
| `review` | 差分のリスク確認 | コード・変更内容のレビュー時 |
| `grilling` | 要件・方針の確認 | 実装を左右する不明点があるとき |
| `merge-request` | GitHub PR / GitLab MR の作成 | PR/MR 作成を明示的に依頼されたとき |

## 開発フロー

標準フローは `research / grilling → plan → implement → test → review` です。小さな変更でも工程を省略せず、各工程を簡略化します。

- `plan`: 対象ファイル、変更手順、テストコードの要否、検証コマンド、リスクを決める
- `implement`: plan の範囲だけを編集する。テストコードの追加・修正もここで行う
- `test`: lint、typecheck、test、build などを実行し、結果と未検証範囲を記録する
- `review`: plan、差分、test 結果を読み取り、不具合・回帰・セキュリティ・互換性を確認する

test の失敗は `implement → test`、review の指摘は `implement → test → review` に戻します。計画変更が必要な場合は `plan` からやり直します。

## 導入

既存の `~/.agents` を退避または削除したうえで clone します。

```sh
mv ~/.agents ~/.agents.backup
git clone <dotagents-repository-url> ~/.agents
```

このリポジトリを `~/.agents` 以外へ clone する場合、global skill の配置先と一致しないため、外部スキル管理の正本にはなりません。

## 自作スキル

自作スキルは `skills/<name>/SKILL.md` を正本とします。変更後は frontmatter、参照ファイル、対象 agent での利用可否を確認します。

## 外部スキル

外部スキルは導入元を確認し、内容をレビューしてから global install します。

```sh
npx skills add -g <owner>/<repo> --skill <name>
npx skills list -g
npx skills update -g
```

`npx skills add -g` と `npx skills update -g` は `~/.agents/skills/` を更新します。更新後は次を確認してからコミットします。

- `SKILL.md` が想定した内容か
- 外部参照、シェル実行、認証情報の扱いに問題がないか
- 自作スキルと名前が衝突していないか

外部スキルは信頼できるソースに限定し、導入したコードは agent 権限で実行され得ることを前提に扱います。
