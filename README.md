# Winebar Tsuki-akari 公式サイト

東京・湯島のワインバー **Winebar Tsuki-akari** の静的サイトです。HTML / CSS / JavaScriptで構成され、ビルドやパッケージのインストールは不要です。既存のWordPressとは独立した構成です。

このREADMEはリポジトリ内の実装を説明します。公開サーバーへの反映状況を示すものではありません。

## ファイル構成

```text
.
├── index.html           # トップページ、SEO・OGP情報
├── menu/
│   └── index.html       # メニュー・税込価格一覧
├── styles.css           # 両ページ共通のデザイン・レスポンシブ対応
├── script.js            # モバイルナビ、スクロール演出、年表示
├── CNAME                # GitHub Pages用ドメイン指定
├── README.md
└── assets/
    ├── counter-hero-*.webp   # ファーストビュー用2サイズ
    ├── concept-*.webp        # コンセプト写真
    ├── wine-food-*.webp      # Wine & Food写真
    ├── sommelier-*.webp      # ソムリエ紹介のサービス写真
    ├── gallery-*.webp        # ギャラリー3枚
    ├── entrance-*.webp       # 店舗外観
    ├── favicon.svg          # 月をモチーフにしたアイコン
    ├── og-image.svg         # 初期の仮OGP画像（現在は未参照）
    └── *.jpeg / *.jpg       # 元写真・保管画像
```

## ページ構成

### トップページ `/`

次の11セクションで構成しています。

1. ファーストビュー（`#top`）
2. Concept／店のコンセプト（`#concept`）
3. Wine & Food・料金（`#wine`）
4. First Visit／初めての方への案内（`#first-visit`）
5. Sommelier／山崎翔の紹介（`#sommelier`）
6. Gallery（`#gallery`）
7. Instagram（`#instagram`）
8. FAQ（`#faq`）
9. Information／ご利用案内（`#guest-information`）
10. Access／店舗情報・アクセス（`#information`）
11. 予約・お問い合わせ（`#reservation`）

旧Our Philosophy・ExperienceはConceptとFirst Visitへ、旧Wine SelectionはWine & Foodへ統合済みです。Wine & Foodには英語アクセント「Selection / By the Glass / Pairing」、チャージ・グラスワインの価格、詳細メニューへのリンクがあります。

トップのナビでは、Menuが`menu/`、Accessが店舗情報、Informationがご利用案内へ移動します。

### メニューページ `/menu/`

チャージ、グラスワイン、ビール、ウイスキー、前菜、パスタ、デザートの税込価格と注意事項を掲載しています。共通のCSS・JavaScriptを使用します。

## デザイン・機能

- 黒・アイボリー・ゴールドを基調に、明朝系の書体と店舗写真を使用。
- 画面幅820px以下でモバイルナビに切り替え。
- `script.js`でナビの開閉、スクロール時のヘッダー変化、要素の表示演出、著作権年の自動更新を実装。
- FAQはHTML標準の`details` / `summary`による開閉式。
- 両ページに一休.comへ移動する予約追従ボタンを設置。
- トップの予約欄には一休.com、食べログ、電話のリンクを設置。サイト内で予約を処理するフォームやバックエンドはありません。
- InstagramはElfsightの外部ウィジェットで表示。

## 画像の使い分け

トップの写真8枚はWebPを使用しています。元JPEGは削除・上書きせず保管しています。

| 用途 | 使用ファイル（`assets/`内） | 選択方法 |
|---|---|---|
| ファーストビュー | `counter-hero-pc.webp`（3840×2560）／`counter-hero-mobile.webp`（2880×1920） | CSSで821px以上はPC用、820px以下はスマホ用 |
| コンセプト | `concept-1080.webp`／`concept-1920.webp` | `srcset`・`sizes` |
| Wine & Food | `wine-food-1280.webp`／`wine-food-2000.webp` | `srcset`・`sizes` |
| ソムリエ紹介 | `sommelier-1280.webp`／`sommelier-2000.webp` | `srcset`・`sizes` |
| ギャラリー：席 | `gallery-space-800.webp`／`gallery-space-1200.webp` | `srcset`・`sizes` |
| ギャラリー：ワイン | `gallery-wine-800.webp`／`gallery-wine-1200.webp` | `srcset`・`sizes` |
| ギャラリー：料理 | `gallery-pairing-800.webp`／`gallery-pairing-1200.webp` | `srcset`・`sizes` |
| 外観 | `entrance-1440.webp`／`entrance-2400.webp` | `srcset`・`sizes` |

