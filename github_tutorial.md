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

## 2. 開発の流れ

### 2.1 Issue を作って課題のタスク分けを行う
![Screen Shot 2022-06-13 at 22 16 26](https://user-images.githubusercontent.com/66197642/173498886-b6fd3f9b-5f9e-4207-a8f1-42e00458152c.png)

参考リンク
- [Issueの作成方法](https://docs.github.com/ja/issues/tracking-your-work-with-issues/creating-an-issue)
- [Issueで課題管理Assignee, Label, Project機能](https://style.potepan.com/articles/31077.html)
- [Markdown記法の書き方1](https://qiita.com/tbpgr/items/989c6badefff69377da7)
- [Markdown記法の書き方2](https://www.markdownguide.org/basic-syntax/)

<br />

### 2.2 Issue に対する ```feature``` ブランチを ```develop``` から切る

```
git switch develop
git pull
git switch -c feature/#50_add_cpu
```

tips
- 最新の ```develop``` を pull してから ```feature``` ブランチを切りましょう
- ```feature``` ブランチ名を ```feature/#[Issue 番号]_XXXXXX``` に統一することでどの Issue に対するブランチなのかが明確になります

<br />

### 2.3 ```feature``` ブランチで開発する

```
git add .
git status
git commit -m "#50 add random CPU"
```

tips
- コミット時のメッセージを ```#[Issue 番号] XXXXXX``` に統一することで Issue とコミットを紐づけられます

<br />

### 2.4 開発終了後、```develop``` へプルリクを作成する

```
git push origin feature/#50_add_cpu
```

