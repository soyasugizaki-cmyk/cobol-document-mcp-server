# microCMS Document MCP Server

microCMS ドキュメントにアクセスするための Model Context Protocol (MCP) サーバーです。

## 概要

この MCP サーバーは、microCMSの提供するドキュメントへのアクセスを提供します。  
AI アシスタントが最新のドキュメント内容を検索・取得できるようにします。

## 機能

- **fetch_general**: microCMSの一般的な内容を読み込みます
- **list_documents**: `docs` ディレクトリ内の利用可能なドキュメントファイル一覧を返します
- **search_document**: 指定されたドキュメントファイルの内容を取得します


## MCP クライアントの設定

Claude Desktop や他の MCP クライアントでこのサーバーを使用するには、以下の設定を追加してください：

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
