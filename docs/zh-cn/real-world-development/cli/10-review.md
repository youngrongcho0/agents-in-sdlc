---
title: "第 10 课 - 总结和下一步"
description: "回顾 Copilot CLI 工作流、两个拉取请求、可复用的自定义项和更多资源。"
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

你已在 Tailspin Toys 的完整工作流中使用 GitHub Copilot CLI。你：

- 准备了 Codespace，安装 Copilot CLI，探索项目，并找到预置的筛选议题。
- 添加星级评分，在转发的浏览器中审查结果，并手动合并了第一个拉取请求（PR）。
- 从筛选议题开始，在 Plan 模式中确定方法，在 Autopilot 模式中构建，并在 Interactive 模式中审查。
- 使用自定义指令指导智能体，然后自定义现有的 `quality-checks` 技能，并用它运行单元测试、lint 和类型检查。
- 添加了 Playwright Model Context Protocol（MCP）服务器，并使用它在真实浏览器中探索筛选功能。
- 创建并选择质量保证（QA）自定义智能体，评估需求、覆盖率、技能结果和浏览器证据。
- 审查了完整的筛选更改，并授权 Agent Merge 合并筛选 PR。
- 探索了用于上下文、模型、共享和可选云端委派的斜杠命令。

## 你交付的内容

本研讨会包含两个 PR 里程碑，每个里程碑都从更新后的 `main` 创建自己的分支：

1. **星级评分**：在游戏卡片上显示已有的 `starRating` 和明确的未评分状态。
2. **筛选和质量工作流**：实现筛选功能，更新指令并将其应用于功能，自定义 `quality-checks` 报告，创建 QA 配置文件，并加入相关测试。

从规划筛选功能到打开 PR，你使用的是同一个会话和分支。我们将这些工作合并到一个 PR 中，以简化研讨会。

## 不同类型的验证

你通过多种方式检查了代码：自动化测试、自己的浏览器检查，以及 Copilot 通过 MCP 执行的浏览器探索。`quality-checks` 技能运行了单元测试、lint 和类型检查，并以新格式报告结果。QA 将这些结果与需求和测试覆盖率审查结合起来，然后再提交 PR。

新增测试应弥补真实缺口；不需要新增测试的 QA 运行也可能是正确的。授权合并前请审查代码和证据，更改后请刷新受影响的证据。

## 最佳实践

提供给 Copilot 的上下文和工具会影响它的工作。在本研讨会中，你更新了指令、自定义了技能、创建了 QA 配置文件并配置了 MCP 服务器。可以在不同会话中复用这些自定义项，并根据团队需求变化进行调整。指令设定标准，技能描述可重复任务，自定义智能体定义专业角色，MCP 服务器连接外部工具。请审查实际更改和工具结果，而不只是智能体的摘要。

让**模式和模型**匹配任务。使用 **Plan** 在构建前思考方法，使用 **Interactive** 参与范围明确的更改，使用 **Autopilot** 完成范围清晰的任务。日常编辑可选择更快的模型，复杂工作可选择功能更强的模型。

上下文仍然和基础设施一样重要。清楚说明要构建**什么**、**为什么**构建以及**如何**构建，会显著改变输出。

## 继续探索

你已经完成核心工作流。以下是一些值得了解的 CLI 功能：

- `/review`：请求代码审查智能体分析更改。
- `/rubber-duck`：讨论问题并获得另一种观点。
- `/fleet`：并行协调独立子任务。
- `/worktree`：隔离单独任务。
- `/delegate`：将任务发送给 Copilot 云智能体。

## 下一步

改进任何工具的最佳方式就是持续使用它！可以将它用于生产代码、业余项目，或多年来一直想构建却尚未开始的小应用。与团队分享经验，也向团队学习，并一如既往地探索文档。

如果想从终端扩展 Tailspin Toys，请继续学习可选的 [Foundry Backer Concierge 系列][foundry]。若要比较其他环境，请探索 [VS Code 研讨会][vscode]、[GitHub Copilot app 研讨会][app] 或 [Copilot 云智能体研讨会][cloud]。

## 资源

- [关于 GitHub Copilot CLI][about-cli]
- [Copilot CLI 命令参考][cli-reference]
- [自定义 Copilot CLI][customize-cli]
- [使用 Copilot CLI 管理拉取请求][manage-prs]

[previous-lesson]: ../9-cli-power-tools/
[foundry]: ../8-foundry-agent/
[vscode]: ../../vscode/
[app]: ../../app/
[cloud]: ../../cloud/
[about-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[customize-cli]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
