# AGENTS.md

## 言語

ユーザーとのやり取りは**必ず日本語で行うこと**(コード・コミットメッセージは英語可)。

## プロジェクト

**yuuturn5** の静的プロフィールページ。

スタック: **Astro**(静的出力)。Node.js `>=22.12.0` が必要。
GitHub リポジトリ: https://github.com/yuuturn/yuutrn5-profile-page (public、デフォルトブランチ `main`)

## 確定済みの決定事項(再議論しない)

- ホスティング: **Cloudflare Pages**(GitHub Pages は使わない)。
- スタック: 静的サイトジェネレータ。**Astro** を第一候補とする。
- 出力は完全に静的であること。サーバーサイドランタイムは使わない。

## ハンドル名の罠

SNS ハンドルは `yuuturn5` だが、GitHub のユーザー名は **`yuuturn`**(`5` なし)。リンクやデプロイ設定で混同しないこと。

## プロフィール内容(単一の情報源)

- X (Twitter): https://x.com/yuuturn5
- Bluesky: https://bsky.app/profile/yuuturn5.yfujii.net (`yfujii.net` 配下のカスタムドメイン)
- GitHub: https://github.com/yuuturn
- ブログ(はてなブログ): https://yuuturn0422.hatenablog.jp/

## コマンド

- dev: `npm run dev`(フォアグラウンド)/ `npx astro dev --background` でバックグラウンド起動。後者は `npx astro dev stop|status|logs` で管理する。
- build: `npm run build` → `dist/` に完全静的出力。
- preview: `npm run preview`。
- Cloudflare Pages 設定: ビルドコマンド `npm run build`、出力ディレクトリ `dist`。

## ブランチ戦略

- **Conventional Branch** 形式でブランチを切り出す(例: `feature/add-ogp`、`fix/meta-description`)。プレフィックスは Conventional Commits の type に準拠(`feature/`、`fix/`、`docs/`、`chore/`、`refactor/` など)。
- `main` に直接 commit/push はしない。作業は必ずブランチ上で行い、push 後 `gh pr create` で PR を作成する。
- **マージはユーザーが行う**。エージェントはマージや `main` への直接 push をしない。PR 作成後はレビューを待つ。

## 本番環境

- カスタムドメイン: **https://profile.yfujii.net**(第一 URL)
- workers.dev: https://yuutrn5-profile-page.yuuturn5.workers.dev
- `main` への push で Cloudflare Pages が自動ビルド・デプロイする(Git 統合)。
