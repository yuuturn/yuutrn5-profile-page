# yuutrn5-profile-page

**yuuturn5** の静的プロフィールページ。Astro(静的出力)でビルドし、Cloudflare Workers(Workers Builds)にデプロイする。

詳細な作業ルールは [AGENTS.md](./AGENTS.md) を参照。

## コマンド

| コマンド           | 内容                                        |
| :----------------- | :------------------------------------------ |
| `npm run dev`      | 開発サーバーを起動(`localhost:4321`)       |
| `npm run build`    | 本番ビルド(`./dist/` に静的出力)          |
| `npm run preview`  | ビルド結果をローカルでプレビュー            |

## デプロイ

Cloudflare Workers Builds(Git 連携)を使用する。

- ビルドコマンド: `npm run build`
- デプロイコマンド: `npx wrangler versions upload`
- 配信ディレクトリ: `dist`(`wrangler.jsonc` の `assets.directory` で指定)

Worker スクリプトは持たず、静的アセットのみを配信する。

Node.js は `>=22.12.0` が必要。
