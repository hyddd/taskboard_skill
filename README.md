# TaskBoard Skill for Clawdbot

这是一个为 **Clawdbot** 打造的 **TaskBoardAI** 集成技能。它允许 Clawdbot 通过 MCP (Model Context Protocol) 协议，直接在后台管理任务看板，实现“意图识别 -> 任务创建 -> 执行 -> 归档”的全自动化工作流。

## 核心功能

*   **全生命周期管理**：支持创建 (Todo)、执行 (Doing)、阻塞 (Blocked)、完成 (Done) 四种状态的自动流转。
*   **MCP 深度集成**：使用 stdio 模式与 TaskBoard 后端直接通信，无需维护额外的 HTTP 服务。
*   **内容自适应**：自动修复了 TaskBoard 前端渲染 `content` 字段而非 `description` 字段的问题。
*   **条件反射协议**：配合 `AGENTS.md`，实现通过关键字“【任务】”触发自动建卡。

## 安装与配置

### 1. 前置依赖
本技能依赖于 [TaskBoardAI](https://github.com/taskboardai/taskboardai)。请先全局安装：

```bash
npm install -g taskboardai
```

### 2. 安装 Skill
将本目录克隆至你的 Clawdbot 工作区：

```bash
cd ~/clawd/skills
git clone https://github.com/hyddd/taskboard_skill.git taskboard
```

### 3. 配置路径
检查 `SKILL.md` 中的 `<arg>` 路径是否指向你系统中真实的 `kanbanMcpServer.js` 位置：
```xml
<arg>/opt/homebrew/lib/node_modules/taskboardai/server/mcp/kanbanMcpServer.js</arg>
```

## 使用方法

在与 Clawdbot 的对话中：
*   **创建任务**：“【任务】调研量化框架”
*   **查询任务**：“现在有哪些进行中的任务？”
*   **更新状态**：“那个调研任务做完了，结论是...”

## 工作流协议 (AGENTS.md)

为了获得最佳体验，建议在你的 `AGENTS.md` 中添加以下协议：

```markdown
## Task Protocol
**Trigger:** "【任务】"
1. **Initiate**: Create card in 'Todo' -> Move to 'Doing' -> Announce.
2. **Execute**: Perform the task.
3. **Finalize**: Update content with result -> Move to 'Done'.
```

---

# TaskBoard Skill for Clawdbot

This is a **TaskBoardAI** integration skill designed for **Clawdbot**. It enables Clawdbot to manage a Kanban board directly via the MCP (Model Context Protocol), achieving a fully automated workflow of "Intent Recognition -> Task Creation -> Execution -> Archiving".

## Core Features

*   **Full Lifecycle Management**: Supports automatic transitions between Todo, Doing, Blocked, and Done states.
*   **Deep MCP Integration**: Communicates directly with the TaskBoard backend using stdio mode, eliminating the need for extra HTTP services.
*   **Content Adaptation**: Automatically fixes the issue where the TaskBoard frontend renders the `content` field instead of `description`.
*   **Reflex Protocol**: Works with `AGENTS.md` to trigger automatic card creation via the keyword "【任务】" (Task).

## Installation & Configuration

### 1. Prerequisites
This skill depends on [TaskBoardAI](https://github.com/taskboardai/taskboardai). Please install it globally first:

```bash
npm install -g taskboardai
```

### 2. Install Skill
Clone this directory into your Clawdbot workspace:

```bash
cd ~/clawd/skills
git clone https://github.com/hyddd/taskboard_skill.git taskboard
```

### 3. Configure Path
Check `SKILL.md` to ensure the `<arg>` path points to the actual `kanbanMcpServer.js` location on your system:
```xml
<arg>/opt/homebrew/lib/node_modules/taskboardai/server/mcp/kanbanMcpServer.js</arg>
```

## Usage

In your conversation with Clawdbot:
*   **Create Task**: "【任务】Research quantitative frameworks"
*   **Query Task**: "What tasks are currently in progress?"
*   **Update Status**: "The research task is done, the conclusion is..."

## Workflow Protocol (AGENTS.md)

For the best experience, it is recommended to add the following protocol to your `AGENTS.md`:

```markdown
## Task Protocol
**Trigger:** "【任务】"
1. **Initiate**: Create card in 'Todo' -> Move to 'Doing' -> Announce.
2. **Execute**: Perform the task.
3. **Finalize**: Update content with result -> Move to 'Done'.
```
