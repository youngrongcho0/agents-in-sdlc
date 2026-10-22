---
title: "第 2 课 - 添加星级评分：快速见效"
description: "使用 Copilot CLI 对游戏卡片进行小幅更改，在转发的浏览器中审查更改，并将其作为第一个拉取请求合并。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

现在你已经安装了 Copilot CLI 并尝试过对话，是时候对项目进行第一次更改了。保持更改小而明确：游戏数据中已经有星级评分，但主页上的游戏卡片尚未显示它。你将让智能体显示评分、审查更改，并将其作为第一个拉取请求合并。

本课将完成以下任务：

- 在功能分支上启动专注于某项功能的 Copilot 会话。
- 让智能体对项目进行小幅更改。
- 使用 `/diff` 审查更改。
- 运行应用，在转发的浏览器中确认更改。
- 打开并合并第一个拉取请求。

## 场景

Tailspin Toys 中的每个游戏都可以有星级评分，游戏详细信息页已经显示了评分。不过，主页上的游戏卡片只显示标题、类别、发布者和描述。作为热身练习，让智能体在每张卡片上显示已有评分，这是一个非常适合首次会话的小型独立更改。

## 对话的组成

**对话**是你与 Copilot CLI 共同处理任务的地方。与 Copilot app 不同，普通 CLI 对话使用终端当前检出的存储库和 Git 分支，而不是创建专用工作树。已保存的对话可以让你稍后返回同一讨论，同时文件和分支仍是磁盘上的普通 Git 状态。

在对话中，你会看到三类内容：你的提示和智能体的响应；智能体探索和编辑文件时的工具活动；以及可使用 `/diff` 检查的更改。

## 启动对话并请求更改

现在开始新的对话，实现功能。

1. 返回 Codespace。
2. 如果之前未打开终端，请按 <kbd>Control</kbd>+<kbd>\`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>\`</kbd>（Windows/Linux）。
3. 如果 Copilot 尚未启动，请使用以下命令：

   ```bash
   copilot --yolo
   ```

4. 使用斜杠命令 `/new` 启动新会话，然后按 <kbd>Enter</kbd>。
5. 使用以下提示请求更改：

   ```plaintext
   Show each game's starRating out of 5 in the game cards on the list page. If the rating is null, show "No rating yet". Keep the card layout as it is, add tests, and run the relevant checks.
   ```

Copilot 会探索项目，找到显示游戏详细信息所需的文件，并创建必要的代码。现在，你已使用 Copilot CLI 添加了一个新功能！

## 审查差异

所有 AI 生成的更改都应在合并前审查，即使更改很小。现在就在 Copilot CLI 中探索更改。

1. 输入 `/diff`，检查每个更改的文件。
2. 确认游戏卡片在有评分时显示数值评分，在 `starRating` 为 `null` 时显示 `No rating yet`。
3. 确认测试覆盖这两种状态。
4. 查看 Copilot 运行的检查结果，并让它修复任何失败。
5. 审查完成后，按 <kbd>Esc</kbd> 退出差异屏幕。

> [!NOTE]
> Copilot 和所有生成式 AI 工具一样具有概率性而非确定性，因此实际代码可能不同。请审查行为，而不要期待某种完全相同的实现。

## 检查更改

当然，不能只阅读代码就假定它有效。让 Copilot 启动网站，以便我们在 Codespaces 转发的浏览器中检查更新后的 UI。

1. 让 Copilot 启动应用：

   ```plaintext
   Start the app so I can inspect the star-rating change in my browser. Tell me the URL and leave the server running.
   ```

2. Codespaces 报告端口 `4321` 可用后，选择 **Open in Browser**。
3. 确认游戏卡片显示五分制评分。
4. 返回 Copilot，让它停止启动的服务器：

   ```plaintext
   Stop the development server you started.
   ```

## 打开并合并第一个拉取请求

现在你已创建功能！接下来创建拉取请求（PR），将新代码合并到项目中。

1. 让默认智能体提交更改：

   ```plaintext
   Commit the reviewed star-rating changes with an appropriate commit message.
   ```

2. 输入 `/pr create`。Copilot CLI 创建 PR 时会推送现有提交，并显示 PR URL。
3. 按住 <kbd>Command</kbd>（Mac）或 <kbd>Ctrl</kbd>（Windows/Linux），选择 Copilot CLI 显示的 URL，打开 PR。
4. 审查更改的文件和检查。
5. 准备就绪后，选择 **Merge pull request**，然后确认合并。
6. 返回 Codespace，使用 `/exit` 退出 Copilot CLI。
7. 更新本地 `main`：

   ```bash
   git checkout main
   git pull
   ```

## 总结和下一步

恭喜！你已使用 GitHub Copilot CLI 交付了第一个更改！具体来说，你：

- 在功能分支上启动了专注于某项功能的 Copilot 会话。
- 让智能体对游戏卡片进行了小幅更改。
- 使用 `/diff` 审查了更改。
- 运行应用，在转发的浏览器中确认了更改。
- 打开并合并了第一个拉取请求。

接下来，你将[从筛选议题开始，使用 Plan 和 Autopilot 模式][next-lesson]构建更大的功能。

## 资源

- [关于 GitHub Copilot CLI][about-copilot-cli]
- [Copilot CLI 命令参考][cli-reference]

[previous-lesson]: ../1-install-copilot-cli/
[next-lesson]: ../3-agent-modes/
[about-copilot-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
