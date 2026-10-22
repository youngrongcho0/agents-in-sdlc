---
title: "第 3 课 - 智能体模式：Plan 和 Autopilot"
description: "使用 Plan 确定实施方法，使用 Autopilot 根据议题构建筛选功能，并使用 Interactive 模式审查结果。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

我们先向项目添加了一个小功能。但更大的更改需要更可靠的流程。GitHub Copilot CLI 可以配合组织现有的工作流，确保我们以正确的方式构建正确的内容。这是几节智能体驱动开发课程中的第一节：从议题开始生成新功能，确保代码有效、功能符合预期，并最终成功合并到项目中。

> [!NOTE]
> 继续完成整个功能工作流时，将使用同一个会话和分支。通常，不同的文件类型会使用不同的分支或拉取请求，但本研讨会会采用捷径，帮助你专注于核心概念。

本课将完成以下任务：

- 从 GitHub 议题启动新的 Copilot 会话。
- 在 Plan 模式中定义需求。
- 使用 Autopilot 模式实现新功能。
- 审查代码。
- 在转发的浏览器中手动验证功能。

继续完成此功能时，你还会更新存储库指令、自定义现有的 `quality-checks` 技能、添加 MCP 验证、创建 QA 智能体，并打开功能拉取请求。

## 场景

Tailspin Toys 的目录正在增长，访客需要按类别和发布者筛选游戏。待办议题描述了此功能，但组合类别等细节需要在编码前达成一致。你将使用 Plan 模式解决这些决策，然后授权 Autopilot 在限定范围内实现功能。

## 背景

将 AI 编码智能体引入开发流程并不会改变基本原则，反而会让这些原则更加重要！大多数开发者遵循类似下面的流程：

1. 从已提交的议题开始，了解需要完成的工作。
2. 制定要构建的内容的计划。
3. 编写并审查代码。
4. 运行测试验证代码。
5. 手动验证新功能。
6. 创建拉取请求（PR）。
7. 代码通过审查且持续集成成功后，合并代码。

> [!NOTE]
> 具体细节会因团队和组织而异，但大多数流程都与上面列出的主题类似。

坚持使用这种标准方法，可以确保 AI 生成的代码满足要求，并经历与手写代码相同的审查流程。

## 会话模式

**会话模式**控制智能体拥有的自主程度。按 <kbd>Shift</kbd>+<kbd>Tab</kbd> 可在模式之间循环切换：

- **Interactive**：你与智能体协作。智能体提出更改，并在继续前等待你的输入。
- **Plan**：智能体先创建计划，并被禁止编辑项目文件。
- **Autopilot**：智能体自主工作：编写代码、运行测试，并不断迭代直到认为任务完成。

先从 Plan 模式开始，审查计划，然后使用 Autopilot 实现计划。

## 从议题开始

开始筛选工作前，返回 Codespace，确保存储库和终端已准备就绪。

1. 返回 Codespace。如果它已停止，请先重新启动。
2. 确认星级评分 PR 已合并。
3. 如果终端尚未打开，请按 <kbd>Control</kbd>+<kbd>\`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>\`</kbd>（Windows/Linux）。
4. 更新 `main`，然后为筛选工作创建分支：

   ```bash
   git checkout main
   git pull --ff-only
   git checkout -b game-filters-cli
   ```

5. 启动 Copilot CLI：

   ```bash
   copilot --yolo
   ```

6. 按两次 <kbd>Tab</kbd> 打开 **Issues** 选项卡。
7. 按 <kbd>A</kbd> 显示所有议题。
8. 使用箭头键突出显示标题为 **Allow users to filter games by category and publisher** 的议题。
9. 按 <kbd>C</kbd> 将议题添加到提示中，然后返回 **Session** 选项卡。

请注意，此时提示会以 `#7`（或类似编号）开头。`#` 可用于将 GitHub 上的议题或拉取请求（PR）带入上下文。

## 规划筛选功能

规划可以先确定实现功能或完成任务的方法，再交给 Copilot 执行。对于任何复杂工作，先规划都是好做法。现在切换到 Plan 模式，让 Copilot 创建计划。

1. 按 <kbd>Shift</kbd>+<kbd>Tab</kbd> 切换到 Plan 模式。确认提示下方的模式指示器显示 **Plan**。
2. 在上一步添加的议题引用后输入以下提示：

   ```plaintext
   Create a plan for implementing this feature.
   ```

Copilot 会开始制定计划：先探索项目，然后确定最佳方法。

3. 在此过程中，Copilot 可能会询问筛选功能应如何工作。根据你的偏好回答即可，没有错误答案！
4. 计划完成后，按 <kbd>Control</kbd>+<kbd>E</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>E</kbd>（Windows/Linux）展开计划。
5. 上下滚动查看计划。
6. 如果计划的某些部分不符合你的决定，请让 Copilot 修改。

## 批准 Autopilot

计划编写并审查完毕后，就可以实现它了！现在使用 Autopilot 让 Copilot 开始工作。

Autopilot 会不断迭代问题，直到 Copilot 认为任务完成。

1. 选择 **Accept plan and build on autopilot (recommended)**，或已安装版本中名称相似的选项。
2. 确认提示下方的模式指示器显示 **Autopilot**。
3. 观察 Copilot 按照既定计划迭代、生成代码并运行测试。

> [!NOTE]
> 批准操作可能会立即开始实现，因此请先审查计划。如果 Copilot 报告缺少依赖项或端口冲突，请先解决设置问题，再将检查视为完成。

## 审查并验证实现

代码生成后，必须像其他代码一样在合并前进行审查。现在同时审查代码并运行站点，确保一切正常。

1. 按 <kbd>Shift</kbd>+<kbd>Tab</kbd> 进入 Interactive 模式。确认模式指示器不再显示 **Plan** 或 **Autopilot**。
2. 输入 `/diff`，检查筛选实现和测试。
3. 将结果与议题以及规划时做出的决定进行比较。
4. 审查代码后，按 <kbd>Esc</kbd> 退出差异视图。
5. 查看项目检查的输出，并让 Copilot 解决任何失败。

## 探索新功能

代码看起来不错，但它能运行吗？像之前一样启动应用，通过 Codespaces 转发的端口打开站点。

1. 让 Copilot 启动应用：

   ```plaintext
   Start the app so I can try the filtering feature in my browser. Tell me the URL and leave the server running.
   ```

2. Codespaces 报告端口 `4321` 可用后，选择 **Open in Browser**。
3. 尝试类别筛选、发布者筛选，以及计划中确定的组合。
4. 确认重置和无结果行为符合议题和你的决定。
5. 返回 Codespace，让 Copilot 停止它启动的开发服务器。

## 总结和下一步

你已使用不同的会话模式构建并审查功能。本课中，你：

- 从 GitHub 议题启动了新的 Copilot 会话。
- 在 Plan 模式中定义了需求。
- 使用 Autopilot 模式实现了新功能。
- 审查了代码。
- 在转发的浏览器中手动验证了功能。

接下来，通过[使用自定义指令][next-lesson]深入了解代码生成，确保代码遵循记录在案的实践。

## 资源

- [GitHub Copilot CLI 中的 Autopilot][autopilot]
- [Copilot CLI 命令参考][cli-reference]

[autopilot]: https://docs.github.com/copilot/concepts/agents/copilot-cli/autopilot
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[previous-lesson]: ../2-add-star-rating/
[next-lesson]: ../4-custom-instructions/
