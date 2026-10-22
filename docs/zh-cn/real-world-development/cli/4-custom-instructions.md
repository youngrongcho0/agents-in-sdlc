---
title: "第 4 课 - 使用自定义指令指导 Copilot"
description: "了解存储库指令，添加文档标准，并将其应用于筛选代码。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

使用生成式 AI 时，上下文至关重要。如果任务必须以特定方式完成，就应让 Copilot 获取相关指导。[指令文件][instruction-files]不仅描述想要什么代码，还描述代码应如何组织。现在你已经构建了筛选功能，可以了解 Copilot 使用的指令，添加文档标准，并将其应用于代码。

本课将完成以下任务：

- 了解存储库指令和路径范围指令文件如何传递给智能体。
- 更新指令文件，确保遵循编码标准。
- 查看指令文件对代码的影响。

## 场景

和任何优秀的开发团队一样，Tailspin Toys 也有一套开发实践指南和要求，包括：

- 注释应解释意图和不明显的决策，而不是重复代码。
- `db/` 和 `src/lib/` 中的导出函数应使用 TSDoc/JSDoc 记录用途、参数和返回值（如有可注入的 `db` 参数，也应记录）。
- 可复用的 Astro 组件应记录其 `Props` 契约，相关代码更改时注释也应保持更新。
- 应保留现有的格式化和 lint 指导。

通过使用指令文件，可以确保 Copilot 获得正确的信息，按照上述实践完成任务。

## 指令文件

自定义指令可以向 Copilot 提供上下文和偏好，帮助它更好地理解你的编码风格和要求。这是一项强大的功能，可用于引导 Copilot 提供更相关的建议和代码片段。你可以为整个存储库创建指令，也可以为特定文件类型创建任务级上下文。

指令文件有两种类型：

- `.github/copilot-instructions.md`：针对存储库每个请求发送给 Copilot 的单个指令文件。它应包含与大多数请求相关的项目级信息。
- `.github/instructions/*.instructions.md`：为特定语言、文件类型或任务提供指导。

> [!NOTE]
> 不同环境支持的其他指令格式可能有所不同。依赖某种格式前，请查阅[自定义指令支持参考][custom-instructions-support]。

## 探索本项目中的自定义指令文件

为了开始探索，启动项目已包含一组指令文件。在进行更改前先了解现有内容，以便观察其影响。

1. 返回 Codespace。
2. 在 Codespaces 编辑器中（而非终端）打开 `.github/copilot-instructions.md`。
3. 浏览文件，注意项目的简要说明和编码指导。这些指令适用于此存储库中与 Copilot 的每次交互。
4. 打开 `.github/instructions` 文件夹并浏览其中的文件。注意其中包含 Astro 文件、Drizzle 数据层、测试等方面的指令。
5. 打开 `.github/instructions/unit-tests.instructions.md`。注意顶部的 `applyTo` 字段，它会设置决定指令适用文件的 glob。
6. 打开 `.github/instructions/drizzle.instructions.md`，注意其中指向其他指令文件和现有项目文件的链接。这样可以将较大的指令集拆分为较小、可复用的文件，并指向可参考的示例。

## 更新指令文件以符合团队指导

现有文件已经是不错的起点，但还缺少一项内容。修改核心 `copilot-instructions.md` 文件，确保新生成的 TypeScript 包含 TSDoc 注释。

1. 在 `.github/copilot-instructions.md` 中找到 **Code formatting guidance** 部分，该部分应在第 35 行附近。
2. 在最后一个项目符号后添加以下内容：

   ```markdown
   - All new TypeScript should contain TSDocs comments for documentation purposes.
   ```

文件会自动保存！

## 使用更新后的指导

Copilot CLI 会在会话开始时加载存储库指令。保存更新后的指令后，退出并恢复筛选会话，让 Copilot 在不丢失功能上下文的情况下使用新指令。

1. 如果筛选会话仍处于打开状态，请输入 `/exit` 关闭它。Copilot CLI 会自动保存会话。
2. 在 `game-filters-cli` 分支的存储库根目录中，恢复已保存的会话：

   ```bash
   copilot --resume
   ```

   如果系统提示，请选择筛选会话，并确认已检出 `game-filters-cli` 分支。
3. 让 Copilot 应用更新后的指导：

   ```plaintext
   We just updated our instructions and code guidance. Can you please update the code you generated to match that guidance?
   ```

4. 输入 `/diff`，阅读更改的 TypeScript 文件。注意新生成的 TSDoc 注释，并确认它们准确解释了代码。

## 总结和下一步

你了解了 Copilot CLI 如何获取指令文件中的上下文，并将新标准应用于功能。具体来说，你：

- 探索了存储库指令和路径范围指令文件如何传递给智能体。
- 更新了指令文件，确保遵循编码标准。
- 查看了指令文件对代码的影响。

接下来，[自定义并运行可复用的 quality-checks 技能][next-lesson]，确保一致地运行 lint 和测试。

## 资源

- [为 Copilot CLI 添加自定义指令][instruction-files]
- [自定义指令支持][custom-instructions-support]
- [创建有效自定义指令的最佳实践][instructions-best-practices]
- [Awesome Copilot — 指令文件和其他资源集合][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/
