---
contentId: delete-content
directory: content-api
---

# DELETE /api/v1/{endpoint}/{content_id}

DELETE APIを用いることで、コンテンツの削除をAPI経由で行うことができます。

**リスト形式のAPIのみ利用可能**です。**オブジェクト形式のAPIでは利用できません**ので、ご注意ください。

リクエストヘッダー
=========

X-MICROCMS-API-KEY
------------------

DELETE APIリクエストの際に必要な認証キーです。  
デフォルト権限もしくは個別権限で「DELETE」を有効にして、リクエストヘッダーに含めて送信してください。

X-MICROCMS-API-KEYが判別できると、第三者による不正なコンテンツの操作が可能となります。お取り扱いには十分ご注意ください。詳細は「[APIキー（APIの認証と権限管理）](https://document.microcms.io/content-api/x-microcms-api-key)」をご覧ください。

リクエストボディ
========

不要です。

レスポンス
=====

正常にコンテンツを削除できた場合は`202`レスポンスが返却されます。

レスポンスボディ
--------

リクエストを正常に実行できた場合のレスポンスボディは以下のようになります。

    Accepted

エラーレスポンス
========

[コンテンツAPIのエラーレスポンス](https://document.microcms.io/content-api/api-error-response)を参照ください。