# MicroCMS Document MCP Server

MicroCMS ドキュメントを参照するための MCP (Model Context Protocol) サーバーです。

## 機能

1. **list_documents**: docs/manual ディレクトリのファイル名一覧を返します
2. **search_document**: 指定されたファイル名のドキュメント内容を返します

## セットアップ

```bash
npm install
npm run build
```

## 使用方法

### 開発環境での実行

```bash
npm run dev
```

### ビルドして実行

```bash
npm run build
npm start
```

## MCP クライアントでの設定

Claude Desktop や他の MCP クライアントで使用する場合は、以下のような設定を追加してください：

```json
{
  "mcpServers": {
    "microcms-document": {
      "command": "node",
      "args": ["/path/to/microcms-document-mcp-server/dist/index.js"]
    }
  }
}
```# microcms-docs-mcp-server
