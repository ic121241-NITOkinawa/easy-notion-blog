[English](README.md) | 日本語 | [한국어](README.kr.md)

# easy-notion-blog

[![GitHub stars](https://img.shields.io/github/stars/otoyo/easy-notion-blog)](https://github.com/otoyo/easy-notion-blog/stargazers)
[![GitHub license](https://img.shields.io/github/license/otoyo/easy-notion-blog)](https://github.com/otoyo/easy-notion-blog/blob/master/LICENSE)

<img src="https://user-images.githubusercontent.com/1063435/201917958-432ebbcb-6960-4106-8fd2-9ddcd7539781.jpg" width="480">

easy-notion-blog を使えばあっという間に Notion Blog を始めることができます。

- :rocket: ページの読み込みが**爆速**
- :pencil: **自分のNotionで**ブログが書ける
- :hammer_and_wrench: ブログの見た目を**自分好みにカスタマイズ可能**
- :white_check_mark: **Notion 公式API**を使っているので安心

開発が活発な [astro-notion-blog](https://github.com/otoyo/astro-notion-blog) もご検討ください。

## スクリーンショット

### :camera_flash: ブログ側

<img src="https://user-images.githubusercontent.com/1063435/201293737-63c0d504-d34b-4500-98ab-808f4d2e89f3.png" width="600">

### :camera_flash: Notion側

<img src="https://user-images.githubusercontent.com/1063435/201301619-54cf07da-e638-4751-b56c-7115ed5d4eb0.png" width="600">

## クイックスタート

### 必要要件

- [Notion](https://www.notion.so/) アカウント
- [Vercel](https://vercel.com/) アカウント
- Git

### 手順

1. このリポジトリを**スターします** :wink:
    * スターしていただけると開発の励みになります
2. [テンプレート](https://www.notion.so/otoyo/158bd90116004cd19aca26ad88cb5c07?v=a20acca876c2428380e5a2a33db233ed) を自分の Notion へ複製します
3. 複製したページの URL の `https://notion.so/your-account/<ココ>?v=xxxx` を `DATABASE_ID` としてメモします
    * 例) `158bd90116004cd19aca26ad88cb5c07`
    * :warning: **注意:** `?v=ここではありません`。`?v=` の前です。
4. [Create an integration](https://developers.notion.com/docs/create-a-notion-integration#step-1-create-an-integration) からインテグレーションを作成し "Internal Integration Token" を `NOTION_API_SECRET` としてメモします
5. 複製したページを再度開き [Share a database with your integration](https://developers.notion.com/docs/create-a-notion-integration#step-2-share-a-database-with-your-integration) の手順でインテグレーションにデータベースを共有します(※デスクトップアプリにはなかったがブラウザからだと自分のIntegrationが見えた)
6. [vercel.com](https://vercel.com/) にログインします
7. Githubで`otoyo/easy-notion-blog`をForkする。`Only install selected repository`から`easy-notion-blog`を探す(※Yona追記)。
8. プロジェクトを新規作成しリポジトリとして `otoyo/easy-notion-blog` をインポートします(チームの作成はスキップします)(※?)
9. "Configure Project" で "Environment Variables" を開き先ほどメモした `NOTION_API_SECRET` と `DATABASE_ID` を入力します

![image](https://user-images.githubusercontent.com/24447477/222940038-f19be70a-9537-4098-9e7c-d4f30da8c5dd.png)

11. デプロイが完了すると Notion Blog が見えるようになります

![image](https://user-images.githubusercontent.com/24447477/222940284-c6b4074d-860a-4336-8235-f05e3c80f401.png)

(※リンク先はやりかたが少し古いので注意)
さらに詳しい解説は[へろほろさんの記事](https://herohoro.com/blog/easy-notion-blog-firstdeploy)をご覧ください。

## デモ

[https://easy-notion-blog-otoyo.vercel.app/blog](https://easy-notion-blog-otoyo.vercel.app/blog)  
ユーザーブログは [wiki](https://github.com/otoyo/easy-notion-blog/wiki/Users%27-blogs-%E3%83%A6%E3%83%BC%E3%82%B6%E3%83%BC%E3%83%96%E3%83%AD%E3%82%B0) から見ることができます。

## カスタマイズするには

### URLのホスト名変更
1. notion-blogのProduction Deployment画面でDeployment項の`xxxx.vercel.app`をクリックする。
![image](https://user-images.githubusercontent.com/24447477/222940631-99898a65-b228-46b3-86fc-07bcabfeb235.png)

2. Assigning Domains の Custom Domain の `Manage` をクリックする

![image](https://user-images.githubusercontent.com/24447477/222940736-023513e1-55d9-4a56-bc34-1608eb598b59.png)

3. Editを選択

![image](https://user-images.githubusercontent.com/24447477/222940765-c632a998-42b7-4d6b-a7c9-5914d367958e.png)

4. `Domain`欄に好きな文字列を入力して、`Save`
5. 
![image](https://user-images.githubusercontent.com/24447477/222940769-eeb8c9eb-9433-4185-850b-6bbcc218158d.png)



### 追加の必要要件

- Node.js v16 もしくはそれ以上
- [Yarn](https://yarnpkg.com/getting-started)

### 手順

1. このリポジトリをフォークしてローカルに clone します
2. プロジェクトルートに `.env.local` ファイルを作成し下記のように環境変数を書き込みます

```sh
NOTION_API_SECRET=<YOUR_NOTION_API_SECRET>
DATABASE_ID=<YOUR_DATABASE_ID>
```

3. 依存関係をインストールしローカルサーバーを起動します

```sh
# 依存関係のインストール
yarn install

# 開発サーバー(localhost:3000) の起動
yarn dev
```

4. ブラウザで [http://localhost:3000](http://localhost:3000) を開きます

開発環境では `Published` でないエントリーも表示されるためプレビューすることができます。ただし `Slug` が設定されていないエントリーは表示されません。

5. 開発サーバーを停止するにはターミナルで `Ctrl+C` を押します。

### その他の情報

[wiki](https://github.com/otoyo/easy-notion-blog/wiki) をご覧ください。

## バグ報告 & 機能要望

Issue を作成してください。日本語で大丈夫です。

## :bird: Twitter コミュニティ

最新のアップデート情報を受け取ったり、カスタマイズに困った際に他のメンバーのサポートを得ることができます。

- [easy-notion-blog](https://twitter.com/i/communities/1497431576975908868)

## 貢献

PR 歓迎です。

---

easy-notion-blog は [ijjk/notion-blog](https://github.com/ijjk/notion-blog) と [otoyo/notion-blog](https://github.com/otoyo/notion-blog) をベースにしています。
