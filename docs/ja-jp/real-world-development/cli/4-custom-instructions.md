---
title: "レッスン 4 - カスタム instruction で Copilot を導く"
description: "リポジトリの instruction を確認し、ドキュメント標準を追加して、フィルタリングコードに適用します。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

生成 AI と作業するときはコンテキストが重要です。特定の方法で実行する必要があるタスクでは、そのガイダンスを Copilot に渡します。[instruction file][instruction-files] は、必要なコードだけでなく、その構造も説明します。フィルタリングを構築したので、Copilot が使った instruction を確認し、ドキュメント標準を追加して、コードに適用します。

このレッスンでは、次のことを行います。

- リポジトリの instruction とパス単位の instruction file がエージェントに届く仕組みを確認する。
- コーディング標準に従うよう instruction file を更新する。
- instruction file がコードに与える影響を確認する。

## シナリオ

Tailspin Toys には開発プラクティスに関するガイドラインと要件があります。

- コメントはコードを繰り返すのではなく、意図と自明でない判断を説明する。
- `db/` と `src/lib/` の公開関数には、目的、引数、戻り値を説明する TSDoc/JSDoc を追加し、存在する場合は注入可能な `db` 引数も記載する。
- 再利用可能な Astro コンポーネントには `Props` の契約を記載し、関連コードの変更時もコメントを最新に保つ。
- 既存のフォーマットと lint のガイダンスを維持する。

instruction file を使って、Copilot がこれらのプラクティスに沿って作業できるようにします。

## Instruction file

カスタム instruction を使うと、コンテキストや設定を Copilot に渡し、コーディングスタイルを理解させられます。リポジトリ全体、または特定のファイル種別向けに作成できます。

instruction file には 2 種類あります。

- `.github/copilot-instructions.md`: リポジトリのすべてのリクエストで Copilot に送られる単一の instruction file。
- `.github/instructions/*.instructions.md`: 特定の言語、ファイル種別、タスク向けのガイドラインを提供するファイル。

> [!NOTE]
> ほかの instruction 形式のサポート状況は環境によって異なります。特定の形式を利用する前に、[カスタム instruction のサポートリファレンス][custom-instructions-support]を確認してください。

## このプロジェクトのカスタム instruction file を確認する

1. Codespace に戻ります。
2. Codespaces エディターで `.github/copilot-instructions.md` を開きます。
3. プロジェクトの説明と、すべての操作に適用されるガイダンスを確認します。
4. `.github/instructions` フォルダーを開き、ファイルを確認します。ファイル種別によって instruction が適用されます。
5. `.github/instructions/unit-tests.instructions.md` を開き、先頭の `applyTo` フィールドが対象ファイルを決めることを確認します。
6. `.github/instructions/drizzle.instructions.md` を開き、ほかの instruction file や既存のプロジェクトファイルへのリンクを確認します。

## instruction file を更新する

1. `.github/copilot-instructions.md` で **Code formatting guidance** セクションを探します。
2. 最後の箇条書きとして、次の行を追加します。

   ```markdown
   - All new TypeScript should contain TSDocs comments for documentation purposes.
   ```

3. ファイルを保存します。

Copilot CLI は会話の開始時にリポジトリの instruction を読み込みます。保存したら、フィルタリングの会話を終了して再開します。

1. 会話がまだ開いている場合は `/exit` を入力します。
2. `game-filters-cli` ブランチのリポジトリルートから、保存した会話を再開します。

   ```bash
   copilot --resume
   ```

3. Copilot に更新されたガイダンスを適用するよう依頼します。

   ```plaintext
   We just updated our instructions and code guidance. Can you please update the code you generated to match that guidance?
   ```

4. `/diff` を入力して変更された TypeScript ファイルを確認し、TSDoc が正確に説明していることを確認します。

## 更新した instruction を使う

リポジトリの instruction は会話の開始時に読み込まれるため、更新後に会話を再開して変更を適用します。生成されたコードを確認し、TSDoc コメントが追加されていることを確認してください。

## まとめと次のステップ

Copilot CLI がリポジトリの instruction を取得する仕組みを確認し、更新した標準をコードに適用しました。

- リポジトリの instruction とパス単位の instruction file がエージェントに届く仕組みを確認した。
- instruction file を更新してコーディング標準を適用した。
- instruction file がコードに与える影響を確認した。

次は、再利用可能な `quality-checks` skill を[カスタマイズして実行][next-lesson]、lint とテストを一貫して実行します。

## リソース

- [Copilot CLI のカスタム instruction][instruction-files]
- [カスタム instruction のサポート][custom-instructions-support]
- [効果的なカスタム instruction のベストプラクティス][instructions-best-practices]
- [Awesome Copilot — instruction file などのリソース集][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/
