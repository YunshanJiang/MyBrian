---
tags:
  - Rhino
  - 快捷键
---

# Rhino 选取与视图快捷键

| 操作 | 快捷键 / 命令 | 用法 |
|---|---|---|
| 聚焦选中物体 | `ZS` | 先选中一个或多个物体，在命令行输入 `ZS` 并回车（Zoom Selected）。 |
| 选取子物件的点、边、面 | `Ctrl + Shift + 左键单击` | 按住组合键后点击物件上的顶点、边或面。可用于多重曲面、网格和 SubD 等物件；可选子元素取决于几何类型。 |
| 切换子物件选择过滤器 | `F5` | 循环切换面、边、点/顶点/控制点等选择过滤器。 |
| 显示曲线或曲面的控制点 | `F10` | 先选中曲线或曲面，再按 F10 显示控制点。 |
| 隐藏控制点 | `F11` | 关闭控制点显示。 |

**注意：** `ZS` 是 Rhino 的命令别名，需要在命令行输入并回车；它不是单独的键盘按键。`Ctrl + Shift + 点击` 选的是物件子元素；`F10` 显示的是曲线/曲面的控制点，两者用途不同。

## 参考

- [Rhino 8：对象与子对象选择](https://docs.mcneel.com/rhino/8/help/en-us/commands/selection_commands.htm?Highlight=select+all)
- [Rhino 8：选择过滤器](https://docs.mcneel.com/rhino/8/help/en-us/commandlist/command_list.htm)
- [Rhino 8：PointsOn / PointsOff](https://docs.mcneel.com/rhino/8/help/en-us/commands/pointson.htm)
- [Rhino 8：Zoom](https://docs.mcneel.com/rhino/8/help/en-us/unfurl/zoom.htm)

## 添加参考图

1. 切换到要放置参考图的视口（例如 Top、Front 或 Right）。
2. 在命令行输入 `Picture` 并回车，选择图片文件。
3. 在视口中点击图片平面的第一个角，再点击另一个角；也可以输入长度。图片会保持原始长宽比。

`Picture` 会创建一个带图片材质的平面，可在模型中移动和缩放。

参考：[Rhino 8：Picture 命令](https://docs.mcneel.com/rhino/8/help/en-us/commands/picture.htm)

## 网格捕捉

- **F9**：切换 Grid Snap（网格捕捉）开/关。缩放或拖动时若总按固定网格间距跳动，可关闭它。
- 也可以点击 Rhino 窗口底部状态栏的 **Grid Snap** 开关。
- Grid Snap 与 **Osnap**（物件捕捉）是不同设置。

参考：[Rhino 8：Snap / Grid Snap](https://docs.mcneel.com/rhino/8mac/help/en-us/commands/snap.htm)
## 检查 Watertight（封闭性）

- **多重曲面 / NURBS 实体**：选中物体，输入 `What`；确认结果为 `Valid polysurface` 和 `Closed solid polysurface`。也可按 `F3` 打开 Properties，在 Details 中查看。
- **网格或 SubD**：选中物体，输入 `ShowEdges`，查看 `Naked edges`。有裸边高亮表示存在开口；网格还应检查 `Non-manifold edges`，确保没有非流形边。

参考：[Rhino 8：ShowEdges](https://docs.mcneel.com/rhino/8/help/en-us/commands/showedges.htm) · [Rhino User Guide：检查实体是否封闭](https://docs.mcneel.com/rhino/8/training-command/en-us/usersguide/Rhino%20User%27s%20Guide%20for%20Windows.pdf)

## 锁定物体，防止移动

1. 先选中整个物体（不要只选点、边或面）。
2. 按 `Ctrl + L`，或输入 `Lock` 并回车。物体仍然可见，但不能被选中编辑或移动。
3. 要只解锁一个物体，按 `Ctrl + Shift + L`（`UnlockSelected`），点选目标物体并按 Enter。`Ctrl + Alt + L` 会解锁全部锁定物体。

参考：[Rhino 8：Lock / Unlock / UnlockSelected](https://docs.mcneel.com/rhino/8/help/en-us/commands/lock.htm)

