# microCMS Document MCP Server

microCMS ドキュメントにアクセスするための Model Context Protocol (MCP) サーバーです。

## 概要

この MCP サーバーは、microCMSの提供するドキュメントへのアクセスを提供します。  
AI アシスタントが最新のドキュメント内容を検索・取得できるようにします。


## MCP クライアントの設定

### 方法1. Cursorに設定する

Cursorに導入する場合、以下のリンクをクリックしてインストールできます。

<a href="cursor://anysphere.cursor-deeplink/mcp/install?name=microcms-document&config=JTdCJTIyY29tbWFuZCUyMiUzQSUyMm5weCUyMC15JTIwbWljcm9jbXMtZG9jdW1lbnQtbWNwLXNlcnZlciUyMiU3RA%3D%3D"><img src="https://cursor.com/deeplink/mcp-install-dark.svg" alt="Add microcms-document MCP server to Cursor" height="32" /></a>

### 方法2. Claude Desktopに設定する（DXT）

Claude Desktopに導入する場合、dxtファイルを使って簡単にインストールできます。

1. リリースページ から最新の microcms-document-mcp-server.dxt をダウンロード
2. Claude Desktopを起動し、設定 > エクステンション を開く
3. ダウンロードしたdxtファイルをClaude Desktopにドラッグ＆ドロップ

### 方法3. その他のMCPクライアントに設定する

その他のMCPクライアントに導入する場合、設定ファイルに以下を追加してください。

```json
{
  "mcpServers": {
    "microcms-document": {
      "command": "npx",
      "args": ["-y", "microcms-document-mcp-server"]
    }
  }
}
```

## 利用方法

セットアップ後、microCMSについての質問をするとAIが必要に応じてドキュメントを読み、回答します。
チャットの文章に `use microcms-docs-mcp` と書くと明示的にMCPの利用を依頼することもできます。

microCMSの仕様について質問する
```
microCMSで、下書きで登録済みのコンテンツをAPI経由で公開したい。
どのようなリクエストを送ればいい？
```

microCMSのドキュメントを読みながら実装してもらう
```
microCMSで、特定の日付以降に更新されたコンテンツの一覧を取得するスクリプトを作ります。

- 環境変数でサービスIDとAPIキーを指定
- コマンドライン引数でAPIエンドポイントと基準となる日付を指定
- 結果は整形して表示

言語はJavaScriptでお願いします。

use microcms-docs-mcp
```


## 利用可能なツール

### fetch_general

microCMSの一般的な情報を返します。

### list_documents

`docs` ディレクトリ内の利用可能なドキュメントファイル名の配列を返します。

**戻り値**: ドキュメントファイル名の配列

### search_document

指定されたドキュメントファイルの内容を取得します。

**戻り値**: ドキュメントの内容（マークダウン形式のテキスト）


## ライセンス

このプロジェクトは MIT ライセンスの下で公開されています。
