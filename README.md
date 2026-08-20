# dotagents

`~/.agents` に配置して使う個人用 agent 設定と skills のリポジトリです。

## 構成

- `AGENTS.md`: 共通の agent 指示
- `skills/`: 自作スキルと `npx skills add -g` で導入した外部スキル
- `.skill-lock.json`: 外部スキルの取得元・更新情報。生成された場合は Git 管理する

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

`npx skills add -g` と `npx skills update -g` は `~/.agents/skills/` と `~/.agents/.skill-lock.json` を更新します。更新後は次を確認してからコミットします。

- `SKILL.md` が想定した内容か
- 外部参照、シェル実行、認証情報の扱いに問題がないか
- 自作スキルと名前が衝突していないか
- `.skill-lock.json` の source、ref、hash が意図したものか

外部スキルは信頼できるソースに限定し、導入したコードは agent 権限で実行され得ることを前提に扱います。
