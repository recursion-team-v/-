# 上級者チーム開発 - Git を使った開発の流れ

## 概要

チーム開発で Git を活用する上で効率よく作業を進められるよう、git-flow のルールをベースとしてリポジトリを管理し、主な作業の流れとしては:
1. Issue を作って課題のタスク分けを行う
2. Issue に対してその機能追加用の ```feature``` ブランチを ```develop``` から切る
3. 開発終了後、```develop``` へプルリクを作成する
4. 最低一人のメンバーにプルリクに対するレビューをしてもらい、その後 ```develop``` へマージする

---

## 1. git-flow とは？

git-flow とは Git におけるリポジトリの分岐モデルであり、ルールのことを指します。
それぞれのブランチを明確に定義し、複数人での開発時にそれぞれが好き勝手にブランチを作成し混乱することを防ぎます。

下図はその概念図です。

![GitFlow-1200wi](https://user-images.githubusercontent.com/45121253/220487052-5c6afa1b-d283-4b55-b00b-74994aac8da1.png)

一般的に使用する各ブランチの定義は、

```main (master)```: リリース用のブランチであり、このブランチ上での作業は行わない

```develop```: 開発用のブランチであり、コードが安定し、リリースへの準備ができたら ```main``` へマージする

```feature```: 機能追加用のブランチであり、```develop``` から分岐し、```develop``` へマージする

---

## 2. Git の初期設定

### 2.1 - Organization を作成する

![Screenshot 2023-02-26 at 12 05 40](https://user-images.githubusercontent.com/45121253/221390035-79d95f3c-4474-4243-849e-334e650620fc.png)

**tips**
- Organization 内で複数のレポジトリを管理出来るため、上記では Quasar というレポジトリで Quasar のフレームワークの検証などを行っています。

<br />

### 2.2 - Repository を作成する

Organization 内で新しいレポジトリを作成し、下記のブランチ保護設定を ```develop``` と ```main``` に対して行います。

![Screenshot 2023-02-26 at 12 25 42](https://user-images.githubusercontent.com/45121253/221390751-b60a42d3-f8b1-4cf6-9e95-2a76c6c189f3.png)

```Require a pull request before merging``` はパターンにマッチするブランチに対してマージする前に、プルリクエストを必須にする設定。

```Required number of approvals before merging``` はプルリクのレビューの approve の最低限の数を設定する（例:2に設定したら最低2人に承認を得る必要がある）

また、Github Actions などの CI を追加する場合、

![Screenshot 2023-02-26 at 12 35 24](https://user-images.githubusercontent.com/45121253/221390932-ab080dba-957d-4521-8a27-0d21b968a079.png)

---

## 3. 開発の流れ

### 3.1 - Issue を作って課題のタスク分けを行う
![Screenshot 2023-02-22 at 9 53 41](https://user-images.githubusercontent.com/45121253/220492780-2d96796f-e5bb-448f-a144-b70ee7b68fc0.png)

参考リンク
- [Issueの作成方法](https://docs.github.com/ja/issues/tracking-your-work-with-issues/creating-an-issue)
- [Issueで課題管理Assignee, Label, Project機能](https://style.potepan.com/articles/31077.html)
- [Markdown記法の書き方1](https://qiita.com/tbpgr/items/989c6badefff69377da7)
- [Markdown記法の書き方2](https://www.markdownguide.org/basic-syntax/)

<br />

### 3.2 - Issue に対する ```feature``` ブランチを ```develop``` から切る

```
git switch develop
git pull
git switch -c feature/#50_add_cpu
```

**tips**
- 最新の ```develop``` を pull してから ```feature``` ブランチを切りましょう
- ```feature``` ブランチ名を ```feature/#[Issue 番号]_XXXXXX``` に統一することでどの Issue に対するブランチなのかが明確になります

<br />

### 3.3 - ```feature``` ブランチで開発する

```
git add .
git status
git commit -m "#50 add random CPU"
```

**tips**
- コミット時のメッセージを ```#[Issue 番号] XXXXXX``` に統一することで Issue とコミットを紐付けられます

<br />

### 3.4 - 開発終了後、```develop``` へプルリクを作成する

```
git push origin feature/#50_add_cpu
```

![Screenshot 2023-02-22 at 9 52 23](https://user-images.githubusercontent.com/45121253/220492595-a6dafad3-aa0b-460b-9cc7-6355f7335ae3.png)

**tips**
- プルリクで今回の目的や実装の概要を書いてどのような変更を行なったのか説明しましょう
- ```closes #50``` などとプルリクに追記することでマージされた際 Issue を自動的に close することも出来ます

<br />

### 3.5 - 最低一人のメンバーにプルリクのレビューをしてもらう

![Screenshot 2023-02-26 at 11 54 24](https://user-images.githubusercontent.com/45121253/221389797-464e06b6-b13d-4572-9585-3c471f3a58f1.png)

```2.2``` で設定したプルリクに対する approve の最低個数や CI のチェックが満たされているかどうかを確認し、その場合マージします。

参考リンク
- [PullRequestで提案された変更をレビューする](https://docs.github.com/ja/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request)
- [複数行へのレビュー](https://qiita.com/YumaInaura/items/65d59adbce322567ef14)
- [マージコンフリクトを解決する](https://docs.github.com/ja/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-on-github)
- [特定のpull requestをローカルに持ってくる](https://qiita.com/tarr1124/items/d807887418671adbc46f)
- [PullRequestでマージしたのを打ち消す](https://saikeblog.com/2020/03/09/github%E3%81%A7pull-request%E3%81%AE%E3%83%9E%E3%83%BC%E3%82%B8%E3%82%92%E6%89%93%E3%81%A1%E6%B6%88%E3%81%99%E6%96%B9%E6%B3%95/)
