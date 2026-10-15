---
tags:
  - Rhino
  - 快捷键
  - 建模操作
updated: 2026-10-16
---

# Rhino 快捷键与建模操作

> 合并原有的两篇 Rhino 笔记。按内容更新时间倒序整理：2026-10-16、2026-10-15；未标注日期的原有常用条目单独保留。

## 2026-10-16｜快捷键与建模操作

### 快捷键

| 快捷键 / 命令 | 用途 |
|---|---|
| `F8` | 切换 Ortho 正交约束；对齐镜像轴时辅助保持水平或垂直。 |
| `F10` | 显示曲线/曲面的控制点（PointsOn）。 |
| `F11` | 隐藏控制点（PointsOff）。 |
| `SetPt` | 改点坐标；没有默认单键快捷键，在命令行输入。 |
| `Mirror`、`Split`、`Fillet`、`TextObject`、`ChangeLayer` | 直接在 Rhino 命令行输入命令。 |

### 让曲线上的点横向对齐

1. 切到 `Top` 视图。
2. 选中要移动的点/控制点，运行 `SetPt`。
3. 只启用 `Set Y`，选择 `World`（或需要时选 `CPlane`），再捕捉参考点。
4. Top 视图中相同 `Y` 坐标就是同一水平线；Front 视图里横向对齐通常对应相同 `Z`。

### 在曲线上已有的点处分割曲线

1. 输入 `Split`，选择曲线并回车。
2. 在切割选项中选 `Point`，用 Osnap 的 `Point` 捕捉放在曲线上的点。
3. 回车完成。`Split` 会保留两段；只要一段时，删除另一段。

### 减少曲线控制点

- Rhino 不会把 NURBS 曲线的两个控制点焊接成一个。要少一个点，按 `F10` 后选中多余控制点并按 `Delete`，或运行 `RemoveControlPoint`。
- 删除控制点会改变曲线形状；要整体减少控制点，可用 `Rebuild` 并预览偏差。
- `F10` 显示控制点；`EditPtOn` 显示的曲线编辑点是另一类点。

### 只圆一个拐角

- `FilletCorners` 会圆所选多段线/复合曲线上的所有拐角。
- 只圆平面轮廓的一个角：先 `Explode`，再运行 `Fillet`，依次选择目标拐角相邻的两段（点击位置靠近拐角），设置半径并用 `Trim=Yes`、`Join=Yes`；完成后可再 `Join`。
- 如果是挤出实体的边，用 `FilletEdge`，只选择目标边。

### 镜像曲线

1. 选曲线，输入 `Mirror`。
2. 指定镜像轴的起点和终点；确认 `Copy=Yes` 可保留原曲线并生成副本。
3. Top 视图中，`XAxis` 是水平轴、`YAxis` 是垂直轴；自定义轴可用 `F8` 辅助定向。

### 创建文字曲线、加粗和增加凸起

- 输入 `TextObject`，把 `Output` 设为 `Curves`，得到可编辑的文字轮廓；普通 `Text` 命令创建的是标注文字。
- 创建时可以选择 `Bold` / `Black` 字体。已有文字曲线不能直接切换字体粗细。
- 已有轮廓要按数值加粗：选中文字闭合轮廓，运行 `OffsetMultiple`，例如先试 `0.2 mm`，在字形外侧指定方向。嵌套内孔会向相反方向偏移，空腔会缩小；检查小空腔不要封死。
- 沿 Z 向挤出是增加立体高度，不是加粗笔画。钥匙链文字要凸起 2 mm 时，底板顶面在 Z=3 mm，文字应从顶面附近向上挤出；若要布尔并体，让文字与底板略微相交。

### 将对象放到图层

- 在 Layers 面板选中目标图层，右键选择 `Change Object Layer`；或选对象后运行 `ChangeLayer` 并选择目标图层。
- 若已选中对象，也可运行 `ChangeToCurrentLayer`。未选对象时点击图层，只会把它设为新对象的当前图层。

## 2026-10-15｜机器人钥匙链模型

