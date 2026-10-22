---
title: "レッスン 3 - エージェントモード: Plan と Autopilot"
description: "Plan で方針を合意し、Autopilot で issue からフィルタリングを構築し、Interactive モードで結果を確認します。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

最初に小さな機能をプロジェクトへ追加しました。しかし、大きな変更にはより堅牢なプロセスが必要です。GitHub Copilot CLI は組織の既存の流れに合わせて動作するため、適切なものを適切な方法で構築できます。このレッスンから、issue を使って新機能を生成し、コードを検証し、期待どおりに動作することを確認して、最終的にプロジェクトへマージする、エージェント主導の開発プロセスを学びます。

> [!NOTE]
> 機能のワークフローを続ける間は、同じ会話とブランチを使います。通常は作業するファイルの種類ごとに異なるブランチや PR を使いますが、ここでは中心概念に集中するため近道をします。

このレッスンでは、次のことを行います。

- GitHub issue から新しい Copilot の会話を開始する。
- Plan モードで要件を定義する。
- Autopilot モードで新機能を実装する。
- コードをレビューする。
- 転送されたブラウザーで機能を手動検証する。

機能の作業を続ける中で、リポジトリの instruction を更新し、既存の `quality-checks` skill をカスタマイズし、MCP による検証を追加し、QA エージェントを作成して、機能 PR を開きます。

## シナリオ

Tailspin Toys のカタログは拡大しており、訪問者はゲームをカテゴリとパブリッシャーで絞り込む必要があります。バックログの issue には機能の説明がありますが、カテゴリの組み合わせなどの詳細はコーディング前に合意する必要があります。Plan モードで決定事項を整理し、Autopilot で範囲を限定した実装を承認します。

## 背景

AI コーディングエージェントを開発フローに導入しても、基本は変わりません。むしろ、その重要性は増します。多くの開発者は次のような流れで作業します。

1. 実装内容を説明する issue から始める。
2. 構築するものの計画を作成する。
3. コードを作成してレビューする。
4. テストを実行してコードを検証する。
5. 新しい機能を手動で検証する。
6. プルリクエスト (PR) を作成する。
7. コードレビューが完了し、継続的インテグレーションが成功したら、コードをマージする。

この標準的な方法に従うことで、AI が生成したコードにも要件を満たしていることと、手書きのコードと同じ検証プロセスを通っていることを確実にできます。

## 会話モード

**会話モード**は、エージェントに許可する自律性の程度を制御します。<kbd>Shift</kbd>+<kbd>Tab</kbd> を押すとモードを切り替えられます。

- **Interactive**: エージェントと協力して作業します。エージェントは変更を提案し、入力を待ちます。
- **Plan**: エージェントは最初に計画を作成し、プロジェクトファイルの編集はできません。
- **Autopilot**: エージェントは自律的にコードを作成し、テストを実行し、タスクが完了するまで反復します。

最初に Plan モードで計画を確認し、その後 Autopilot で実装します。

## issue から始める

フィルタリング作業を始める前に、Codespace に戻り、リポジトリとターミナルを準備します。

1. Codespace に戻ります。停止している場合は再起動します。
2. 星評価の PR がマージ済みであることを確認します。
3. ターミナルが開いていない場合は、<kbd>Control</kbd>+<kbd>\`</kbd> (Mac) または <kbd>Ctrl</kbd>+<kbd>\`</kbd> (Windows/Linux) を押します。
4. `main` を更新し、フィルタリング作業用のブランチを作成します。

   ```bash
   git checkout main
   git pull --ff-only
   git checkout -b game-filters-cli
   ```

5. Copilot CLI を起動します。

   ```bash
   copilot --yolo
   ```

6. <kbd>Tab</kbd> を 2 回押して **Issues** タブを開きます。
7. <kbd>A</kbd> を押してすべての issue を表示します。
8. 矢印キーで **Allow users to filter games by category and publisher** というタイトルの issue を選択します。
9. <kbd>C</kbd> を押して issue をプロンプトに追加し、**Session** タブに戻ります。

## フィルタリング機能を計画する

計画を立てると、複雑な機能を実装する前に方針を定義できます。

1. <kbd>Shift</kbd>+<kbd>Tab</kbd> を押して Plan モードに切り替え、プロンプト下のモード表示が **Plan** であることを確認します。
2. issue の参照の後に次のプロンプトを入力します。

   ```plaintext
   Create a plan for implementing this feature.
   ```

Copilot はプロジェクトを調査し、最適な方法を判断して計画を作成します。

3. フィルタリングの動作について質問されたら、好みに基づいて回答します。
4. 計画が完成したら、<kbd>Control</kbd>+<kbd>E</kbd> (Mac) または <kbd>Ctrl</kbd>+<kbd>E</kbd> (Windows/Linux) を押して計画を展開します。
5. 計画を確認します。
6. 判断と異なる部分があれば、Copilot に計画の修正を依頼します。

## Autopilot を承認する

計画を作成して確認したら、実装に進みます。

1. **Accept plan and build on autopilot (recommended)**、またはインストールされているバージョンで同等の名前の選択肢を選びます。
2. プロンプト下のモード表示が **Autopilot** になっていることを確認します。
3. Copilot が計画に沿って反復し、コードを生成してテストを実行する様子を確認します。

> [!NOTE]
> 承認するとすぐに実装が始まることがあります。まず計画を確認してください。依存関係がない、またはポートが競合していると報告された場合は、チェックが完了したと判断する前にセットアップの問題を解決します。

## 実装をレビューして検証する

1. <kbd>Shift</kbd>+<kbd>Tab</kbd> を押して Interactive モードに入り、モード表示が **Plan** や **Autopilot** でないことを確認します。
2. `/diff` と入力してフィルタリングの実装とテストを確認します。
3. 結果を issue と計画中の決定事項と比較します。
4. 確認が終わったら <kbd>Esc</kbd> を押して差分表示を終了します。
5. プロジェクトのチェック結果を確認し、失敗があれば Copilot に修正を依頼します。

## 新機能を試す

1. Copilot にアプリの起動を依頼します。

   ```plaintext
   Start the app so I can try the filtering feature in my browser. Tell me the URL and leave the server running.
   ```

2. Codespaces でポート `4321` が利用可能になったら、**Open in Browser** を選択します。
3. 計画で合意したカテゴリフィルタリング、パブリッシャーフィルタリング、組み合わせを試します。
4. リセットと結果が空の場合の動作が issue と決定事項に一致することを確認します。
5. Codespace に戻り、起動した開発サーバーを停止するよう Copilot に依頼します。

## まとめと次のステップ

異なる会話モードを使って、機能を構築してレビューしました。このレッスンでは、次のことを行いました。

- GitHub issue から新しい Copilot の会話を開始した。
- Plan モードで要件を定義した。
- Autopilot モードで新機能を実装した。
- コードをレビューした。
- 転送されたブラウザーで機能を手動検証した。

次は、[カスタム instruction を使って][next-lesson]、コードが文書化されたプラクティスに従うようにします。

## リソース

- [GitHub Copilot CLI の Autopilot][autopilot]
- [Copilot CLI コマンドリファレンス][cli-reference]

[autopilot]: https://docs.github.com/copilot/concepts/agents/copilot-cli/autopilot
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[previous-lesson]: ../2-add-star-rating/
[next-lesson]: ../4-custom-instructions/
