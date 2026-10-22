---
title: "第 7 课 - 创建并使用 QA 智能体"
description: "创建 QA 自定义智能体，结合议题要求、quality-checks 技能和 Playwright MCP。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

你已经使用 `quality-checks` 技能运行自动检查，并使用 Playwright MCP 在浏览器中观察筛选体验。现在将这些能力结合到一个具有明确 QA 流程的自定义智能体中。

本课将完成以下任务：

- 了解自定义智能体如何与指令、技能和 MCP 工具协作。
- 创建并检查可复用的质量保证配置文件。
- 选择 QA 智能体，并根据筛选议题审查其发现。

## 场景

Tailspin Toys 希望在打开拉取请求（PR）前，对需求、代码质量、自动检查、测试覆盖率和浏览器行为进行一致的审查。自定义智能体可以协调 QA 流程，并提供可复用的报告。

## 什么是自定义智能体？

自定义智能体是通过 Markdown 配置文件定义的 Copilot 专用版本。配置文件描述智能体的用途、指令和可用工具。在本研讨会中，你将在 `.github/agents/qa.agent.md` 中定义 QA 角色，并在 Copilot CLI 中选择它。

你使用过的自定义项各有不同用途。存储库指令描述团队标准；`quality-checks` 技能封装可重复的检查；Playwright MCP 提供浏览器工具；QA 配置文件告诉 Copilot 如何使用这些能力评估需求并报告结果。它不会取代这些能力，也不需要另一个会话。

## 创建 QA 配置文件

打开功能 PR 前，让 Copilot 创建可复用的 QA 配置文件。该配置文件会定义 QA 执行的检查以及必须遵守的边界。

1. 返回 Codespace，并确认筛选会话处于 Interactive 模式。
2. 让默认智能体创建新的自定义智能体：

   ```plaintext
   Create a custom agent named QA in .github/agents/qa.agent.md. It should check features against their issues and agreed requirements, follow the repository instructions, run the quality-checks skill, use Playwright MCP to verify behavior, and add tests when coverage is missing.

   Have it report each requirement as pass, fail, or blocked with supporting evidence. It must ask before changing implementation code, and it must not commit changes or open pull requests.

   Just create the profile for now so I can review it.
   ```

## 检查配置文件

使用新智能体前，检查其配置文件，确认 Copilot 捕获了预期的 QA 工作流和边界。这可以避免智能体在你只想验证功能时更改功能。

1. 输入 `/diff`，打开 `.github/agents/qa.agent.md`。
2. 阅读 frontmatter。`description` 是必需的；`name` 是可选的，但包含它可以为智能体提供清晰的显示名称。
3. 阅读配置文件指令，确认 QA 从需求开始，遵循存储库指令，运行 `quality-checks` 技能，并使用 Playwright MCP。
4. 确认 QA 会报告支持证据，在更改实现代码前询问，并且不会提交更改或打开拉取请求。
5. 如果生成的配置文件缺少上述职责或边界，请让默认智能体在继续前修改它。

## 根据议题运行 QA

Copilot CLI 会在会话开始时加载项目智能体。创建配置文件后，恢复同一个筛选会话，然后选择 QA，使它可以使用已有的议题和规划决策。

1. 使用以下提示启用智能体：

   ```plaintext
   /agent QA
   ```

> [!NOTE]
> 因为你刚刚创建了智能体，它可能不会显示在可用智能体列表中。但它确实存在，上面的命令会将其激活。

2. 使用以下提示，让 QA 智能体审查功能：

   ```plaintext
   Review the filtering feature against the issue and the decisions in our plan. Is it ready for a PR?
   ```

3. QA 智能体会开始工作！
4. 完成后阅读它提供的报告！

## 总结和下一步

你已向工作流添加可复用的专业角色，并审查了它的工作。在本课中，你：

- 探索了自定义智能体如何与指令、技能和 MCP 工具协作。
- 创建并检查了可复用的质量保证配置文件。
- 选择了 QA 智能体，并根据筛选议题审查了其发现。

现在，你已经准备好实现、技能更新、QA 配置文件、测试和验证报告，可以开始审查。接下来，[将这些内容整合到功能 PR 中，并使用 Agent Merge][next-lesson]。

## 资源

- [为 Copilot CLI 创建自定义智能体][create-agents]
- [自定义智能体配置][agent-config]

[previous-lesson]: ../6-mcp-playwright/
[next-lesson]: ../8-create-pull-request/
[create-agents]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli
[agent-config]: https://docs.github.com/copilot/reference/custom-agents-configuration
