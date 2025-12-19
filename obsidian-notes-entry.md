---
category: ai
tags: [MCP, Obsidian, TypeScript, AI工具, 自制工具]
summary: Obsidian MCP Server - 将 Obsidian 笔记库暴露为 MCP 服务，让 AI 助手可以搜索和读取笔记
folder: 知识点/04-人工智能/MCP/自己制作的MCP/
created: 2024-12-19
---

# Obsidian MCP Server

## 项目概述

将 Obsidian 笔记库暴露为 MCP 服务，让 AI 助手（如 Claude、Windsurf）可以搜索和读取你的笔记。

- **包名**: `@andysama/obsidian-mcp-server`
- **版本**: 1.0.0
- **仓库**: https://github.com/andysama-work/obsidian-mcp-server
- **协议**: MIT

## 功能列表

| 工具 | 描述 |
|------|------|
| `search_notes` | 按关键词、标签、分类搜索笔记 |
| `read_note` | 读取指定笔记的完整内容 |
| `list_folder` | 列出文件夹下的笔记和子文件夹 |
| `get_note_structure` | 获取笔记库目录结构 |
| `full_text_search` | 在所有笔记中全文搜索 |

## 技术栈

- **语言**: TypeScript
- **运行时**: Node.js
- **核心依赖**:
  - `@modelcontextprotocol/sdk` - MCP SDK
  - `gray-matter` - YAML Frontmatter 解析
  - `glob` - 文件匹配

## 安装方式

### 方式一：直接使用（推荐）

无需安装，直接在 MCP 配置中使用 `npx`：

```json
{
  "mcpServers": {
    "obsidian-notes": {
      "command": "npx",
      "args": [
        "-y",
        "@andysama/obsidian-mcp-server",
        "--vault",
        "/path/to/your/obsidian/vault"
      ]
    }
  }
}
```

### 方式二：全局安装

```bash
npm install -g @andysama/obsidian-mcp-server
```

### 方式三：从源码构建

```bash
git clone https://github.com/andysama-work/obsidian-mcp-server.git
cd obsidian-mcp-server
npm install
npm run build
```

## 配置示例

### Claude Desktop

编辑配置文件：
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`
- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "obsidian-notes": {
      "command": "node",
      "args": [
        "/path/to/obsidian-mcp-server/dist/index.js",
        "--vault",
        "/path/to/your/obsidian/vault"
      ]
    }
  }
}
```

### Windsurf / Cursor

在 MCP 配置文件中添加相同配置。

## 使用示例

配置完成后，AI 助手可以：

- **搜索笔记**: `搜索关于 STM32 的笔记`
- **读取内容**: `读取 STM32系列选型速查.md`
- **浏览结构**: `列出硬件学习文件夹的内容`
- **全文搜索**: `在笔记中搜索 "定时器"`

## Frontmatter 支持

本工具会解析笔记的 YAML Frontmatter，支持以下字段：

```yaml
---
category: hardware
tags: [STM32, 嵌入式]
summary: 笔记摘要
folder: 知识点/03-硬件学习/
created: 2024-12-18
---
```

## 本地路径

项目位置: `D:\AI\MCP\obsidian-mcp-server`
