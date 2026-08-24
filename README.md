# skills

`npx skills add` で導入する自作 skills のリポジトリです。
個人 AGENTS は補助設定であり、このリポジトリの配布物の必須依存ではありません。

## 自作 skills

| Skill | 用途 | 利用契機 |
|---|---|---|
| `branch` | 規約に沿う branch の作成 | branch 作成を明示的に依頼されたとき |
| `commit` | 安全な対象だけを commit | commit を明示的に依頼されたとき |
| `plan` | 実装内容と検証方針の計画 | 変更を実装する前 |
| `implement` | 計画に沿った最小変更の実装 | plan 完了後 |
| `test` | 検証コマンドの実行 | implement 完了後 |
| `research` | 事実確認と方針整理 | 調査・診断・実装前の確認時 |
| `review` | 差分のリスク確認 | コード・変更内容のレビュー時 |
| `grilling` | 要件・方針の確認 | 実装を左右する不明点があるとき |
| `merge-request` | GitHub PR / GitLab MR の作成 | PR/MR 作成を明示的に依頼されたとき |
| `self-improvement` | 会話からスキル改善候補を抽出し承認後に反映 | スキル改善を依頼されたとき |

## 標準フロー

通常の変更は `plan → implement → test → review` で進めます。各 skill は目的を絞り、前工程の結果は対象、変更内容、検証結果、残リスクの自然言語で引き渡します。

不足する事実は必要時のみ `research`、判断が必要な不明点は必要時のみ `grilling` に戻します。`self-improvement` は候補単位の明示承認後に標準フローで反映します。

## 導入前提

- `npx`: skill の導入・一覧・更新に必要です。
- `Git`: Git 状態や差分を扱う skill に必要です。
- `gh` / `glab` と対応する認証: `merge-request` に必要です。
- ネットワーク: 導入、remote 確認、PR/MR 操作、明示的に許可された外部調査に必要です。対象と送信内容を確認してから使用します。

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

導入後は `npx skills list -g` で source と導入先を確認できます。読み取り専用 smoke test を行う場合は、導入先を `SKILLS_DIR` に設定します。

```sh
SKILLS_DIR="<npx skills list -g で確認した導入先>"
for skill in branch commit plan implement test research review grilling merge-request self-improvement; do
  test -r "$SKILLS_DIR/$skill/SKILL.md" || exit 1
done
```

skills は agent 権限で実行され得るため、外部参照、シェル実行、認証情報の扱いを確認してから使用します。

`graphify-labs/graphify` は現在、Skills CLI が要求する `SKILL.md` ではなく生成用の
`graphify/skill-agents.md` を配布しているため、`npx skills add` の直接取得に対応していません。
upstream が対応した後は次で導入できます。

```sh
npx skills add -g graphify-labs/graphify --skill graphify
```
