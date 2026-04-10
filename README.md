# Excalidraw Diagram Skill

一个面向 AI 编码代理的通用 Excalidraw 制图 skill。  
它帮助代理稳定生成简洁、美观、可编辑的 `.excalidraw` 文件，并给出轻量的 PNG 导出指引。

## 它能做什么

- 生成流程图、架构图、模块关系图、组件图、交互说明图
- 支持两种风格：
  - `普通风格`：更规整、专业，适合正式文档
  - `手绘风格`：保留 Excalidraw 草图感，但仍保持整洁
- 输出完整 `.excalidraw` JSON，而不是零散片段
- 控制文字安全边距，避免文字压边、双击编辑时裁切
- 要求节点连线使用绑定箭头，拖动节点时连线可跟随
- 提供 PNG 导出建议，但不依赖脚本渲染

## 适用场景

- 用 Codex、Claude Code、Cursor、Cline、OpenCode 等代理生成图
- 需要可继续编辑的 Excalidraw 源文件
- 希望图风格统一、结构清晰、少踩交互细节坑

## 仓库结构

- [SKILL.md](C:/work/codes/Art/excalidraw-diagram-skill/SKILL.md)：skill 主说明
- [references](C:/work/codes/Art/excalidraw-diagram-skill/references)：风格、图形模式、自检规则
- [examples](C:/work/codes/Art/excalidraw-diagram-skill/examples)：示例文件，包含每个题材的普通版和手绘版

## 如何使用

以 Codex 为例，推荐直接在提示中显式引用这个 skill，并说明图类型、内容、风格和输出文件名。

示例 1：普通风格架构图

```text
使用 C:\work\codes\Art\excalidraw-diagram-skill 的 excalidraw-diagram-skill，
生成一个普通风格的系统架构图。
内容包括：Web Client、API Gateway、Core Service、Database。
请输出完整 .excalidraw 文件，文件名为 architecture.excalidraw。
```

示例 2：手绘风格流程图

```text
使用 C:\work\codes\Art\excalidraw-diagram-skill 的 excalidraw-diagram-skill，
生成一个手绘风格的审批流程图。
步骤包括：提交申请、经理审批、执行发布。
请输出完整 .excalidraw 文件，并附上 PNG 导出说明。
```

示例 3：带长标签的模块图

```text
使用 C:\work\codes\Art\excalidraw-diagram-skill 的 excalidraw-diagram-skill，
生成一个普通风格的模块关系图。
要求长标签不要压边，拖动节点时连线要跟随。
请输出完整 .excalidraw 文件。
```

## 使用建议

- 想要手绘效果时，明确写“手绘风格”或 `hand-drawn`
- 想要正式文档风格时，明确写“普通风格”或 `normal`
- 如果图里节点可移动，最好明确要求“连线绑定节点”
- 如果需要 PNG，建议先生成 `.excalidraw`，再导入 Excalidraw 导出 PNG

## 示例

- 流程图手绘版：[flowchart-basic.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/flowchart-basic.excalidraw)
- 流程图普通版：[flowchart-normal.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/flowchart-normal.excalidraw)
- 架构图普通版：[architecture-basic.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/architecture-basic.excalidraw)
- 架构图手绘版：[architecture-hand-drawn.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/architecture-hand-drawn.excalidraw)
- 模块图普通版：[module-map-basic.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/module-map-basic.excalidraw)
- 模块图手绘版：[module-map-hand-drawn.excalidraw](C:/work/codes/Art/excalidraw-diagram-skill/examples/module-map-hand-drawn.excalidraw)
