---
contentId: patch-contents-status
directory: management-api
---

# PATCH /api/v1/contents/{endpoint}/{content_id}/status

PATCH APIを用いることで、コンテンツの公開状態をAPI経由で変更することができます。

リクエストヘッダー
=========

X-MICROCMS-API-KEY
------------------

PATCH APIリクエストの際に必要な認証キーです。  
マネジメントAPIのデフォルト権限で「コンテンツの公開状態を変更」を有効にして、リクエストヘッダーに含めて送信してください。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/4ab2795fa97e4d05861f15768159afe7/CleanShot%202024-03-22%20at%2014.40.50%402x.png)

X-MICROCMS-API-KEYが判別できると、第三者による不正なコンテンツの操作が可能となります。お取り扱いには十分ご注意ください。詳細は「[APIキー（APIの認証と権限管理）](https://document.microcms.io/content-api/x-microcms-api-key)」をご覧ください。

Content-Type
------------

送信するデータの形式を指定します。  
microCMSではJSON形式のデータのみ扱っているため、`application/json`と指定してください。  

リクエストボディ
========

公開状態を変更するためには、`PUBLISH`、または`DRAFT`を配列に文字列として渡してください。`PUBLISH`はコンテンツを公開状態に変更できます。`DRAFT`はコンテンツを下書き状態に変更できます。

    // 「公開中」にする場合
    {"status": ["PUBLISH"]}
    
    //　「下書き中」にする場合
    {"status": ["DRAFT"]}

現在のところ、操作可能なステータス変更は限られています。詳細は以下の通りです。  
  
**■対応している変更**

*   「公開中」→「下書き中」
*   「下書き中」→「公開中」

  
**■対応していない変更**

*   「公開中」→「公開中かつ下書き中」
*   「公開中」→「公開終了」
*   「公開中かつ下書き中」→「公開中」（下書き中の内容を公開する）
*   「公開終了」→「公開中」
*   「公開終了」→「下書き中」

レスポンス
=====

正常にコンテンツを作成できた場合は`200`レスポンスが返却されます。