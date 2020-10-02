---
title: Azbill Web App
---
**注意: これは実在しないアプリのドキュメントです。**

## アーキテクチャ

![architecture](arch.drawio.svg)

- 組織内の Azure の利用状況のレポートを作成し、ダッシュボードの web アプリで閲覧できるようにします。
- レポート作成
  - [azbill CLI](https://github.com/yaegashi/azbill) のバッチ処理により作成します。
  - バッチ処理は Azure Container Instance のコンテナにより実行します。
  - バッチ処理は Azure Functions によりスケジュール実行します。実行頻度は1日1回程度です。
  - レポートは JSON の形式で Blob Storage に保存します。
- Web アプリ
  - シングルページアプリとして App Service にデプロイします。
  - Azure AD 連携 (EasyAuth) により組織内ユーザーのみが閲覧できます。
