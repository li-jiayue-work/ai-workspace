# ai-workspace

基于 Claude Code 搭建的个人多项目工作区，用于 AI 辅助开发的日常干活场所。

## 工作区结构

```
active/      ← 活跃开发中的项目
archive/     ← 已完成或暂停的项目
agents/      ← 自定义 Agent、MCP 配置
workflows/   ← 标准流程定义
templates/   ← 项目模板
snippets/    ← 可复用代码片段
learning/    ← 学习笔记
assets/      ← 图片素材
memory/      ← 跨会话持久记忆
```

## 主要产出

- 个人作品集网站（Next.js + Tailwind）
- 亚马逊畅销书市场分析（Python 数据分析）
- 亚马逊印度电商商品分析（Python 数据分析）
- 30+ HTML 模板库

## 工作方式

根目录 CLAUDE.md 定义全局规范，在任何子目录执行 Claude Code 时自动加载上下文。
