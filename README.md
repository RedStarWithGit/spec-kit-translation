<div align="center">
    <img src="./media/logo_large.webp" alt="Spec Kit Logo" width="200" height="200"/>
    <h1>🌱 Spec Kit</h1>
    <h3><em>快速构建高质量软件。</em></h3>
</div>

<p align="center">
    <strong>一个开源工具包，让您能够专注于产品场景和可预测的结果，而不是从头开始编写差异化代码。</strong>
</p>

<p align="center">
    <a href="https://github.com/github/spec-kit/actions/workflows/release.yml"><img src="https://github.com/github/spec-kit/actions/workflows/release.yml/badge.svg" alt="Release"/></a>
    <a href="https://github.com/github/spec-kit/stargazers"><img src="https://img.shields.io/github/stars/github/spec-kit?style=social" alt="GitHub stars"/></a>
    <a href="https://github.com/github/spec-kit/blob/main/LICENSE"><img src="https://img.shields.io/github/license/github/spec-kit" alt="License"/></a>
    <a href="https://github.github.io/spec-kit/"><img src="https://img.shields.io/badge/docs-GitHub_Pages-blue" alt="Documentation"/></a>
</p>

---

## 目录

- [🤔 什么是规范驱动开发？](#-什么是规范驱动开发)
- [⚡ 快速入门](#-快速入门)
- [📽️ 视频概述](#️-视频概述)
- [🤖 支持的 AI 代理](#-支持的-ai-代理)
- [🔧 Specify CLI 参考](#-specify-cli-参考)
- [📚 核心理念](#-核心心理念)
- [🌟 开发阶段](#-开发阶段)
- [🎯 实验目标](#-实验目标)
- [🔧 先决条件](#-先决条件)
- [📖 了解更多](#-了解更多)
- [📋 详细流程](#-详细流程)
- [🔍 故障排除](#-故障排除)
- [👥 维护者](#-维护者)
- [💬 支持](#-支持)
- [🙏 致谢](#-致谢)
- [📄 许可证](#-许可证)

## 🔍 什么是规范驱动开发？

规范驱动开发（SDD）**颠覆**了传统软件开发。几十年来，代码一直至上——规范只是我们构建的脚手架，一旦"真正的编码工作"开始就被丢弃。规范驱动开发改变了这一点：**规范变得可执行**，直接生成工作实现，而不仅仅是指导实现。

## ⚡ 快速入门

### 1. 安装 Specify CLI

选择您喜欢的安装方式：

#### 选项 1：持久安装（推荐）

一次安装，随处使用：

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

然后直接使用工具：

```bash
# 创建新项目
specify init <PROJECT_NAME>

# 或在现有项目中初始化
specify init . --ai claude
# 或
specify init --here --ai claude

# 检查已安装的工具
specify check
```

要升级 Specify，请参阅[升级指南](./docs/upgrade.md)以获取详细说明。快速升级：

```bash
uv tool install specify-cli --force --from git+https://github.com/github/spec-kit.git
```

#### 选项 2：一次性使用

无需安装直接运行：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init <PROJECT_NAME>
```

**持久安装的好处：**

- 工具保持安装并在 PATH 中可用
- 无需创建 shell 别名
- 使用 `uv tool list`、`uv tool upgrade`、`uv tool uninstall` 更好的工具管理
- 更清晰的 shell 配置

### 2. 建立项目原则

在项目目录中启动您的 AI 助手。`/speckit.*` 命令在助手中可用。

使用 **`/speckit.constitution`** 命令创建项目的治理原则和开发指南，这些原则将指导所有后续开发。

```bash
/speckit.constitution 创建专注于代码质量、测试标准、用户体验一致性和性能要求的原则。包括这些原则应如何指导技术决策和实现选择的治理。
```

### 3. 创建规范

使用 **`/speckit.specify`** 命令描述您想要构建的内容。重点关注**什么**和**为什么**，而不是技术栈。

```bash
/speckit.specify 构建一个可以帮助我整理照片到单独相册的应用程序。相册按日期分组，可以通过在主页面上拖放来重新组织。相册绝不会在其他嵌套的相册中。在每个相册中，照片以图块式界面预览。
```

### 4. 创建技术实现计划

使用 **`/speckit.plan`** 命令提供您的技术栈和架构选择。

```bash
/speckit.plan 应用程序使用 Vite，使用最少量的库。尽可能使用原生 HTML、CSS 和 JavaScript。图像不会上传到任何地方，元数据存储在本地 SQLite 数据库中。
```

### 5. 分解为任务

使用 **`/speckit.tasks`** 从实现计划创建可执行的任务列表。

```bash
/speckit.tasks
```

### 6. 执行实现

使用 **`/speckit.implement`** 执行所有任务并根据计划构建功能。

```bash
/speckit.implement
```

有关详细分步说明，请参阅我们的[综合指南](./spec-driven.md)。

## 📽️ 视频概述

想要看 Spec Kit 的实际操作吗？观看我们的[视频概述](https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv)！

[![Spec Kit video header](/media/spec-kit-video-header.jpg)](https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv)

## 🤖 支持的 AI 代理

| 代理 | 支持 | 说明 |
| ------------------------------------------------------------------------------------ | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Qoder CLI](https://qoder.com/cli) | ✅ | |
| [Amazon Q Developer CLI](https://aws.amazon.com/developer/learning/q-developer-cli/) | ⚠️ | Amazon Q Developer CLI [不支持](https://github.com/aws/amazon-q-developer-cli/issues/3064)斜杠命令的自定义参数。 |
| [Amp](https://ampcode.com/) | ✅ | |
| [Auggie CLI](https://docs.augmentcode.com/cli/overview) | ✅ | |
| [Claude Code](https://www.anthropic.com/claude-code) | ✅ | |
| [CodeBuddy CLI](https://www.codebuddy.ai/cli) | ✅ | |
| [Codex CLI](https://github.com/openai/codex) | ✅ | |
| [Cursor](https://cursor.sh/) | ✅ | |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli) | ✅ | |
| [GitHub Copilot](https://code.visualstudio.com/) | ✅ | |
| [IBM Bob](https://www.ibm.com/products/bob) | ✅ | 支持斜杠命令的基于 IDE 的代理 |
| [Jules](https://jules.google.com/) | ✅ | |
| [Kilo Code](https://github.com/Kilo-Org/kilocode) | ✅ | |
| [opencode](https://opencode.ai/) | ✅ | |
| [Qwen Code](https://github.com/QwenLM/qwen-code) | ✅ | |
| [Roo Code](https://roocode.com/) | ✅ | |
| [SHAI (OVHcloud)](https://github.com/ovh/shai) | ✅ | |
| [Windsurf](https://windsurf.com/) | ✅ | |

## 🔧 Specify CLI 参考

`specify` 命令支持以下选项：

### 命令

| 命令 | 说明 |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `init` | 从最新模板初始化新的 Specify 项目 |
| `check` | 检查已安装的工具（`git`、`claude`、`gemini`、`code`/`code-insiders`、`cursor-agent`、`windsurf`、`qwen`、`opencode`、`codex`、`shai`、`qoder`) |

### `specify init` 参数和选项

| 参数/选项 | 类型 | 说明 |
| ---------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<project-name>` | 参数 | 新项目目录的名称（如果使用 `--here` 则可选，或使用 `.` 表示当前目录） |
| `--ai` | 选项 | 要使用的 AI 助手：`claude`、`gemini`、`copilot`、`cursor-agent`、`qwen`、`opencode`、`codex`、`windsurf`、`kilocode`、`auggie`、`roo`、`codebuddy`、`amp`、`shai`、`q`、`bob` 或 `qoder` |
| `--script` | 选项 | 要使用的脚本变体：`sh`（bash/zsh）或 `ps`（PowerShell） |
| `--ignore-agent-tools` | 标志 | 跳过对 AI 代理工具（如 Claude Code）的检查 |
| `--no-git` | 标志 | 跳过 git 仓库初始化 |
| `--here` | 标志 | 在当前目录初始化项目，而不是创建新项目 |
| `--force` | 标志 | 在当前目录中初始化时强制合并/覆盖（跳过确认） |
| `--skip-tls` | 标志 | 跳过 SSL/TLS 验证（不推荐） |
| `--debug` | 标志 | 启用详细的调试输出以进行故障排除 |
| `--github-token` | 选项 | API 请求的 GitHub 令牌（或设置 GH_TOKEN/GITHUB_TOKEN 环境变量） |

### 示例

```bash
# 基本项目初始化
specify init my-project

# 使用特定 AI 助手初始化
specify init my-project --ai claude

# 使用 Cursor 支持初始化
specify init my-project --ai cursor-agent

# 使用 Qoder 支持初始化
specify init my-project --ai qoder

# 使用 Windsurf 支持初始化
specify init my-project --ai windsurf

# 使用 Amp 支持初始化
specify init my-project --ai amp

# 使用 SHAI 支持初始化
specify init my-project --ai shai

# 使用 IBM Bob 支持初始化
specify init my-project --ai bob

# 使用 PowerShell 脚本初始化（Windows/跨平台）
specify init my-project --ai copilot --script ps

# 在当前目录初始化
specify init . --ai copilot
# 或使用 --here 标志
specify init --here --ai copilot

# 在当前（非空）目录中强制合并而无需确认
specify init . --force --ai copilot
# 或
specify init --here --force --ai copilot

# 跳过 git 初始化
specify init my-project --ai gemini --no-git

# 启用调试输出以进行故障排除
specify init my-project --ai claude --debug

# 使用 GitHub 令牌进行 API 请求（对企业环境有用）
specify init my-project --ai claude --github-token ghp_your_token_here

# 检查系统要求
specify check
```

### 可用的斜杠命令

运行 `specify init` 后，您的 AI 编码代理将可以访问这些斜杠命令进行结构化开发：

#### 核心命令

规范驱动开发工作流的基本命令：

| 命令 | 说明 |
| ----------------------- | ------------------------------------------------------------------------ |
| `/speckit.constitution` | 创建或更新项目治理原则和开发指南 |
| `/speckit.specify` | 定义您想要构建的内容（需求和用户故事） |
| `/speckit.plan` | 使用您选择的技术栈创建技术实现计划 |
| `/speckit.tasks` | 为实现生成可执行的任务列表 |
| `/speckit.implement` | 根据计划执行所有任务以构建功能 |

#### 可选命令

用于增强质量和验证的额外命令：

| 命令 | 说明 |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `/speckit.clarify` | 澄清未指定的领域（推荐在 `/speckit.plan` 之前使用；以前为 `/quizme`） |
| `/speckit.analyze` | 跨制品一致性和覆盖分析（在 `/speckit.tasks` 之后，`/speckit.implement` 之前运行） |
| `/speckit.checklist` | 生成自定义质量检查清单，验证需求完整性、清晰度和一致性（如"英语的单元测试"） |

### 环境变量

| 变量 | 说明 |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `SPECIFY_FEATURE` | 覆盖非 Git 仓库的功能检测。设置为功能目录名称（例如 `001-photo-albums`）以在不使用 Git 分支的情况下处理特定功能。<br/>**必须在您使用的助手的上下文中设置，然后才使用 `/speckit.plan` 或后续命令。 |

## 📚 核心理念

规范驱动开发是一个强调以下内容的结构化过程：

- **意图驱动开发**，其中规范在"如何"之前定义"什么"
- **使用护栏和组织原则进行丰富的规范创建**
- **多步完善**，而不是从提示进行一次性代码生成
- **大量依赖**高级 AI 模型能力进行规范解释

## 🌟 开发阶段

| 阶段 | 重点 | 关键活动 |
| ---------------------------------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **0 到 1 开发**（"绿地"（Greenfield）） | 从头生成 | <ul><li>从高级需求开始</li><li>生成规范</li><li>规划实现步骤</li><li>构建生产就绪的应用程序</li></ul> |
| **创造性探索** | 并行实现 | <ul><li>探索多样化的解决方案</li><li>支持多种技术栈和架构</li><li>实验 UX 模式</li></ul> |
| **迭代增强**（"棕地"（Brownfield）） | 棕地现代化 | <ul><li>迭代添加功能</li><li>现代化遗留系统</li><li>适应流程</li></ul> |

## 🎯 实验目标

我们的研究和实验重点在于：

### 技术独立性

- 使用多样化的技术栈创建应用程序
- 验证规范驱动开发是一个不依赖于特定技术、编程语言或框架的流程的假设

### 企业约束

- 演示关键任务应用程序开发
- 整合组织约束（云提供商、技术栈、工程实践）
- 支持企业设计系统和合规要求

### 以用户为中心的开发

- 为不同的用户群体和偏好构建应用程序
- 支持各种开发方法（从氛围编码到 AI 原生开发）

### 创造性和迭代流程

- 验证并行实现探索的概念
- 提供健壮的迭代功能开发工作流程
- 扩展流程以处理升级和现代化任务

## 🔧 先决条件

- **Linux/macOS/Windows**
- [支持的](#-支持的-ai-代理) AI 编码代理。
- [uv](https://docs.astral.sh/uv/) 用于包管理
- [Python 3.11+](https://www.python.org/downloads/)
- [Git](https://git-scm.com/downloads)

如果您遇到代理问题，请打开 issue，以便我们完善集成。

## 📖 了解更多

- **[完整的规范驱动开发方法论](./spec-driven.md)** - 深入了解完整流程
- **[详细演练](#-详细流程)** - 分步实现指南

---

## 📋 详细流程
<details>
<summary>点击展开详细的分步演练</summary>

您可以使用 Specify CLI 引导您的项目，这将在您的环境中引入必要的工件。运行：

```bash
specify init <project_name>
```

或在当前目录初始化：

```bash
specify init .
# 或使用 --here 标志
specify init --here
# 当目录已有文件时跳过确认
specify init . --force
# 或
specify init --here --force
```

![Specify CLI 在终端中引导新项目](./media/specify_cli.gif)

您将被提示选择您正在使用的 AI 代理。您还可以在终端中主动指定它：

```bash
specify init <project_name> --ai claude
specify init <project_name> --ai gemini
specify init <project_name> --ai copilot

# 或在当前目录中：
specify init . --ai claude
specify init . --ai codex

# 或使用 --here 标志
specify init --here --ai claude
specify init --here --ai codex

# 在非空当前目录中强制合并
specify init . --force --ai claude

# 或
specify init --here --force --ai claude
```

CLI 将检查您是否安装了 Claude Code、Gemini CLI、Cursor CLI、Qwen CLI、opencode、Codex CLI、Qoder CLI 或 Amazon Q Developer CLI。如果您没有安装，或者您希望在不检查正确工具的情况下获取模板，请在命令中使用 `--ignore-agent-tools`：

```bash
specify init <project_name> --ai claude --ignore-agent-tools
```

### **步骤 1：** 建立项目原则

转到项目文件夹并运行您的 AI 代理。在我们的示例中，我们使用 `claude`。

![引导 Claude Code 环境](./media/bootstrap-claude-code.gif)

如果您看到 `/speckit.constitution`、`/speckit.specify`、`/speckit.plan`、`/speckit.tasks` 和 `/speckit.implement` 命令可用，则说明配置正确。

第一步应该是使用 `/speckit.constitution` 命令建立项目的治理原则。这有助于确保所有后续开发阶段的决策一致性：

```text
/speckit.constitution 创建专注于代码质量、测试标准、用户体验一致性和性能要求的原则。包括这些原则应如何指导技术决策和实现选择的治理。
```

这一步创建或更新 `.specify/memory/constitution.md` 文件，其中包含项目的基础指南，AI 代理将在规范、规划和实现阶段引用这些指南。

### **步骤 2：** 创建项目规范

建立了项目原则后，您现在可以创建功能规范。使用 `/speckit.specify` 命令，然后为要开发的项目提供具体需求。

> [!IMPORTANT]
> 尽可能明确您尝试构建的**什么**和**为什么**。**此时不要专注于技术栈。**

示例提示：

```text
开发 Taskify，一个团队生产力平台。它应该允许用户创建项目、添加团队成员、分配任务、在看板风格的板之间评论和移动任务。在此功能的初始阶段，我们称之为"创建 Taskify"，让我们有多个用户，但用户将预先声明、预先定义。我想要两个不同类别的五个用户，一个产品经理和四个工程师。让我们创建三个不同的示例项目。让我们为每个任务的状态使用标准看板列，例如"待办"（To Do）、"进行中"（In Progress）、"审查中"（In Review）和"已完成"（Done）。此应用程序不会有登录，因为这只是非常初步的测试，以确保我们的基本功能已设置。对于 UI 中任务卡的每个任务，您应该能够在看板工作板的不同列之间更改任务的当前状态。您应该能够为特定卡片留下无限数量的评论。您应该能够从该任务卡片中分配一个有效用户。当您首次启动 Taskify 时，它会给您一个五个用户的列表供您选择。不需要密码。当您点击用户时，您进入主视图，显示项目列表。当您点击项目时，您打开该项目的看板。您将看到列。您将能够前后拖放卡片在不同列之间。您将看到分配给您的卡片，当前登录用户，与所有其他卡片颜色不同，以便您快速看到您的卡片。您可以编辑您所做的任何评论，但不能编辑其他人所做的评论。您可以删除您所做的任何评论，但不能删除其他人所做的任何评论。
```

输入此提示后，您应该看到 Claude Code 启动规划和规范起草过程。Claude Code 还将触发一些内置脚本来设置仓库。

此步完成后，您应该创建一个新分支（例如 `001-create-taskify`），以及 `specs/001-create-taskify` 目录中的新规范。

生成的规范应该包含一组用户故事和功能需求，如模板中所定义。

此时，您的项目文件夹内容应类似于以下内容：

```text
└── .specify
    ├── memory
    │  └── constitution.md
    ├── scripts
    │  ├── check-prerequisites.sh
    │  ├── common.sh
    │  ├── create-new-feature.sh
    │  ├── setup-plan.sh
    │  └── update-claude-md.sh
    ├── specs
    │  └── 001-create-taskify
    │      └── spec.md
    └── templates
        ├── plan-template.md
        ├── spec-template.md
        └── tasks-template.md
```

### **步骤 3：** 功能规范澄清（规划前必须）

创建了基准规范后，您可以继续澄清在第一次尝试中未正确捕获的任何需求。

您应该在创建技术计划之前运行结构化澄清工作流程**以减少下游返工**。

首选顺序：

1. 使用 `/speckit.clarify`（结构化）——顺序的、基于覆盖的提问，将答案记录在澄清部分中。
2. 如果仍然感觉模糊，可以选择性地进行临时的自由形式完善。

如果您有意跳过澄清（例如，spike 或探索性原型），请明确说明，以便代理不会在缺失的澄清上阻止。

示例自由形式完善提示（如果仍需在 `/speckit.clarify` 之后使用）：

```text
对于您创建的每个示例项目或项目，应该有 5 到 15 个任务之间变化的可变数量，随机分布到不同的完成状态。确保每个完成阶段至少有一个任务。
```

您还应该要求 Claude Code 验证**审查和验收检查清单**，检查规范满足条件的项目，并使不满足的项目保持为空。可以使用以下提示：

```text
阅读审查和验收检查清单，如果功能规范满足标准，则勾选检查清单中的每个项目。如果不满足，则将其保留为空。
```

重要的是将与 Claude Code 的交互视为澄清和提出有关规范问题的机会——**不要将其第一次尝试视为最终结果**。

### **步骤 4：** 生成计划

您现在可以具体说明技术栈和其他技术要求。您可以使用 `/speckit.plan` 命令，它内置于项目模板中，并带有如下提示：

```text
我们将使用 .NET Aspire 生成此功能，使用 Postgres 作为数据库。前端应该使用 Blazor 服务器，带有拖放任务板和实时更新。应该创建一个 REST API，包含项目 API、任务 API 和通知 API。
```

此步的输出将包括多个实现细节文档，您的目录树类似于以下内容：

```text
.
├── CLAUDE.md
├── memory
│  └── constitution.md
├── scripts
│  ├── check-prerequisites.sh
│  ├── common.sh
│  ├── create-new-feature.sh
│  ├── setup-plan.sh
│  └── update-claude-md.sh
├── specs
│  └── 001-create-taskify
│      ├── contracts
│      │  ├── api-spec.json
│      │  └── signalr-spec.md
│      ├── data-model.md
│      ├── plan.md
│      ├── quickstart.md
│      ├── research.md
│      └── spec.md
└── templates
    ├── CLAUDE-template.md
    ├── plan-template.md
    ├── spec-template.md
    └── tasks-template.md
```

检查 `research.md` 文档，以确保根据您的说明使用了正确的技术栈。如果任何组件突出，您可以要求 Claude Code 完善它，甚至让它检查您想要使用的平台/框架的本地安装版本（例如 .NET）。

此外，如果您选择的技术栈变化很快（例如 .NET Aspire、JS 框架），您可能希望要求 Claude Code 研究有关所选技术栈的详细信息，并带有如下提示：

```text
我希望您通过实现计划和实现细节，查看哪些领域可以从额外研究中受益，因为 .NET Aspire 是一个快速变化的库。对于您识别的需要进一步研究的领域，我希望您更新研究文档，包含有关我们在此 Taskify 应用程序中将使用的特定版本的更多细节，并启动并行研究任务，使用网络研究澄清任何细节。
```

在此过程中，您可能会发现 Claude Code 被错误地研究了错误的内容——您可以用如下提示帮助推动它朝正确的方向发展：

```text
我认为我们需要将其分解为一系列步骤。首先，确定您需要在实施过程中完成且不确定或会从进一步研究中受益的任务列表。写下这些任务列表。然后，对于这些任务中的每一个，我希望您启动一个单独的研究任务，以便最终结果是我们并行研究所有这些非常特定的任务。我看到您正在做的是看起来您正在一般地研究 .NET Aspire，我认为这在这种情况下对我们不会有太大帮助。那是太不针对性的研究。研究需要帮助您解决特定的定向问题。
```

> [!NOTE]
> Claude Code 可能过于急切并添加您没有要求的功能。要求它澄清更改的理由和更改来源。

### **步骤 5：** 让 Claude Code 验证计划

有了计划后，您应该让 Claude Code 运行它，以确保没有遗漏的部分。您可以使用如下提示：

```text
现在我希望您去审核实现计划和实现细节文件。
通读它，重点关注确定是否存在从阅读它就能清楚的一系列任务。因为我不知道这里是否足够。例如，当我查看核心实现时，如果它能够从实现细节中找到适当的信息以在核心实现或完善中完成每个步骤，那将是有用的。
```

这有助于完善实现计划，并帮助您避免 Claude Code 在其规划周期中遗漏的潜在盲点。完成初始完善通过后，要求 Claude Code 再通过一次检查清单，然后您可以进入实现。

如果安装了 [GitHub CLI](https://docs.github.com/en/github-cli/github-cli)，您还可以要求 Claude Code 从当前分支到 `main` 创建一个具有详细描述的拉取请求，以确保工作量得到正确跟踪。

> [!NOTE]
> 在您让代理实现它之前，还值得提示 Claude Code 交叉检查细节，以查看是否有任何过度设计的组件（请记住——它可能过于急切）。如果存在过度设计的组件或决策，您可以要求 Claude Code 解决它们。确保 Claude Code 遵循 [宪章](base/memory/constitution.md) 作为必须在建立计划时遵守的基础部分。

### **步骤 6：** 使用 /speckit.tasks 生成任务分解

验证了实现计划后，您现在可以将计划分解为可以按正确顺序执行的特定、可执行任务。使用 `/speckit.tasks` 命令自动从实现计划生成详细的任务分解：

```text
/speckit.tasks
```

此步在功能规范目录中创建 `tasks.md` 文件，其中包含：

- **按用户故事组织的任务分解** - 每个用户故事成为具有自己一组任务的单独实现阶段
- **依赖管理** - 任务按顺序排列以尊重组件之间的依赖关系（例如，模型在服务之前，服务在端点之前）
- **并行执行标记** - 用 `[P]` 标记可以并行运行的任务，以优化开发工作流程
- **文件路径规范** - 每个任务包括实施应发生的精确文件路径
- **测试驱动开发结构** - 如果请求了测试，则包含测试任务并按在实现之前编写的顺序排列
- **检查点验证** - 每个用户故事阶段包括验证独立功能的检查点

生成的 tasks.md 为 `/speckit.implement` 命令提供了清晰的路线图，确保系统化的实现，保持代码质量并允许用户故事的增量交付。

### **步骤 7：** 实现

准备就绪后，使用 `/speckit.implement` 命令执行实现计划：

```text
/speckit.implement
```

`/speckit.implement` 命令将：

- 验证所有先决条件都已到位（宪章、规范、计划和任务）
- 从 `tasks.md` 解析任务分解
- 按正确顺序执行任务，尊重依赖关系和并行执行标记
- 遵循任务计划中定义的 TDD 方法
- 提供进度更新并适当处理错误

> [!IMPORTANT]
> AI 代理将执行本地 CLI 命令（如 `dotnet`、`npm` 等）- 确保您的机器上安装了必需的工具。

实现完成后，测试应用程序并解决 CLI 日志中可能不可见的任何运行时错误（例如，浏览器控制台错误）。您可以将这些错误复制并粘贴回您的 AI 代理以进行解决。

</details>

---

## 🔍 故障排除

### Linux 上的 Git 凭证管理器

如果您在 Linux 上遇到 Git 认证问题，可以安装 Git 凭证管理器：

```bash
#!/usr/bin/env bash
set -e
echo "正在下载 Git 凭证管理器 v2.6.1..."
wget https://github.com/git-ecosystem/git-credential-manager/releases/download/v2.6.1/gcm-linux_amd64.2.6.1.deb
echo "正在安装 Git 凭证管理器..."
sudo dpkg -i gcm-linux_amd64.2.6.1.deb
echo "正在配置 Git 使用 GCM..."
git config --global credential.helper manager
echo "正在清理..."
rm gcm-linux_amd64.2.6.1.deb
```

## 👥 维护者

- Den Delimarsky ([@localden](https://github.com/localden))
- John Lam ([@jflam](https://github.com/jflam))

## 💬 支持

如需支持，请打开 [GitHub issue](https://github.com/github/spec-kit/issues/new)。我们欢迎错误报告、功能请求和关于使用规范驱动开发的问题。

## 🙏 致谢

本项目严重受到和基于 [John Lam](https://github.com/jflam) 的工作和研究的影响。

## 📄 许可证

本项目根据 MIT 开源许可条款授权。请参阅 [LICENSE](./LICENSE) 文件以获取完整条款。
