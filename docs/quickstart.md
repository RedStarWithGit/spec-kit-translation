# 快速入门指南

本指南将帮助您使用 Spec Kit 开始规范驱动开发。

> [!NOTE]
> 所有自动化脚本现在提供 Bash（`.sh`）和 PowerShell（`.ps1`）两种版本。除非您传递 `--script sh|ps`，`specify` CLI 会根据操作系统自动选择。

## 6 步流程

> [!TIP]
> **上下文感知**：Spec Kit 命令会自动根据您当前的 Git 分支（例如 `001-feature-name`）检测活动功能。要在不同规范之间切换，只需切换 Git 分支。

### 步骤 1：安装 Specify

**在您的终端中**，运行 `specify` CLI 命令来初始化您的项目：

```bash
# 创建新项目目录
uvx --from git+https://github.com/github/spec-kit.git specify init <PROJECT_NAME>

# 或在当前目录初始化
uvx --from git+https://github.com/github/spec-kit.git specify init .
```

显式选择脚本类型（可选）：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init <PROJECT_NAME> --script ps  # 强制使用 PowerShell
uvx --from git+https://github.com/github/spec-kit.git specify init <PROJECT_NAME> --script sh  # 强制使用 POSIX shell
```

### 步骤 2：定义您的宪章

**在 AI 代理的聊天界面中**，使用 `/speckit.constitution` 斜杠命令来建立项目的核心规则和原则。您应该提供项目的特定原则作为参数。

```markdown
/speckit.constitution 本项目遵循"库优先"（Library-First）方法。所有功能必须先作为独立库实现。我们严格使用 TDD。我们偏好函数式编程模式。
```

### 步骤 3：创建规范

**在聊天中**，使用 `/speckit.specify` 斜杠命令来描述您想要构建的内容。重点关注**什么**和**为什么**，而不是技术栈。

```markdown
/speckit.specify 构建一个可以帮助我整理照片到单独相册的应用程序。相册按日期分组，可以通过在主页面上拖放来重新组织。相册绝不会在其他嵌套的相册中。在每个相册中，照片以图块式界面预览。
```

### 步骤 4：完善规范

**在聊天中**，使用 `/speckit.clarify` 斜杠命令来识别和解决规范中的歧义。您可以提供特定的关注领域作为参数。

```bash
/speckit.clarify 重点关注安全和性能要求。
```

### 步骤 5：创建技术实现计划

**在聊天中**，使用 `/speckit.plan` 斜杠命令来提供您的技术栈和架构选择。

```markdown
/speckit.plan 应用程序使用 Vite，使用最少量的库。尽可能使用原生 HTML、CSS 和 JavaScript。图像不会上传到任何地方，元数据存储在本地 SQLite 数据库中。
```

### 步骤 6：分解和实现

**在聊天中**，使用 `/speckit.tasks` 斜杠命令来创建可执行的任务列表。

```markdown
/speckit.tasks
```

（可选）使用 `/speckit.analyze` 验证计划：

```markdown
/speckit.analyze
```

然后，使用 `/speckit.implement` 斜杠命令来执行计划。

```markdown
/speckit.implement
```

## 详细示例：构建 Taskify

这是一个构建团队生产力平台的完整示例：

### 步骤 1：定义宪章

初始化项目的宪章以设定基本规则：

```markdown
/speckit.constitution Taskify 是一个"安全优先"（Security-First）的应用程序。所有用户输入必须经过验证。我们使用微服务架构。代码必须完全文档化。
```

### 步骤 2：使用 `/speckit.specify` 定义需求

```text
开发 Taskify，一个团队生产力平台。它应该允许用户创建项目、添加团队成员、分配任务、评论和在看板风格的任务之间移动任务。在此功能的初始阶段，我们称之为"创建 Taskify"，让我们有多个用户，但用户将预先声明、预先定义。我想要两个不同类别的五个用户，一个产品经理和四个工程师。让我们创建三个不同的示例项目。让我们为每个任务的状态使用标准的看板列，例如"待办"（To Do）、"进行中"（In Progress）、"审查中"（In Review）和"已完成"（Done）。此应用程序不会有登录，因为这只是非常初步的测试，以确保我们的基本功能已设置。对于任务卡片 UI 中的每个任务，您应该能够更改任务在看板工作板的不同列之间的当前状态。您应该能够为特定卡片留下无限数量的评论。您应该能够从该任务卡片中分配一个有效用户。当您首次启动 Taskify 时，它会给您一个五个用户的列表供您选择。不需要密码。当您点击用户时，您进入主视图，显示项目列表。当您点击项目时，您打开该项目的看板。您将看到列。您将能够前后拖放卡片在不同列之间。您将看到分配给您的卡片，当前登录用户，与所有其他卡片颜色不同，以便您快速看到您的卡片。您可以编辑您所做的任何评论，但不能编辑其他人所做的评论。您可以删除您所做的任何评论，但不能删除其他人所做的任何评论。
```

### 步骤 3：完善规范

使用 `/speckit.clarify` 命令交互式解决规范中的任何歧义。您还可以提供您希望确保包含的特定细节。

```bash
/speckit.clarify 我想澄清任务卡详细信息。对于 UI 中任务卡的每个任务，您应该能够在看板工作板的不同列之间更改任务的当前状态。您应该能够为特定卡片留下无限数量的评论。您应该能够从该任务卡片中分配一个有效用户。
```

您可以使用 `/speckit.clarify` 继续用更多细节完善规范：

```bash
/speckit.clarify 当您首次启动 Taskify 时，它会给您五个用户的列表供您选择。不需要密码。当您点击用户时，您进入主视图，显示项目列表。当您点击项目时，您打开该项目的看板。您将看到列。您将能够前后拖放卡片在不同列之间。您将看到分配给您的卡片，当前登录用户，与所有其他卡片颜色不同，以便您快速看到您的卡片。您可以编辑您所做的任何评论，但不能编辑其他人所做的评论。您可以删除您所做的任何评论，但不能删除其他人所做的任何评论。
```

### 步骤 4：验证规范

使用 `/speckit.checklist` 命令验证规范检查清单：

```bash
/speckit.checklist
```

### 步骤 5：使用 `/speckit.plan` 生成技术计划

具体说明您的技术栈和技术要求：

```bash
/speckit.plan 我们将使用 .NET Aspire 生成此功能，使用 Postgres 作为数据库。前端应该使用 Blazor 服务器，带有拖放任务板，实时更新。应该创建一个 REST API，包含项目 API、任务 API 和通知 API。
```

### 步骤 6：验证和实现

让您的 AI 代理使用 `/speckit.analyze` 审核实现计划：

```bash
/speckit.analyze
```

最后，实现解决方案：

```bash
/speckit.implement
```

## 关键原则

- **明确**您要构建的内容以及为什么
- **在规范阶段不要专注于技术栈**
- **在实现之前迭代和完善**您的规范
- **在编码开始之前验证**计划
- **让 AI 代理处理**实现细节

## 下一步

- 阅读[完整方法论](../spec-driven.md)以获取深入指导
- 查看[更多示例](../templates)在仓库中
- 探索[GitHub 上的源代码](https://github.com/github/spec-kit)
