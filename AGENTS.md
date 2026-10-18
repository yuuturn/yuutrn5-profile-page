# AGENTS.md

## 言語

ユーザーとのやり取りは**必ず日本語で行うこと**(コード・コミットメッセージは英語可)。

## プロジェクト

**yuuturn5** の静的プロフィールページ。

スタック: **Astro**(静的出力)。Node.js `>=22.12.0` が必要。
Node バージョンは `.node-version`(22.23.1)で固定しており、Cloudflare Workers Builds のビルド環境にも適用される。Node を更新する際は `.node-version` も忘れずに更新すること。
GitHub リポジトリ: https://github.com/yuuturn/yuutrn5-profile-page (public、デフォルトブランチ `main`)

## 確定済みの決定事項(再議論しない)

- ホスティング: **Cloudflare Workers**(Workers Builds の Git 連携でビルドし、静的アセットとして配信する。GitHub Pages は使わない)。
- スタック: 静的サイトジェネレータ。**Astro**(採用済み)。
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
- Cloudflare Workers Builds 設定: ビルドコマンド `npm run build`、デプロイコマンド `npx wrangler versions upload`。配信ディレクトリは `wrangler.jsonc` の `assets.directory`(`./dist`)で指定する。

## favicon

- 正は `public/favicon.svg`(モダンブラウザ用)。`public/favicon.png` は Safari 用フォールバックで、SVG から生成した PNG。
- `favicon.ico` は廃止済み。SVG + PNG の2本立てで運用する。
- PNG の再生成手順: `qlmanage -t -s 512 -o <dir> public/favicon.svg` で 512px の PNG を生成し、`sips -Z 180` で 180px に縮小して `public/favicon.png` に置き換える。

## ブランチ戦略

- **Conventional Branch** 形式でブランチを切り出す(例: `feature/add-ogp`、`fix/meta-description`)。プレフィックスは Conventional Commits の type に準拠(`feature/`、`fix/`、`docs/`、`chore/`、`refactor/` など)。
- `main` に直接 commit/push はしない。作業は必ずブランチ上で行い、push 後 `gh pr create` で PR を作成する。
- **マージはユーザーが行う**。エージェントはマージや `main` への直接 push をしない。PR 作成後はレビューを待つ。

## 本番環境

- カスタムドメイン: **https://profile.yfujii.net**(第一 URL)
- workers.dev: https://yuutrn5-profile-page.yuuturn5.workers.dev
- `main` への push で Cloudflare Workers Builds が自動ビルド・デプロイする(Git 統合)。
