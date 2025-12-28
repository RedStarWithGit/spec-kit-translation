---
description: 根据可用的设计工件将现有任务转换为功能可操作的、按依赖排序的 GitHub issues。
tools: ['github/github-mcp-server/issue_write']
scripts:
  sh: scripts/bash/check-prerequisites.sh --json --require-tasks --include-tasks
  ps: scripts/powershell/check-prerequisites.ps1 -Json -RequireTasks -IncludeTasks
---

## 用户输入

```text
$ARGUMENTS
```

您**必须**在继续之前考虑用户输入（如果不为空）。

## 概述

1. 从仓库根目录运行 `{SCRIPT}` 并解析 FEATURE_DIR 和 AVAILABLE_DOCS 列表。所有路径必须是绝对路径。对于像 "I'm Groot" 这样的参数中的单引号，使用转义语法：例如 'I'\''m Groot'（或如果可能则使用双引号："I'm Groot"）。
2. 从执行的脚本中，提取 **tasks** 的路径。
3. 通过运行以下命令获取 Git 远程：

```bash
git config --get remote.origin.url
```

> [!CAUTION]
> 仅当远程是 GITHUB URL 时继续执行后续步骤

4. 对于列表中的每个任务，使用 GitHub MCP 服务器在代表 Git 远程的仓库中创建新的 issue。

> [!CAUTION]
> 在任何情况下都不要在不匹配远程 URL 的仓库中创建 issues
