---
title: "レッスン 7 - QA エージェントを作成して使う"
description: "issue の要件、quality-checks skill、Playwright MCP を組み合わせる QA カスタムエージェントを作成します。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

`quality-checks` skill で自動チェックを実行し、Playwright MCP でブラウザーのフィルタリング体験を確認しました。ここでは、それらを明確な QA プロセスを持つカスタムエージェントにまとめます。

このレッスンでは、次のことを行います。

- カスタムエージェントが instruction、skill、MCP ツールと連携する方法を確認する。
- 再利用可能な品質保証プロファイルを作成して確認する。
- QA エージェントを選択し、フィルタリング issue に対する結果を確認する。

## シナリオ

Tailspin Toys は、プルリクエスト (PR) を開く前に、要件、コード品質、自動チェック、テストカバレッジ、ブラウザー動作を一貫して確認したいと考えています。カスタムエージェントで QA プロセスを調整し、再利用可能なレポートを作成できます。

## カスタムエージェントとは

カスタムエージェントは、Markdown プロファイルで定義する Copilot の専門版です。プロファイルには、目的、instruction、利用可能なツールを記載します。このワークショップでは `.github/agents/qa.agent.md` に QA の役割を定義し、Copilot CLI で選択します。

リポジトリの instruction はチームの標準を説明し、`quality-checks` skill は繰り返し実行するチェックをまとめ、Playwright MCP はブラウザーツールを提供します。QA プロファイルは、それらを使って要件を評価し、結果を報告する方法を Copilot に伝えます。

## QA プロファイルを作成する

1. Codespace に戻り、フィルタリングの会話が Interactive モードであることを確認します。
2. 既定のエージェントに、次のカスタムエージェントを作成するよう依頼します。

   ```plaintext
   Create a custom agent named QA in .github/agents/qa.agent.md. It should check features against their issues and agreed requirements, follow the repository instructions, run the quality-checks skill, use Playwright MCP to verify behavior, and add tests when coverage is missing.

   Have it report each requirement as pass, fail, or blocked with supporting evidence. It must ask before changing implementation code, and it must not commit changes or open pull requests.

   Just create the profile for now so I can review it.
   ```

## プロファイルを確認する

1. `/diff` と入力し、`.github/agents/qa.agent.md` を開きます。
2. frontmatter を読みます。`description` は必須で、`name` は任意ですが、含めると表示名が明確になります。
3. instruction に従い、`quality-checks` skill を実行し、Playwright MCP を使うことを確認します。
4. QA が根拠を報告し、実装コードの変更前に確認を求め、コミットやプルリクエストを作成しないことを確認します。
5. 不足があれば、既定のエージェントに修正を依頼してから続行します。

## issue に対して QA を実行する

Copilot CLI は会話開始時にプロジェクトのエージェントを読み込みます。プロファイルを作成したら、同じ会話を再開して QA を選択します。

1. 次のプロンプトを入力してエージェントを有効にします。

   ```plaintext
   /agent QA
   ```

2. 次のプロンプトで機能をレビューするよう QA エージェントに依頼します。

   ```plaintext
   Review the filtering feature against the issue and the decisions in our plan. Is it ready for a PR?
   ```

3. QA エージェントの作業が完了するまで待ちます。
4. レポートを確認します。

## まとめと次のステップ

ワークフローに再利用可能な専門家の役割を追加し、その作業をレビューしました。

- カスタムエージェントが instruction、skill、MCP ツールと連携する方法を確認した。
- 再利用可能な品質保証プロファイルを作成して確認した。
- QA エージェントを選択し、フィルタリング issue に対する結果を確認した。

次は、[機能 PR を作成し、Agent Merge を使う][next-lesson]ことで、実装、skill の更新、QA プロファイル、テスト、検証レポートをまとめます。

## リソース

- [Copilot CLI のカスタムエージェントを作成する][create-agents]
- [カスタムエージェントの設定][agent-config]

[previous-lesson]: ../6-mcp-playwright/
[next-lesson]: ../8-create-pull-request/
[create-agents]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli
[agent-config]: https://docs.github.com/copilot/reference/custom-agents-configuration
