---
title: "レッスン 9 - GitHub Copilot CLI のスラッシュコマンド"
description: "コンテキストの管理、モデルの選択、セッションの共有、任意のクラウド委任に使えるスラッシュコマンドを確認します。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

優れた CLI ツールと同様に、GitHub Copilot CLI には多くのスラッシュコマンドがあります。これらのコマンドは、高度な機能、内部情報、追加の設定を提供します。すでに `/diff`、`/mcp`、`/skills`、`/agent`、`/pr` などを使いました。ここでは、さらに便利なコマンドを確認します。

このレッスンでは、次のことを行います。

- `/context` と `/compact` で Copilot のコンテキスト管理を確認する。
- `/model` で利用可能なモデルを確認する。
- `/share` でセッションをエクスポートまたは共有する。
- 並列作業、worktree、クラウドエージェントへの委任に使える任意のコマンドを確認する。

## シナリオ

CLI の中心的なワークフローが完了したので、コンテキストの管理、モデルの切り替え、セッションの共有、[Copilot cloud agent][about-cloud-agent] への任意の委任を確認します。

## Copilot CLI のコンテキストを確認する

大きく複雑なタスクでは、モデルの最大コンテキストウィンドウに達することがあります。Copilot CLI は必要に応じて会話を自動的にコンパクト化しますが、スラッシュコマンドで自分で確認や圧縮もできます。

1. Codespace に戻り、まだ開いていなければリポジトリルートから Copilot CLI を起動します。
2. 次を入力します。

   ```plaintext
   /context
   ```

3. モデル、現在のトークン使用量、システム instruction、ツール、メッセージ、空き領域への分割を確認します。
4. 会話をコンパクト化します。

   ```plaintext
   /compact
   ```

5. もう一度 `/context` を入力して結果を比較します。会話が小さい場合は大きな変化がないこともあります。

> [!NOTE]
> Copilot CLI はコンテキストが埋まると自動的にコンパクト化します。実行するタイミングを選びたいときは `/compact` を使い、関係のないタスクに切り替えるときは `/clear` または `/new` を使います。

## モデルを選択する

1. 次を入力します。

   ```plaintext
   /model
   ```

2. 利用可能なモデルと使用状況を確認します。
3. 現在のモデルを維持するか、別のモデルを選択するか、<kbd>Esc</kbd> を押して一覧を閉じます。

## セッションを共有する

1. `/help` を入力し、インストールされているバージョンの `/share` オプションを確認します。
2. 共有する場合は、`/share file` など適切な保存先を選びます。
3. 送信または公開する前にエクスポート内容を確認します。セッションのエクスポートにはプロンプト、応答、プロジェクトの詳細が含まれる場合があります。

リンクや gist の公開は任意です。チームが共有を意図していないリポジトリや会話の内容は公開しないでください。

## 任意: 規模を拡大または委任する

ワークショップの中心部分は完了しました。Copilot CLI には大きなタスク向けのコマンドもあります。

- `/fleet` は独立したサブタスクをサブエージェントに分割し、並列実行できます。
- `/worktree` は別タスク用の隔離された Git worktree を作成できます。
- `/delegate` はタスクを Copilot cloud agent に送り、非同期で作業させ、プルリクエストを開けます。

これらは追加の worktree やリモート作業を作成するため任意です。試す場合は新しく、範囲を明確にしたタスクから始め、通常のワークフローで結果を確認してください。非同期エージェントについて詳しく知りたい場合は、[cloud agent ワークショップ][cloud-workshop]に進みます。

## まとめと次のステップ

スラッシュコマンドを使うと、Copilot CLI を設定し、セッションを共有し、内部の動作を確認できます。このレッスンでは、次のことを行いました。

- `/context` と `/compact` で Copilot のコンテキスト管理を確認した。
- `/model` で利用可能なモデルを確認した。
- `/share` でセッションをエクスポートまたは共有できることを学んだ。
- 並列作業、worktree、クラウドエージェントへの委任に使える任意のコマンドを確認した。

利用できるスラッシュコマンドはほかにもあります。最後に、[学んだことを振り返り][next-lesson]、次の学習ステップを確認します。

## リソース

- [Copilot CLI コマンドリファレンス][cli-reference]
- [Copilot CLI のコンテキスト管理][context-management]
- [Copilot cloud agent について][about-cloud-agent]

[previous-lesson]: ../8-create-pull-request/
[next-lesson]: ../10-review/
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[context-management]: https://docs.github.com/copilot/concepts/agents/copilot-cli/context-management
[about-cloud-agent]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-workshop]: ../../cloud/
