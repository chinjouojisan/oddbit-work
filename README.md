# Oddbit Work

未知の断片に出会い、意外性のあるラインを生成する日課アプリ。
単一の静的サイト(HTML/CSS/JS)で動作する、インストール可能なPWAです。

## ファイル構成

```
oddbit-work-site/
├── index.html          アプリ本体
├── manifest.json        PWA設定(アイコン・アプリ名など)
├── service-worker.js     オフラインキャッシュ
├── icons/
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

データ(FEEDBACKの一行ログ、ゴーストグリッドに追加した当せん番号)は
すべてブラウザの `localStorage` に保存されます。サーバーには送信されません。
端末・ブラウザが変わると別データになる点にご注意ください。

## GitHub Pagesで公開する手順

1. GitHubで新しいリポジトリを作成する(例: `oddbit-work`)
2. このフォルダの中身一式(index.html, manifest.json, service-worker.js, icons/, README.md)を
   リポジトリのルートに置いてpushする

   ```bash
   cd oddbit-work-site
   git init
   git add .
   git commit -m "Oddbit Work v1"
   git branch -M main
   git remote add origin https://github.com/chinjouojisan/oddbit-work.git
   git push -u origin main
   ```

3. GitHubのリポジトリページで **Settings → Pages** を開く
4. "Build and deployment" の Source を **Deploy from a branch** にする
5. Branch を **main** / フォルダを **/(root)** にして Save
6. 数分待つと `https://chinjouojisan.github.io/oddbit-work/` で公開されます

以降は、内容を変更してpushするたびに自動で反映されます。

## スマホのホーム画面に追加する(PWAとして使う)

公開後、スマホのブラウザで上記URLを開き、
- iOS Safari: 共有ボタン →「ホーム画面に追加」
- Android Chrome: メニュー →「ホーム画面に追加」/「アプリをインストール」

これでアイコンからアプリのように起動できます。

## 注意点

- `manifest.json` の `start_url` / `scope` は `./` (相対パス)にしてあるので、
  リポジトリ名のサブパス(`/oddbit-work/`)配下でもそのまま動きます。
- 独自ドメインを使う場合は、リポジトリの Settings → Pages で
  Custom domain を設定してください。
