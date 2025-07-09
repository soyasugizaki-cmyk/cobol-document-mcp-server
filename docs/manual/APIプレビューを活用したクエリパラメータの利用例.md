---
contentId: query-parameters-sample-using-api-preview
directory: manual
---

# APIプレビューを活用したクエリパラメータの利用例

このページではコンテンツ（主にリスト形式）のAPIプレビュー機能を活用し、さまざまなシーンにおける各クエリパラメータの使い方の実例をご紹介します。

各クエリパラメータの詳細な使い方については、[GET /api/v1/{endpoint}](https://document.microcms.io/content-api/get-list-contents#h929d25d495) のページをご参照ください。

前提
==

前提として、APIと各コンテンツが以下のように存在していると仮定します。

*   **ブログ**
*   **カテゴリ**（ブログに「コンテンツ参照」で紐づけられている）
*   **タグ**（ブログに「複数コンテンツ参照」で紐づけられている）

  
**▼ブログのAPIスキーマ**  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/4842f7374a974542a10ff81fc9d453ea/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-19%2017.05.08.png)  
  
**▼ ブログのコンテンツ一覧**  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/7269163060ab477aa881382ac43aeb11/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-19%2017.10.04.png)  
  
**▼ カテゴリのコンテンツ一覧**  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/e2c7b6966c604848b247c658ebc1a823/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-19%2017.05.21.png)  
  
**▼ タグのコンテンツ一覧**  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/b6d4da73d1e443aca8f7fbfe1bdd1048/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-19%2017.05.27.png)

利用例
===

【例1】コンテンツ数を指定して取得する
-------------------

コンテンツ数を指定して取得する場合、`limit` パラメータを利用します。  
参考: [GET /api/v1/{endpoint} - limit](https://document.microcms.io/content-api/get-list-contents#h4cd61f9fa1)  
  
以下は、ブログ一覧において、1件のコンテンツを取得する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/6866264de30b4d0eb6c844dd1162235d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.03.04.png)

`limit`パラメータのデフォルト値は10件です。

【例2】取得開始位置をずらして取得する
-------------------

ページングの実装などのために取得開始位置をずらして取得する場合、`offset` パラメータを利用します。  
参考: [GET /api/v1/{endpoint} - offset](https://document.microcms.io/content-api/get-list-contents#h41838110ca)  
  
以下は、ブログ一覧において、2件目のコンテンツから取得する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/f2af6a5db7304ebc9d480590fe3cd926/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.03.33.png)

【例3】公開日が新しい順に取得する
-----------------

コンテンツの順序を指定して取得する場合、並び替えのための`orders` パラメータを利用します。  
参考: [](https://document.microcms.io/content-api/get-list-contents#h41838110ca)[GET /api/v1/{endpoint} - orders](https://document.microcms.io/content-api/get-list-contents#hf1af2f632c)  
  
以下は、ブログ一覧において、公開日（`publishedAt`）が新しい順（降順）に取得する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/2622e3cde0f44038a7aa3fa84b4309ba/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.04.04.png)

【例4】ブログの「タイトル」および「内容」を対象に全文検索したい
--------------------------------

テキストフィールド／テキストエリア／リッチエディタを横断して全文検索をしたい場合、`q` パラメータを利用します。  
参考: [](https://document.microcms.io/content-api/get-list-contents#h41838110ca)[GET /api/v1/{endpoint} - q](https://document.microcms.io/content-api/get-list-contents#ha8abec0b2f)  
  
以下は、ブログ一覧において、「タイトル（テキストフィールド）」および「内容（リッチエディタ）」フィールドに対して「フレームワーク」という文字列で横断的に全文検索する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/f6f5a53d8c11484aac8227258ddab5b7/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.05.34.png)

`q`パラメータによる検索は、コンテンツ内容を形態素解析した結果を対象に実施されます。検索語句と一致するキーワードの登録がないコンテンツでも、検索結果に含まれることがあります。正確な部分一致検索が必要な場合は、`filters`パラメータの使用をご検討ください。

【例5】特定のカテゴリ（コンテンツ参照）を持つコンテンツのみを絞り込んで取得したい
-----------------------------------------