- 图纸关键尺寸：孔中心到右端 60 mm、牌身高 25 mm、底板厚 3 mm、字凸起 2 mm、外耳 Ø8 mm、孔 Ø4 mm；示例文字 `ROBOT`。
- 已在原有 Rhino 实例中通过 RhinoCode CLI 建模并保存：
  - 3DM：`F:\Codex\RobotOnStageCourse\robot_keychain.3dm`
  - STL：`F:\Codex\RobotOnStageCourse\robot_keychain.stl`
- 成品为一个封闭实体；未注圆角过渡按平滑曲线近似。

## 原有快捷键与常用操作｜原始更新时间未注明

| 操作 | 快捷键 / 命令 | 用法 |
|---|---|---|
| 聚焦选中物体 | `ZS` | 选物体后在命令行输入 `ZS` 并回车（Zoom Selected）；这是命令别名，不是单独按键。 |
| 选取子物件的点、边、面 | `Ctrl + Shift + 左键单击` | 按住组合键点击物件上的顶点、边或面；可选类型取决于几何类型。 |
| 切换子物件选择过滤器 | `F5` | 循环切换面、边、点/顶点/控制点等过滤器。 |
| 网格捕捉 | `F9` | 切换 Grid Snap；与 Osnap（物件捕捉）不同，也可点击状态栏的 Grid Snap。 |

### 添加参考图

1. 切换到要放置参考图的视口（例如 Top、Front 或 Right）。
2. 输入 `Picture`，选择图片文件。
3. 点击图片平面的两个角，或输入长度；图片保持原始长宽比。

`Picture` 会创建一个带图片材质的平面，可在模型中移动和缩放。

### 检查 Watertight（封闭性）

- **多重曲面 / NURBS 实体**：选中物体，输入 `What`；确认是 `Valid polysurface` 和 `Closed solid polysurface`。也可按 `F3` 打开 Properties 查看。
- **网格或 SubD**：选中物体，输入 `ShowEdges` 查看 `Naked edges`；网格还要检查 `Non-manifold edges`。

### 锁定物体，防止移动

1. 选中整个物体（不要只选点、边或面）。
2. 按 `Ctrl + L` 或输入 `Lock`。物体仍可见，但不能被选中编辑或移动。
3. 只解锁一个物体：按 `Ctrl + Shift + L`（`UnlockSelected`），点选目标物体并回车。`Ctrl + Alt + L` 解锁全部锁定物体。

## McNeel 官方参考

- [对象与子对象选择](https://docs.mcneel.com/rhino/8/help/en-us/commands/selection_commands.htm?Highlight=select+all)
- [选择过滤器](https://docs.mcneel.com/rhino/8/help/en-us/commandlist/command_list.htm)
- [PointsOn / PointsOff](https://docs.mcneel.com/rhino/8/help/en-us/commands/pointson.htm)
- [Zoom](https://docs.mcneel.com/rhino/8/help/en-us/unfurl/zoom.htm)
- [Picture](https://docs.mcneel.com/rhino/8/help/en-us/commands/picture.htm)
- [Grid Snap](https://docs.mcneel.com/rhino/8mac/help/en-us/commands/snap.htm)
- [ShowEdges](https://docs.mcneel.com/rhino/8/help/en-us/commands/showedges.htm)
- [Lock / Unlock / UnlockSelected](https://docs.mcneel.com/rhino/8/help/en-us/commands/lock.htm)
- [SetPt](https://docs.mcneel.com/rhino/8/help/en-us/commands/setpt.htm)
- [Split](https://docs.mcneel.com/rhino/8/help/en-us/commands/split.htm)
- [RemoveControlPoint / Rebuild](https://docs.mcneel.com/rhino/8/help/en-us/commands/removeknot.htm)
- [Fillet / FilletCorners](https://docs.mcneel.com/rhino/8/help/en-us/commands/fillet.htm)
- [Mirror](https://docs.mcneel.com/rhino/8/help/en-us/commands/mirror.htm)
- [TextObject](https://docs.mcneel.com/rhino/8/help/en-us/commands/textobject.htm)
- [OffsetMultiple](https://docs.mcneel.com/rhino/8/help/en-us/commands/offsetmultiple.htm)
- [ChangeLayer](https://docs.mcneel.com/rhino/8/help/en-us/commands/changelayer.htm)
