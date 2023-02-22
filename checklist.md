# 上級者チーム開発 - チェックリスト

## 概要
チーム開発を進める中で達成すべき内容。

下記は**一周目**に達成すべき事項
#### 1. 必ず週2回全メンバーが集まれる時間を決めて、ミーティングを行う
#### 2. 今回の課題で達成したい要件（requirements）を決める 
#### 3. チームメンバーと Git の[管理の仕方](https://github.com/recursion-team-v/team-v-devlog/blob/main/github_tutorial.md)を共有し、レポジトリを作成する
#### 4. 最低限の開発環境を構築する
- 使用する言語
- 使用するフレームワーク
- 使用する CI (husky、github actions など）
- Linter とコードフォーマッターの設定（eslint、prettier など）
#### 5. deploy 環境を決める
- フロントエンドは Vercel、Netlify など
- バックエンドは Google Cloud Run、AWS、Render など

また、開発を進める中で、
#### 6. 毎週末にその週行った作業をまとめて全チームと共有する
レポジトリに ```dev-log.md``` を作成し、毎週末更新する。
内容としては、
```
1. 達成したこと
2. 苦労していること（直面している問題）
3. 今後の課題
```