コンテンツ参照フィールドを利用しているとき、参照先の特定のコンテンツのみを持つコンテンツを絞り込んで取得したい場合、`filters` パラメータを利用します。  
参考: [](https://document.microcms.io/content-api/get-list-contents#h41838110ca)[GET /api/v1/{endpoint} - filters](https://document.microcms.io/content-api/get-list-contents#hdebbdc8e86)  
  
以下は、ブログ一覧において、「更新情報（コンテンツID: `pk_fl45f4f`）」を持つコンテンツのみを取得する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/c05b9cb9b6a64951968c3659778d556d/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.06.14.png)

【例6】特定のタグ（複数コンテンツ参照）を持つコンテンツのみを絞り込んで取得したい
-----------------------------------------

複数コンテンツ参照フィールドを利用しているとき、参照先の特定のコンテンツのみを絞り込んで取得したい場合、`filters` パラメータを利用します。  
参考: [](https://document.microcms.io/content-api/get-list-contents#h41838110ca)[GET /api/v1/{endpoint} - filters](https://document.microcms.io/content-api/get-list-contents#hdebbdc8e86)  
  
以下は、ブログ一覧において、「タグA（コンテンツID: `zulopdaa50d`）」を持つコンテンツのみを取得する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/1b9fb86f7984469c8a6e119cc7850773/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.06.52.png)

【例7】必要な項目（id, titleなど）にのみ絞って取得したい
---------------------------------

コンテンツの`id`や`title`など、必要な項目にのみ絞り込んで取得したい場合、`fields` パラメータを利用します。  
参考: [](https://document.microcms.io/content-api/get-list-contents#h41838110ca)[GET /api/v1/{endpoint} - fields](https://document.microcms.io/content-api/get-list-contents#h7462d83de4)  
  
以下は、ブログ一覧において`id`と`title`のみを取得する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/63f76b55a7834d65a5c3cdd1ac8db18b/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.07.15.png)

`fields`パラメータは、取得するデータ量を絞り込むことで、データ転送量を節約するのに役立ちます。

【例8】指定したコンテンツIDを持つコンテンツを一気に取得したい
--------------------------------

指定したコンテンツIDを持つ複数のコンテンツを一気に取得したい場合、`ids` パラメータを利用します。  
参考: [](https://document.microcms.io/content-api/get-list-contents#h41838110ca)[GET /api/v1/{endpoint} - ids](https://document.microcms.io/content-api/get-list-contents#h6b992e0fe4)  
  
以下は、ブログ一覧において、次のコンテンツID（`nvlzo5qffq` と `8of0r4h9ppc`）を持つコンテンツを取得する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/f37d10630ce248e0a217634d2d4f4473/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.07.46.png)

高度な利用例
======

複数のパラメータを組み合わせたケースなど、高度な利用例をご紹介します。

【例1】特定のカテゴリ（コンテンツ参照）を持つコンテンツのみを絞り込み、日時順で並び替えたうえで取得したい
-----------------------------------------------------

コンテンツ参照フィールドで紐づけている特定のコンテンツのみを絞り込み、さらに日時順で並び替えたうえで取得したい場合、`filters`パラメータと`orders`パラメータを利用します。  
  
以下は、ブログ一覧において、「更新情報（コンテンツID: `pk_fl45f4f`）」を持つコンテンツのみを取得し、公開日時（`publishedAt`）の新しい順に並び替える場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/e15908c4b0a841a49f9f67521b8bb51a/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.08.29.png)

【例2】ブログの「タイトル」および「内容」を対象に全文検索し、必要な項目（id, title）にのみ絞り取得したい
---------------------------------------------------------

テキストフィールド／テキストエリア／リッチエディタを横断して全文検索をし、その結果について必要な項目にのみ絞って取得したい場合、`q`パラメータと`fields`パラメータを利用します。  
  
以下は、ブログ一覧において、「タイトル」および「内容」フィールドに対して「フレームワーク」という文字列で横断的に全文検索し、それらのコンテンツの`id`と`title`のみを取得する場合の指定です。  
  
![](https://images.microcms-assets.io/assets/d6af1616730544a596d299c20834f460/1f2e23554fdc4a8f9707cf9e2666ff01/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-05-26%2014.09.02.png)