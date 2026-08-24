# skills

`npx skills add` で導入する自作 skills のリポジトリです。
共通の agent 指示は `~/dotfiles/.agents/AGENTS.md` で管理します。

## 自作 skills

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

## 導入

```sh
npx skills add -g isksss/skills --all
npx skills list -g
npx skills update -g
```

特定の skill だけ導入する場合:

```sh
npx skills add -g isksss/skills --skill plan
```

## 外部 skills

外部 skills はこのリポジトリにコピーせず、導入元から直接追加します。

```sh
npx skills add -g anomalyco/opencode --skill effect rtl-aware-development
npx skills add -g herdrdev/herdr --skill herdr herdr-pre-release-audit herdr-throwaway-repro triage
```

導入後は `npx skills list -g` で source と導入先を確認します。skills は agent 権限で実行され得るため、
外部参照、シェル実行、認証情報の扱いを確認してから使用します。

`graphify-labs/graphify` は現在、Skills CLI が要求する `SKILL.md` ではなく生成用の
`graphify/skill-agents.md` を配布しているため、`npx skills add` の直接取得に対応していません。
upstream が対応した後は次で導入できます。

```sh
npx skills add -g graphify-labs/graphify --skill graphify
```
