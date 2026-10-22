---
title: "レッスン 8 - 機能 PR を作成してマージする"
description: "フィルタリング、instruction、skill の更新、QA プロファイル、テストをまとめて確認し、PR を作成して Agent Merge を使います。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

フィルタリングの実装、instruction の更新、skill の更新、品質保証 (QA) プロファイル、テストが、1 つのブランチに保存されています。まとめて確認して、プルリクエストを開くときです。星評価のプルリクエスト (PR) は自分でマージしましたが、今回は **Agent Merge** にプロセスを任せます。

> [!NOTE]
> 通常は、機能、instruction の更新、skill の更新、QA エージェントをいくつかの PR に分けます。このワークショップでは流れを簡単にするため、フィルタリングと品質ワークフロー全体を 1 つの会話とブランチにまとめ、すべての作業をこの PR に含めています。

このレッスンでは、次のことを行います。

- Agent Merge とは何か、マージのライフサイクルを自動化する方法を学ぶ。
- 機能全体の変更と検証結果を確認する。
- フィルタリングの PR を作成する。
- レビュー後にのみ Agent Merge を有効にし、PR がマージされたことを確認する。

## シナリオ

フィルタリングのワークフロー全体で、Copilot を使って機能の計画、実装、検証を行いました。Tailspin Toys は現在、開発者がマージを承認できる状態を保ちながら、残りの PR 作業を自動化したいと考えています。

## Agent Merge の概要

**Agent Merge** は、プルリクエストを取り込むために必要な残りの作業を自動化します。有効にすると、Copilot は PR を妨げている問題に対応します。たとえば、失敗した継続的インテグレーション (CI) チェックの修正、レビューコメントへの対応、必要に応じたリベースを行い、リポジトリで許可されていれば GitHub の自動マージを有効にします。

これまでは自分で **Merge pull request** を選択していました。Agent Merge にその責任を任せることができます。ただし、Agent Merge を有効にする前に作業を確認し、準備ができていると判断してください。

## Agent Merge で PR を管理する

コードが完成したので、まとめてレビューし、PR を作成して、残りのプロセスを Agent Merge に任せます。

1. Codespace に戻ります。
2. `/agent` と入力してエージェントダイアログを開きます。
3. オプションの一覧から **Default** を選択し、<kbd>Enter</kbd> を押します。
4. `/pr create` コマンドを使って新しい PR を作成します。
5. `/pr agentmerge` を使って Agent Merge を有効にします。
6. Copilot は PR の継続的インテグレーションの処理を監視します。すべて成功すると、マージを実行します。
7. Copilot から `PR #14 was squash-merged successfully.` のようなメッセージが表示されることを確認します。

> [!IMPORTANT]
> Agent Merge は、必須の承認、ブランチ保護、マージキュー、リポジトリの設定、不足している権限を回避しません。ブロックされた場合は、報告された理由を読み、リポジトリで許可されているときに、レビュー済みのマージを手動で完了してください。

## まとめと次のステップ

コードの生成、テストと検証、そして今回のプルリクエストのプロセスなど、開発プロセスの複数の部分を自動化しました。具体的には、次のことを行いました。

- Agent Merge とは何か、マージのライフサイクルを自動化する方法を学んだ。
- 機能全体の変更と検証結果を確認した。
- フィルタリングの PR を作成した。
- レビュー後にのみ Agent Merge を有効にし、PR がマージされたことを確認した。

次は、[コンテキスト、モデル、共有、任意のクラウド委任に使える Copilot CLI のスラッシュコマンド][next-lesson]を確認します。

## リソース

- [Copilot CLI でプルリクエストを管理する][manage-prs]
- [Copilot CLI コマンドリファレンス][cli-reference]

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../9-cli-power-tools/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
