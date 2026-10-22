---
title: "レッスン 6 - Playwright MCP で機能を検証する"
description: "Copilot CLI で Playwright MCP を確認または設定し、ブラウザーでフィルタリング機能を試します。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

コードを書くことが開発のすべてではありません。データや外部サービスを扱い、Copilot が利用できる自動化も追加する必要があります。MCP サーバーを使うと、Copilot CLI に組み込まれた機能を超えるツールやサービスを利用できます。

このレッスンでは、次のことを行います。

- Model Context Protocol (MCP) と Copilot CLI での使い方を理解する。
- 未設定の場合に Playwright MCP サーバーを追加する。
- エージェントにブラウザーを操作させ、フィルタリング機能を確認する。

## シナリオ

単体テストやエンドツーエンドテストは重要ですが、UI の更新を検証するには、実際に UI を操作する必要があります。ユーザーと同じように Web サイトを操作できる Copilot を使い、変更の信頼性を高めます。

## Model Context Protocol (MCP) とは

[Model Context Protocol (MCP)][mcp-blog-post] は、AI エージェントが外部ツールやサービスと通信する方法を提供します。MCP を使うと、AI エージェントは最新情報にアクセスし、ユーザーに代わって操作を実行できます。

ツールとリソースには MCP サーバー経由でアクセスします。MCP サーバーは AI エージェントと外部ツールやサービスの橋渡しをします。各サーバーは、エージェントが利用できる異なるツールとリソースの集合を表します。

代表的な MCP サーバーには、次のものがあります。

- **[GitHub MCP Server][github-mcp]**: GitHub リポジトリ、issue、プルリクエストを管理する API にアクセスできます。
- **[Playwright MCP Server][playwright-mcp-server]**: Playwright によるブラウザー自動化機能を提供します。

ほかにも多くの MCP サーバーがあります。GitHub は、エコシステムの発見と貢献を促す [MCP レジストリ][mcp-registry]をホストしています。

> [!CAUTION]
> MCP サーバーは、プロジェクトのほかの依存関係と同じように扱ってください。使用前にソースコードを確認し、公開元を検証して、セキュリティへの影響を検討します。

## Playwright MCP サーバーを追加する

Playwright MCP サーバーがまだ利用できない場合は、Copilot がユーザーのように Web サイトを操作できるように追加します。

> [!NOTE]
> Copilot CLI ですでに Playwright MCP を設定している場合は、この手順をスキップして次のセクションへ進みます。

1. Codespace に戻ります。
2. Copilot CLI で次のコマンドを入力し、MCP サーバーの追加ダイアログを開きます。

   ```plaintext
   /mcp add
   ```

3. 名前に `playwright` と入力し、<kbd>Tab</kbd> を押します。
4. <kbd>Enter</kbd> を押してサーバーの種類 **STDIO** を確認し、<kbd>Tab</kbd> を押します。
5. **Command** ダイアログに次のコマンドを貼り付けます。

   ```plaintext
   npx -y @playwright/mcp@latest --headless --no-sandbox
   ```

6. <kbd>Control</kbd>+<kbd>S</kbd> (Mac) または <kbd>Ctrl</kbd>+<kbd>S</kbd> (Windows/Linux) を押して保存します。
7. <kbd>Esc</kbd> を押して MCP ダイアログを終了します。

## Playwright で機能を確認するよう Copilot に依頼する

1. 次のプロンプトを使用して、Playwright MCP サーバーで機能を検証するよう Copilot に指示します。

   ```plaintext
   Start the app and use Playwright MCP to check filtering against the issue and our plan. Tell me what works and what doesn't, without making changes. Stop the server you started when you're done.
   ```

2. Copilot がブラウザーで確認する手順を読みます。
3. レポートを確認し、期待どおりに動作することを確認します。

Copilot はサーバーを起動し、Playwright で Web サイトを操作し、サーバーを停止してレポートを返します。

## まとめと次のステップ

Playwright MCP サーバーを使って、Copilot CLI から実際のブラウザーで機能を確認しました。

- Model Context Protocol (MCP) と Copilot CLI での使い方を学んだ。
- 未設定の場合に Playwright MCP サーバーを追加した。
- エージェントにブラウザーを操作させ、フィルタリング機能を確認した。

次は、skill とブラウザーツールをまとめる[QA カスタムエージェントを作成][next-lesson]します。

## リソース

- [MCP とは何か、なぜ注目されているのか][mcp-blog-post]
- [Microsoft Playwright MCP Server][playwright-mcp-server]
- [Copilot CLI に MCP サーバーを追加する][add-mcp]

[previous-lesson]: ../5-agent-skills/
[next-lesson]: ../7-qa-agent/
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[github-mcp]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[add-mcp]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers
