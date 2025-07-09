---
contentId: introduction
directory: content-api
---

# コンテンツAPIとは

コンテンツAPIは、microCMSにおいてデータの取得や登録を行うための基本的なAPIです。通常はこちらのAPIから取得したデータを利用して、Webサイトやアプリを構築します。

ベースURL
======

`https://{SERVICE_ID}.microcms.io`

仕様
==

*   コンテンツAPIの利用には、APIキーによる認証が必要となります。APIキーに対しては、権限を付与することで利用可能な操作を制限することができます。詳細はAPIキーのドキュメントをご確認ください。

https://document.microcms.io/content-api/x-microcms-api-key

*   コンテンツAPIのエラーレスポンスについては、以下のドキュメントをご参照ください。

https://document.microcms.io/content-api/api-error-response

*   コンテンツAPIのデータはCDNを介して配信されます。CDNのキャッシュが利用される条件の詳細については、以下のヘルプをご参照ください。

https://help.microcms.io/ja/knowledge/how-to-use-content-api-caching

制限事項
====

*   コンテンツAPIの全体に関わる制限事項については、[制限事項のドキュメント](https://document.microcms.io/manual/limitations#h9e37a059c1)をご参照ください。
*   各APIにおける制限事項は、それぞれの個別ページをご参照ください。

APIの種類
======

GET
---

コンテンツの取得を行うためのAPIです。管理画面から登録したデータを利用する場合は、こちらのAPIを利用します。コンテンツ一覧の取得とコンテンツ詳細の取得のための、2種類のAPIがあります。

https://document.microcms.io/content-api/get-list-contents

https://document.microcms.io/content-api/get-content

POST / PUT
----------

コンテンツの作成を行うためのAPIです。他CMSからのコンテンツ移行や、簡単なフォーム送信データの管理などに利用されます。  
POST APIはコンテンツIDが自動生成されますが、PUT APIは任意のコンテンツIDを指定できます。

https://document.microcms.io/content-api/post-content

https://document.microcms.io/content-api/put-content

PATCH
-----

登録済みのコンテンツの内容を書き換えるためのAPIです。外部のデータベースの内容をバッチ処理でCMSに連携するケースなどに利用されます。

https://document.microcms.io/content-api/patch-content

DELETE
------

登録済みのコンテンツを削除するためのAPIです。

https://document.microcms.io/content-api/delete-content