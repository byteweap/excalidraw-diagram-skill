# Excalidraw Diagram Skill

一个面向 AI 编码代理的通用 Excalidraw 制图 skill，用来稳定生成简洁、美观、可编辑的 `.excalidraw` 文件，并提供轻量的 PNG 导出指引。

[开源仓库](https://github.com/byteweap/excalidraw-diagram-skill) ・ [Skill 定义](./SKILL.md) ・ [示例目录](./examples)

## 特性

- 适用于流程图、架构图、模块关系图、组件图、交互说明图
- 支持 `普通风格` 和 `手绘风格`
- 输出完整 `.excalidraw` JSON，而不是零散片段
- 控制文字安全边距，减少压边和编辑态裁切
- 使用绑定箭头，拖动节点时连线可跟随
- 提供 PNG 导出建议，但不依赖脚本渲染

## 适合谁用

- 使用 Codex、Claude Code、Cursor、Cline、OpenCode 等代理生成图
- 需要继续在 Excalidraw 中编辑源文件
- 希望图形风格统一、布局稳定、交互更可靠

## 仓库结构

- [SKILL.md](./SKILL.md)：核心 skill 说明
- [references](./references)：风格规则、图形模式、自检规则
- [examples](./examples)：示例文件，按题材提供普通版和手绘版

## 快速开始

先克隆仓库：

```bash
git clone https://github.com/byteweap/excalidraw-diagram-skill.git
```

然后在 Codex 中显式引用本地 skill 路径。

普通风格架构图：

```text
使用 excalidraw-diagram-skill 生成一个普通风格的系统架构图。
内容包括：Web Client、API Gateway、Core Service、Database。
要求长标签不要压边。
请输出完整 .excalidraw 文件，文件名为 architecture.excalidraw。
```

手绘风格流程图：

```text
使用 excalidraw-diagram-skill 生成一个手绘风格的审批流程图。
步骤包括：提交申请、经理审批、执行发布。
要求长标签不要压边。
请输出完整 .excalidraw 文件，并附上 PNG 导出说明。
```

带长标签的模块图：

```text
使用 excalidraw-diagram-skill 生成一个普通风格的模块关系图。
要求长标签不要压边，拖动节点时连线要跟随。
请输出完整 .excalidraw 文件。
```

## 使用提示

- 需要草图感时，明确写“手绘风格”或 `hand-drawn`
- 需要正式文档风格时，明确写“普通风格”或 `normal`
- 节点连线默认会绑定到节点，拖动时会自动跟随
- 如果需要 PNG，建议先生成 `.excalidraw`，再导入 Excalidraw 导出

## 示例

### 流程图

- 手绘版：[flowchart-basic.excalidraw](./examples/flowchart-basic.excalidraw)
- 普通版：[flowchart-normal.excalidraw](./examples/flowchart-normal.excalidraw)

### 架构图

- 普通版：[architecture-basic.excalidraw](./examples/architecture-basic.excalidraw)
- 手绘版：[architecture-hand-drawn.excalidraw](./examples/architecture-hand-drawn.excalidraw)

### 模块图

- 普通版：[module-map-basic.excalidraw](./examples/module-map-basic.excalidraw)
- 手绘版：[module-map-hand-drawn.excalidraw](./examples/module-map-hand-drawn.excalidraw)
