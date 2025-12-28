---
description: 使用计划模板执行实现规划工作流程以生成设计工件。
handoffs:
  - label: 创建任务
    agent: speckit.tasks
    prompt: 将计划分解为任务
    send: true
  - label: 创建检查清单
    agent: speckit.checklist
    prompt: 为以下领域创建检查清单...
scripts:
  sh: scripts/bash/setup-plan.sh --json
  ps: scripts/powershell/setup-plan.ps1 -Json
agent_scripts:
  sh: scripts/bash/update-agent-context.sh __AGENT__
  ps: scripts/powershell/update-agent-context.ps1 -AgentType __AGENT__
---

## 用户输入

```text
$ARGUMENTS
```

您**必须**在继续之前考虑用户输入（如果不为空）。

## 概述

1. **设置**：从仓库根目录运行 `{SCRIPT}` 并解析 JSON 以获取 FEATURE_SPEC、IMPL_PLAN、SPECS_DIR、BRANCH。对于像 "I'm Groot" 这样的参数中的单引号，使用转义语法：例如 'I'\''m Groot'（或如果可能则使用双引号："I'm Groot"）。

2. **加载上下文**：读取 FEATURE_SPEC 和 `/memory/constitution.md`。加载 IMPL_PLAN 模板（已复制）。

3. **执行计划工作流程**：按照 IMPL_PLAN 模板中的结构：
   - 填充技术上下文（将未知内容标记为 "NEEDS CLARIFICATION"）
   - 从宪章填充宪章检查部分
   - 评估关口（如果违规未证明合理，则出错）
   - 第 0 阶段：生成 research.md（解决所有 NEEDS CLARIFICATION）
   - 第 1 阶段：生成 data-model.md、contracts/、quickstart.md
   - 第 1 阶段：通过运行代理脚本更新代理上下文
   - 在设计后重新评估宪章检查

4. **停止并报告**：命令在第 2 阶段规划后结束。报告分支、IMPL_PLAN 路径和生成的工件。

## 阶段

### 第 0 阶段：概述和研究

1. **从上面的技术上下文中提取未知内容**：
   - 对于每个 NEEDS CLARIFICATION → 研究任务
   - 对于每个依赖项 → 最佳实践任务
   - 对于每个集成 → 模式任务

2. **生成和分派研究代理**：

   ```text
   对于技术上下文中的每个未知内容：
     任务："研究 {feature context} 的 {unknown}"
   对于每个技术选择：
     任务："为 {domain} 中的 {tech} 找到最佳实践"
   ```

3. **在 `research.md` 中整合发现**，格式：
   - 决策：[选择了什么]
   - 基本原理：[为什么选择]
   - 考虑的替代方案：[还评估了什么]

**输出**：research.md，所有 NEEDS CLARIFICATION 已解决

### 第 1 阶段：设计和契约

**先决条件**：`research.md` 完成

1. **从功能规范中提取实体** → `data-model.md`：
   - 实体名称、字段、关系
   - 来自需求的验证规则
   - 状态转换（如果适用）

2. **从功能需求生成 API 契约**：
   - 对于每个用户操作 → 端点
   - 使用标准 REST/GraphQL 模式
   - 输出 OpenAPI/GraphQL 架构到 `/contracts/`

3. **代理上下文更新**：
   - 运行 `{AGENT_SCRIPT}`
   - 这些脚本检测正在使用哪个 AI 代理
   - 更新适当的代理特定上下文文件
   - 仅添加来自当前计划的新技术
   - 保留标记之间的手动添加

**输出**：data-model.md、/contracts/*、quickstart.md、代理特定文件

## 关键规则

- 使用绝对路径
- 在关口失败或未解决的澄清时出错
