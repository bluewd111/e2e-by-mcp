Playwright MCP を使用して Web アプリケーションの E2E（エンドツーエンド）テストを生成するプロジェクトです。

## 前提条件

- Node.js 16 以上がインストールされていること
- テスト対象のサーバーが `http://localhost/` で起動していること

テスト対象サーバーの URL を変更したい場合は `playwright.config.ts` の `baseURL` を変更してください。

## セットアップ

Cursor を利用する前提で記載しています。

1. 依存関係のインストール:

```bash
npm ci
```

2. Playwright ブラウザのインストール（すでに実行済みの場合は不要）:

```bash
npx playwright install
```

3. Cursor の MCP Server を設定

Cursor Settings > MCP > Add new global MCP server から MCP Server を追加

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

## テストの生成

チャットから以下のように指示してください。  
Cursor のチャット欄はテキストのペーストがうまくいかない場合があるので、
その場合は適当なテキストファイルに下記指示をコピーして、チャットではそのファイルを参照させて指示に従うよう伝えてください。

```bash

Playwright用のE2Eテストを作成してください。

# 作成するテスト

- / 画面を表示しログインできること
  - ID: admin
  - PASS: admin

# テスト作成方法

PlaywrightのMCPを使って以下環境へアクセスして要素を解析してください。
そして、解析した要素をベースにE2Eテストを作成してください。

## 環境情報

- http://localhost/

# 補足ルール

必ず以下のルールに従ってください。

- テストファイルは tests ディレクトリに作成してください。
- tests ディレクトリ以外のファイルは原則更新しないでください。どうしても更新が必要であれば許可を求めてください。
- テストの実行に失敗したら、すぐにテストの修正を試みず、どんな原因が考えられて、どう修正する方針であるかを説明して、修正許可を求めてください。

```

## テストの実行

### 全てのテストを実行:

```bash
npx playwright test
```

### 特定のテストファイルを実行:

```bash
npx playwright test tests/example.spec.ts
```

### UI モードでテストを実行:

```bash
npx playwright test --ui
```

### 特定のブラウザでテストを実行:

```bash
npx playwright test --project=chromium
```

### デバッグモードでテストを実行:

```bash
npx playwright test --debug
```

## 参考リソース

- [Playwright 公式ドキュメント](https://playwright.dev/docs/intro)
- [API リファレンス](https://playwright.dev/docs/api/class-playwright)
- [ベストプラクティス](https://playwright.dev/docs/best-practices)
- [Playwright MCP レポジトリ](https://github.com/microsoft/playwright-mcp)
