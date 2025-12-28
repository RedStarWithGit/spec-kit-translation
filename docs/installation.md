# 安装指南

## 先决条件

- **Linux/macOS**（或 Windows；现支持 PowerShell 脚本，无需 WSL）
- AI 编程代理：[Claude Code](https://www.anthropic.com/claude-code)、[GitHub Copilot](https://code.visualstudio.com/)、[Codebuddy CLI](https://www.codebuddy.ai/cli) 或 [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [uv](https://docs.astral.sh/uv/) 用于包管理
- [Python 3.11+](https://www.python.org/downloads/)
- [Git](https://git-scm.com/downloads)

## 安装

### 初始化新项目

最简单的入门方式是初始化一个新项目：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init <PROJECT_NAME>
```

或在当前目录初始化：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init .
# 或使用 --here 标志
uvx --from git+https://github.com/github/spec-kit.git specify init --here
```

### 指定 AI 代理

您可以在初始化时主动指定您的 AI 代理：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init <project_name> --ai claude
uvx --from git+https://github.com/github/spec-kit.git specify init <project_name> --ai gemini
uvx --from git+https://github.com/github/spec-kit.git specify init <project_name> --ai copilot
uvx --from git+https://github.com/github/spec-kit.git specify init <project_name> --ai codebuddy
```

### 指定脚本类型（Shell vs PowerShell）

所有自动化脚本现在都有 Bash（`.sh`）和 PowerShell（`.ps1`）两个版本。

自动行为：

- Windows 默认：`ps`
- 其他操作系统默认：`sh`
- 交互模式：除非您传递 `--script`，否则会提示您

强制指定特定的脚本类型：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init <project_name> --script sh
uvx --from git+https://github.com/github/spec-kit.git specify init <project_name> --script ps
```

### 忽略代理工具检查

如果您希望获取模板而不检查正确的工具：

```bash
uvx --from git+https://github.com/github/spec-kit.git specify init <project_name> --ai claude --ignore-agent-tools
```

## 验证

初始化后，您应该能在 AI 代理中看到以下可用命令：

- `/speckit.specify` - 创建规范
- `/speckit.plan` - 生成实现计划
- `/speckit.tasks` - 分解为可执行的任务

`.specify/scripts` 目录将包含 `.sh` 和 `.ps1` 脚本。

## 故障排除

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
