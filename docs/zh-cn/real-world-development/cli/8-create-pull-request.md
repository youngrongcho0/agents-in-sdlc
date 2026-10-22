---
title: "第 8 课 - 创建并合并功能 PR"
description: "一起审查筛选、指令、技能更新、QA 配置文件和测试，然后创建 PR 并使用 Agent Merge。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

你的筛选实现、指令更新、技能更新、质量保证（QA）配置文件和测试都保存在同一个分支上。现在一起审查这些内容并打开拉取请求。你之前亲自合并了星级评分拉取请求（PR），这次将让 **Agent Merge** 管理整个流程。

> [!NOTE]
> 通常，我们会将功能、指令更新、技能更新和 QA 智能体拆分为几个独立 PR。为了简化研讨会，你将完整的筛选和质量工作流保留在同一个会话和分支中，并将所有工作放入这个 PR。

本课将完成以下任务：

- 了解 Agent Merge 及其如何自动化合并生命周期。
- 检查完整的功能更改和验证证据。
- 创建筛选 PR。
- 仅在审查后启用 Agent Merge，并确认 PR 已合并。

## 场景

在整个筛选工作流中，你使用 Copilot 规划、实现和验证了一个功能。现在，Tailspin Toys 希望自动化剩余的 PR 工作，同时让开发者继续控制合并授权。

## 介绍 Agent Merge

**Agent Merge** 会自动完成合并拉取请求所需的剩余工作。启用后，Copilot 会处理阻止 PR 合并的问题：修复失败的持续集成（CI）检查、响应审查评论，并在需要时变基；然后在存储库允许时启用 GitHub 自动合并。

到目前为止，你都是自己选择 **Merge pull request**。Agent Merge 可以承担这项责任。在启用 Agent Merge 前，请审查工作并确认已准备就绪。

## 使用 Agent Merge 管理 PR

现在所有代码都已创建，让我们一起审查代码、创建 PR，并让 Agent Merge 管理后续流程。

1. 返回 Codespace。
2. 输入 `/agent` 打开智能体对话框。
3. 从选项列表中选择 **Default**，然后按 <kbd>Enter</kbd>。
4. 使用命令 `/pr create` 创建新的 PR。
5. 使用 `/pr agentmerge` 激活 Agent Merge。
6. Copilot 会监视 PR 的持续集成流程。所有检查成功后，它会执行合并。
7. 确认看到 Copilot 发出的类似 `"PR #14 was squash-merged successfully."` 的消息。

> [!IMPORTANT]
> Agent Merge 不会绕过必需的批准、分支保护、合并队列、存储库设置或缺少的权限。如果它被阻止，请阅读报告的原因，并在存储库允许时手动完成经过审查的合并。

## 总结和下一步

你已自动化开发流程的多个部分，包括生成代码、测试和验证代码，以及现在的拉取请求流程。你：

- 了解了 Agent Merge 及其如何自动化合并生命周期。
- 检查了完整的功能更改和验证证据。
- 创建了筛选 PR。
- 仅在审查后启用了 Agent Merge，并确认 PR 已合并。

接下来，[探索更实用的 Copilot CLI 斜杠命令][next-lesson]，了解上下文、模型、共享和可选的云端委派。

## 资源

- [使用 Copilot CLI 管理拉取请求][manage-prs]
- [Copilot CLI 命令参考][cli-reference]

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../9-cli-power-tools/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
