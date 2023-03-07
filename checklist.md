# 上級者チーム開発 - チェックリスト

## 概要
チーム開発を進める中で達成すべき内容。

下記は**一周目**に達成すべき事項
### 1. 必ず週2回全メンバーが集まれる時間を決めて、ミーティングを行う

<br />

### 2. 課題の要件定義（requirements）をまとめる
追記する内容として、
1. 目的
2. 機能要件:「実装する機能」に関する要件
3. 非機能要件: アプリの性能など「実装する機能以外」に関する要件

例:

![Screenshot 2023-02-26 at 14 44 08](https://user-images.githubusercontent.com/45121253/221394469-798c80fb-bbba-4164-97f5-523dbf77ccd5.png)

<br />

### 3. チームメンバーと Git の[管理の仕方](https://github.com/recursion-team-v/team-v-devlog/blob/main/github_tutorial.md)を共有し、Organization と レポジトリを作成する

<br />

### 4. 最低限の開発環境を構築する
- 使用する言語
- 使用するフレームワーク（Vue、React など）
- 使用する CI (husky、github actions など）
- Linter とコードフォーマッターの設定（eslint、prettier など）
- 使用する API、ライブラリなど（候補でもOK）

<br />

### 5. deploy 環境を決める
- フロントエンドは Vercel、Netlify など
- バックエンドは Google Cloud Run、AWS、Render など

### 6. ワイヤーフレームを作成する
- ワイヤーフレームとは、WEBサイト・アプリなどを制作する上で各ページごとに必要な要素を整理したものです
- ワイヤーフレームで実際に基本的なUI要素のデザインをしてみて、完成イメージを「見える化」できます
- [Figma](https://www.figma.com) だと様々な（tailwindcss, materialUI などの）コンポーネントやUI要素が事前に用意されています

例:

<img width="1444" alt="Screenshot 2023-03-07 at 16 49 39" src="https://user-images.githubusercontent.com/45121253/223359870-afe1e4ec-2be7-47c1-9d78-779f9b5e15c9.png">

<br />

### 7. 技術スタックの構成図
- 使用予定の技術スタックをビジュアル化する
- 下書きでも良い、後ほど変更を加える

例:

![architecture drawio](https://user-images.githubusercontent.com/45121253/221457716-2e6b952d-7d92-49be-9c02-538d7969d1f7.png)

参考リンク
- [VSCodeで draw.io を使ってフローチャートやネットワーク図を作る](https://qiita.com/riku-shiru/items/5ab7c5aecdfea323ec4e)

<br />

### 8. クラス・アクティビティ図
- クラス図: システムを構成するクラスとそれらの関係を表現する
- アクティビティ図: 連続する「実行」の遷移、つまり一連の ｢手続き｣ を表現する

クラス図の例:

![class_diagram](https://user-images.githubusercontent.com/45121253/223355327-e679bc24-bd5e-4830-833c-8ffb70f203c9.png)

アクティビティ図の例:

![activity_diagram](https://user-images.githubusercontent.com/45121253/223055482-8b875d4f-0632-4778-8b7c-0ebae904e3b5.png)

<br />

また、開発を進める中で、
### 9. 毎週末にその週行った作業をまとめて全チームと共有する
レポジトリに ```dev-log.md``` を作成し、毎週末更新する。
内容としては、
1. やったこと
 - その週に実装した内容
2. 苦労していること（直面した問題）
 - その週に苦労・直面した問題
 - 解決できた場合その解決策も追記する
3. 今後の課題
 - 次週までに達成する内容・機能

例:

![Screenshot 2023-02-26 at 15 04 02](https://user-images.githubusercontent.com/45121253/221395047-6684e758-501a-4fbd-ac88-791fb3f054f4.png)