ファーストビュー以外のファイル名の数字は画像の横幅（px）です。7枚の`img`は遅延読み込みを使用し、画面幅・画素密度などに応じてブラウザーが解像度を選びます。PC／スマホで必ず同じファイルが選ばれる設定ではありません。

トリミングは既存CSSの`background-size: cover`、`object-fit: cover`と位置指定で行います。一部の`sizes`は縦長の表示枠へ横写真を切り抜く際の解像度を考慮しています。画像だけを差し替える場合も、表示枠と元画像の縦横比に注意してください。

トップのSNS共有用OGP・Twitter画像は、WebPとは別に元の`assets/カウンター.jpeg`を参照しています。`og-image.svg`は現在使用していません。

## 外部サービス・SEO

- 予約：[一休.com](https://restaurant.ikyu.com/154130/)
- 店舗掲載：[食べログ](https://tabelog.com/tokyo/A1310/A131004/13314758/)
- SNS：[Instagram](https://www.instagram.com/tsukiakari.winebar/)
- 人物紹介：[Sho Yamazaki Official Website](https://jugged1984-sketch.github.io/sommelier-yamazaki/)
- フォント：Google FontsのCormorant Garamond、Noto Serif JPをCSSから読み込み。
- Instagram埋め込み：`https://elfsightcdn.com/platform.js`。投稿画像の配信は外部サービス側で管理。

両ページにtitle・description・canonicalを設定し、トップにはOGP・Twitterカード情報を設定しています。canonicalの指定先は`https://tsuki-akari.tokyo/`と`https://tsuki-akari.tokyo/menu/`です。`CNAME`も`tsuki-akari.tokyo`を指定しています。

外部フォントやInstagramの表示にはインターネット接続が必要です。

## ローカルで確認する

Python 3が使用できる環境では、リポジトリのルートで次を実行します。

```bash
python3 -m http.server 8000
```

Windowsでは、Pythonのインストール方法に応じて`py -m http.server 8000`または`python -m http.server 8000`を使用します。

- トップ：`http://localhost:8000/`
- メニュー：`http://localhost:8000/menu/`

これは確認用サーバーです。Pythonはサイトの公開・動作には必要ありません。

## 公開・配置

### GitHub Pages

リポジトリのSettings → Pagesで、ブランチからの公開と対象ブランチの`/(root)`を指定する構成です。独自ドメインを使用する場合は、Pages設定・DNS・HTTPSを実際の公開先に合わせて確認してください。`CNAME`だけでDNS設定が完了するわけではありません。

内部のCSS・JavaScript・画像・ページリンクは相対パスです。別URLで公開する場合は、canonical・OGP・CNAMEの本番ドメイン指定も確認してください。

### Xserverなどの静的ファイルを配置できるサーバー

以下をディレクトリ構造を保ったまま公開ディレクトリ（例：`public_html`）へ配置します。

- `index.html`
- `menu/index.html`
- `styles.css`
- `script.js`
- `assets/`（WebP、元JPEG、ファビコンを含む）

`CNAME`はGitHub Pages向けの設定です。既存WordPressから切り替える場合は、バックアップを取り、別ディレクトリ等で確認してから公開先を切り替えてください。旧URLやサーバーのルーティング設定も確認が必要です。

## 更新時の確認

- 料金は`menu/index.html`とトップの料金案内で整合させる。
- 店舗情報・予約リンク・外部リンクは実際の運用内容と照合する。
- CSSを更新した場合は、両HTMLのCSS参照にある`?v=`も必要に応じて更新する。
- 画像の`src`・`srcset`、CSS背景画像、SNS共有画像の参照先を確認する。
- PC・スマホで写真の見え方、ナビ、FAQ、予約追従ボタン、Instagramを確認する。

画像参照や内部リンクの静的チェックは実施済みですが、画像最適化後の実ブラウザーでの表示・通信確認は未実施です。
