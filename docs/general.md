# microCMS仕様概要

## APIについて

* microCMSには **コンテンツAPI** と **マネジメントAPI** の2種類のAPIがあります
* コンテンツAPI
  * ベースURLは ``https://{SERVICE_ID}.microcms.io` 
  * コンテンツの追加や削除など、基本的なコンテンツ管理で使うAPIです
  * 詳細は docs/content-api 以下にあります
* マネジメントAPI
  * ベースURLは `https://{SERVICE_ID}.microcms-management.io`
  * コンテンツのステータス変更やメディアのアップロードなど、管理画面で行う操作をAPIで実行できます
  * 詳細は docs/management-api 以下にあります


## 管理画面について

* 管理画面での確認が必要なアクションをした場合、管理画面のURLをユーザーに伝えます
* 管理画面トップ
  * https://{サービスID}.microcms.io
* コンテンツ
  * https://{サービスID}.microcms.io/apis/{API_ID}/{コンテンツID}


## ドキュメントについて

* ドキュメント（docs以下のマークダウンファイル）を回答した場合、ユーザーが自分で確認できるようにドキュメントURLを伝えます
* ドキュメントURLの例
  * https://document.microcms.io/{ディレクトリ名}/{コンテンツID}
  * ディレクトリ名は `directory` コンテンツIDは `contentId` というキーでマークダウンファイルに記載されています

## `microcms-document-mcp-server` について

MCPサーバーのToolの使い方を紹介します。

1. 最初に一度 `fetch_general` で全体情報を取得します
2. 次に `list_documents` で参照可能なドキュメントの一覧を取得します
3. 最後に `search_document` で必要なドキュメントを探します

# 諸注意

* プランについての情報は間違えると影響が大きいため、「Teamプラン以上で」のような直接的な言及は避けてください
  * 「利用できるプランについてはドキュメントを確認してください」などと添えるだけにしておきましょう
