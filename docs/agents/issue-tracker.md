# Issue tracker：本地 Markdown

本仓库的 issue 和规格以 Markdown 文件形式存放在 `.scratch/` 中。

## 约定

- 每个功能使用一个目录：`.scratch/<feature-slug>/`
- 规格文件为 `.scratch/<feature-slug>/spec.md`
- 每张实现工单单独存放在 `.scratch/<feature-slug>/issues/<NN>-<slug>.md`，从 `01` 开始编号，不使用合并的工单文件
- Triage 状态记录在 issue 文件顶部附近的 `Status:` 行中；角色字符串参见 `triage-labels.md`
- 评论和讨论历史追加到文件底部的 `## Comments` 标题下

## 当技能要求“发布到 issue tracker”时

在 `.scratch/<feature-slug>/` 下创建新文件；目录不存在时一并创建。

## 当技能要求“获取相关工单”时

读取所引用路径下的文件。用户通常会直接提供路径或 issue 编号。

## Wayfinding 操作

供 `/wayfinder` 使用。一个 **map** 文件对应每张工单的一个 **child** 文件。

- **Map**：`.scratch/<effort>/map.md`，包含 Notes、Decisions-so-far 和 Fog 正文
- **Child ticket**：`.scratch/<effort>/issues/NN-<slug>.md`，从 `01` 开始编号，正文中记录问题；`Type:` 行记录工单类型（`research`、`prototype`、`grilling` 或 `task`），`Status:` 行记录 `claimed` 或 `resolved`
- **阻塞关系**：在文件顶部附近使用 `Blocked by: NN, NN`；所列文件全部为 `resolved` 后，该工单解除阻塞
- **Frontier**：扫描 `.scratch/<effort>/issues/`，查找开放、未阻塞且无人认领的文件；编号最小者优先
- **认领**：开始工作前，将 `Status:` 设置为 `claimed` 并保存
- **解决**：将答案追加到 `## Answer` 标题下，把 `Status:` 设置为 `resolved`，然后把上下文指针（摘要和链接）追加到 `map.md` 的 Decisions-so-far
