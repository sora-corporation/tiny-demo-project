# このリポジトリの説明

受託開発小規模案件のデモプロジェクト。

- ファイル構成
- Issue 管理
- GitHub Projects の利用

などのサンプル。

## デモ案件の設定

- 自転車修理サービスを営む会社 XYZ がクライアント
- 2023 年 12 月に受注し、 2024 年 1 月から着手、納期は 2024 年 2 月 29 日とする
- デザインは別の会社制作のもので決まっている
- 問合せフォーム付きの LP コーディング, 問合せのステータス管理が可能な管理画面が開発スコープ
  - Web サイトの配信環境構築も含む
- LP の流入や CV はクライアントが直接おこないたいが、生の数字を確認できる仕組みを構築するのは開発スコープに入っているものとする
- 納品後は少額での保守契約となる予定とする
- ドメインは新規取得するものとする

以降の行は `README` のサンプル。

---

# デモプロジェクト

自転車修理サービスの問合せフォームと管理画面。  
案件概要: https://the-board.jp/projects/xxx

(😇 クライアント, 受注金額, 納期, プロジェクト番号あたりを確認できる URL 等を貼っておく)

# ワイヤーフレーム

https://www.figma.com/file/yBTPFvXJnOuAUxUO8g2NHk/Round-Rock-Bicycle-Repair?type=design&node-id=1-5&mode=design&t=Ebxh0PQfxS6AKLVJ-0  
※デザイン込みでFIX

# 開発

## Required

- [nvm](https://github.com/nvm-sh/nvm)
- [Yarn](https://yarnpkg.com/)

(😇 開発を始めるにあたり、最低限必要なツールなどを挙げておく)

## 開発ガイドライン

https://github.com/sora-corporation/tiny-demo-project/wiki/%E9%96%8B%E7%99%BA%E3%82%AC%E3%82%A4%E3%83%89%E3%83%A9%E3%82%A4%E3%83%B3

(😇 Gitブランチ戦略, Issue / Pull Request作成のガイドライン, ドキュメント作成方針...etcを書く、または、別のどこかに書いてURLを貼る)

## Quickstart

```sh
git clone git@github.com:sora-corporation/tiny-demo-project.git
cd tiny-demo-project
nvm use
yarn
yarn start
```

ブラウザで http://localhsot:3000 にアクセス

(😇 プロジェクトに新しく入った人が数コマンドで開発環境を構築できるようにしておく。プロジェクトに参加したその日にプルクリを投げられる状態が理想的)

### ドキュメント

- フロントエンド
  - https://github.com/sora-corporation/tiny-demo-project/wiki/%E3%83%87%E3%82%A3%E3%83%AC%E3%82%AF%E3%83%88%E3%83%AA%E6%A7%8B%E6%88%90
- バックエンド
  - https://doc.xxx.xyz

## 環境

- 本番環境
  - https://xxx.xyz
  - デプロイブランチ: `release`
- 開発環境
  - https://dev.xxx.xyz
  - デプロイブランチ: `main`
  - Basic認証: `username / password`

### IaC

Terraformで管理。`terraform/` を参照。  
(😇 開発環境、本番環境ともにIaC化する。インフラ環境の属人化は避ける。)

## CI / CD

### CI

Pull Request が作成されるとLintチェックとTypeScriptの型チェックが実行される。  
`.github/workflows/pre-commit.yml` を参照。

### CD

以下のブランチへの Push をトリガーに Amplify で自動デプロイ

| 本番環境 | 開発環境 |
| --- | --- |
| `release` | `main` |

(😇 デプロイは自動化する)
