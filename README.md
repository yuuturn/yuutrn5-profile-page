# yuutrn5-profile-page

**yuuturn5** の静的プロフィールページ。Astro(静的出力)でビルドし、Cloudflare Pages にデプロイする。

詳細な作業ルールは [AGENTS.md](./AGENTS.md) を参照。

## コマンド

| コマンド           | 内容                                        |
| :----------------- | :------------------------------------------ |
| `npm run dev`      | 開発サーバーを起動(`localhost:4321`)       |
| `npm run build`    | 本番ビルド(`./dist/` に静的出力)          |
| `npm run preview`  | ビルド結果をローカルでプレビュー            |

## デプロイ

Cloudflare Pages を使用。

- ビルドコマンド: `npm run build`
- 出力ディレクトリ: `dist`

Node.js は `>=22.12.0` が必要。
