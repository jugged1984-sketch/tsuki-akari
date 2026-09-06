# Winebar Tsuki-akari 公式サイト

東京・湯島のワインバー **Winebar Tsuki-akari** の公式サイト初期版です。既存の WordPress とは独立した、HTML / CSS / JavaScript のみの静的サイトです。

## ファイル構成

```text
.
├── index.html           # ページ本文、SEO / OGP メタ情報
├── styles.css           # デザイン、レスポンシブ対応
├── script.js            # モバイルメニュー、スクロール演出
└── assets/
    ├── favicon.svg      # 仮ファビコン
    └── og-image.svg     # 仮OGP画像（公開前に写真/JPG推奨）
```

## ローカルで確認する

リポジトリのルートで次を実行し、`http://localhost:8000` を開きます。

```bash
python3 -m http.server 8000
```

## GitHub Pages で公開する

1. GitHub のリポジトリ画面で **Settings → Pages** を開く。
2. **Build and deployment** の Source に `Deploy from a branch` を指定する。
3. 対象ブランチと `/(root)` を選び **Save** する。
4. 表示された公開URLで確認する。

ルート相対パスを使っていないため、プロジェクトサイトのサブディレクトリでも表示できます。なお、canonical / OGP のURLは本番ドメインを指定しています。

## Xserver へ移行する

1. 公開前チェックを完了し、リポジトリ内のファイルを取得する。
2. `index.html`、`styles.css`、`script.js`、`assets` ディレクトリを構造を保ったまま `public_html` へ配置する。
3. 既存 WordPress から切り替える際は、必ずバックアップを取得し、ステージングまたは別ディレクトリで表示を確認する。
4. キャッシュ、HTTPS、canonical / OGP画像のURLを本番環境で確認する。

> この制作では既存 WordPress に変更を加えていません。実際の切り替え作業は本サイトの内容確定後に行ってください。

## 公開前に設定・確認が必要な項目

推測情報を公開しないため、以下は意図的に「要確認」または仮リンクとしています。

- **店舗情報**：住所、営業時間、定休日、電話番号、アクセス、席数、支払方法
- **予約**：オンライン予約先URL、電話番号（`tel:`リンク）
- **外部リンク**：Instagram、山崎翔 Official Website
- **メニュー**：メニューページまたはPDFへのリンク（追加する場合）
- **OGP**：`assets/og-image.svg` は仮画像。SNS互換性のため、公開前に 1200 × 630 px の JPG / PNG へ差し替え、メタタグの拡張子も変更推奨
- **Google Fonts**：外部通信を避ける場合はフォントをセルフホストするか、`styles.css` の `@import` を削除してシステムフォントを使用

未確定リンクには `TODO` コメント、未確認の店舗情報にはHTMLコメントを記載しています。

## 差し替える画像

写真がなくても成立するダークトーンのプレースホルダーを実装しています。写真確定後は以下を差し替えてください。

1. **HERO**：`.hero-art` 内または `.hero` の背景に店内のキービジュアルを設定
2. **WINE & FOOD**：`.wine-visual` を画像要素に差し替え
3. **SOMMELIER**：`.portrait-placeholder` を山崎翔氏の正式なポートレートに差し替え
4. **GALLERY**：各 `.gallery-placeholder` を、適切な `alt` を持つ `<img>` に差し替え（項目の複製で追加可能）
5. **OGP**：`assets/og-image.svg` を正式なブランド画像へ差し替え

画像は WebP（必要に応じて JPEG フォールバック）、目安幅 1600〜2400 px、適切な圧縮を推奨します。被写体に応じた代替テキストを必ず設定してください。
