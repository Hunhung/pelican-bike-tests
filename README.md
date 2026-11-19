# 鹈鹕骑车动画 —— 模型横向对比测试

同一条指令，在 9 个不同模型/档位上各跑一次，对比各自的 SVG 动画代码生成能力。

## 测试指令（所有测试共用）

> 创建一个 html，内容是用 svg 绘制一个鹈鹕骑自行车的 2d 动画

产出均为**纯手写 SVG + CSS 动画**（视差云层、滚动路面、车轮/脚踏旋转等），不是 AI 生成的位图。
所以对比的是**文本模型的代码生成能力**，而非绘图模型。

## 怎么看动画

GitHub 默认把 `.html` 当**源代码**显示，不会执行里面的动画。要看动画请点表格里的 **「▶ 看动画」** 链接（走在线预览）；「源码」链接才是原始文件。

> 想换成官方稳定链接：在仓库 **Settings → Pages → Source 选 main → Save**，开启后把下面的 `htmlpreview.github.io/?https://github.com/...` 换成 `https://hunhung.github.io/pelican-bike-tests/<文件名>` 即可，点开即播。

## 横向对比表

> **思考强度说明**：系统没有把界面上选择的档位（低/中/高）写进记录，无法直接读取。
> 下表改用**首轮生成所消耗的推理 token 数（reasoning tokens）**作为可量化的参考指标——
> 数值越高，代表该次生成实际"想得越多"。注意这不完全等于档位（也受模型实现和任务复杂度影响），
> 且个别模型（如 Qwen）不回报该指标，记为 0，不代表没有思考。

| # | 测试时间 | 模型 | 推理 token（思考强度参考） | AI 平台 | 问题备注 | 看动画 / 源码 |
|---|---|---|---|---|---|---|
| 1 | 2026-11-15 23:29 | 均衡（档位） | 132 | WorkBuddy · CLI | 基准档位；输出最简短 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test01_20261115-2330_balanced.html) · [源码](test01_20261115-2330_balanced.html) |
| 2 | 2026-11-15 23:38 | DeepSeek-V4.1-Flash | 13,878 | WorkBuddy · CLI | 多次改写（20 次写操作） | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test02_20261115-2338_deepseek-v4.1-flash.html) · [源码](test02_20261115-2338_deepseek-v4.1-flash.html) |
| 3 | 2026-11-15 23:40 | 快速（档位） | 24,023 | WorkBuddy · CLI | 推理量最高之一，但耗时短 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test03_20261115-2340_fast.html) · [源码](test03_20261115-2340_fast.html) |
| 4 | 2026-11-15 23:40 | DeepSeek-V4.1-Flash | 19,717 | WorkBuddy · CLI | 与第 2 条同模型，写操作最多（52 次） | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test04_20261115-2340_deepseek-v4.1-flash.html) · [源码](test04_20261115-2340_deepseek-v4.1-flash.html) |
| 5 | 2026-11-15 23:41 | Hy4 | 4,647 | WorkBuddy · CLI | 文件最丰富（26K），细节较多 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test05_20261115-2341_hy4.html) · [源码](test05_20261115-2341_hy4.html) |
| 6 | 2026-11-15 23:45 | GLM-5.3-Flash | 87 | WorkBuddy · CLI | 推理量极低，几乎直接输出 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test06_20261115-2345_glm-5.3-flash.html) · [源码](test06_20261115-2345_glm-5.3-flash.html) |
| 7 | 2026-11-16 00:01 | Qwen3.8-Flash-Next | 0（未回报） | WorkBuddy · CLI | 唯一追加提问"？"的一次；不回报推理 token | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test07_20261116-0001_qwen3.8-flash-next.html) · [源码](test07_20261116-0001_qwen3.8-flash-next.html) |
| 8 | 2026-11-16 00:06 | Hy3 | 6,171 | WorkBuddy · CLI | 有对应预览截图 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test08_20261116-0006_hy3.html) · [源码](test08_20261116-0006_hy3.html) |
| 9 | 2026-11-16 00:16 | DeepSeek-V4.1-Flash | 24,424 | WorkBuddy · CLI | 推理 token 最高的一次 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test10_20261116-0016_deepseek-v4.1-flash.html) · [源码](test10_20261116-0016_deepseek-v4.1-flash.html) |
| 10 | 2026-11-16 10:58 | 未记录（下载副本） | 无法读取 | 未记录 | Downloads 中的副本，原会话信息已丢失 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test11_20261116-1058_unknown.html) · [源码](test11_20261116-1058_unknown.html) |

预览截图：[preview_20261116-0006_hy3.png](preview_20261116-0006_hy3.png)（对应第 8 条 Hy3）

## 逐条审查清单

> 核对每条动画时对照下面的清单逐项检查，结果填到后面的记录表中。

**A. 鹈鹕本体**
- [ ] 形态正确（能看出是鹈鹕：长喙、大喉囊、白色羽毛）
- [ ] 嘴巴 / 喙的位置与朝向正常
- [ ] 翅膀、羽毛形态自然
- [ ] 身体比例协调

**B. 自行车结构**
- [ ] 车架完整（两个轮子 + 车架 + 车把 + 坐垫）
- [ ] 各部件连接正确，没有飞出去 / 断裂 / 悬空

**C. 骑行姿态**
- [ ] 鹈鹕的屁股坐在坐垫上
- [ ] 双脚踩在踏板上（不脱离）
- [ ] 膝盖 / 腿部弯曲符合踩踏逻辑

**D. 运动与传动逻辑**
- [ ] 踏板与车轮都在正常转动
- [ ] 车轮滚动方向正确（与前进方向一致）
- [ ] 踏板转速与车轮转速合理匹配
- [ ] 链条正确移动（如果画了链条）

**E. 场景与整体**
- [ ] 地面向后移动（表示正在前进）
- [ ] 背景 / 视差移动方向一致
- [ ] 整个画面符合物理逻辑

## 我的审查记录（手动填写）

> 每一项填 `✓`（正常）/ `✗`（有问题）/ `？`（看不清），异常的具体表现写进「发现的问题」。

| # | 模型 | A 鹈鹕本体 | B 车架结构 | C 骑行姿态 | D 运动传动 | E 场景整体 | 发现的问题 | 结论 |
|---|---|---|---|---|---|---|---|---|
| 1 | 均衡 |  |  |  |  |  |  |  |
| 2 | DeepSeek-V4.1-Flash |  |  |  |  |  |  |  |
| 3 | 快速 |  |  |  |  |  |  |  |
| 4 | DeepSeek-V4.1-Flash |  |  |  |  |  |  |  |
| 5 | Hy4 |  |  |  |  |  |  |  |
| 6 | GLM-5.3-Flash |  |  |  |  |  |  |  |
| 7 | Qwen3.8-Flash-Next |  |  |  |  |  |  |  |
| 8 | Hy3 |  |  |  |  |  |  |  |
| 9 | DeepSeek-V4.1-Flash |  |  |  |  |  |  |  |
| 10 | 未记录 |  |  |  |  |  |  |  |

## 快速观察

- **推理量最高**：DeepSeek-V4.1-Flash（00:16，24,424）和「快速」档位（24,023）——生成前想得最多。
- **推理量最低**：GLM-5.3-Flash（87）、均衡档位（132）——几乎不假思索直接出代码。
- **同模型对比**：DeepSeek-V4.1-Flash 跑了 3 次（第 2/4/9 条），推理量在 13.8k～24.4k 之间波动。
- **档位 vs 模型**：「均衡」「快速」是产品内的档位名称，不是具体模型名；其余为模型版本号。
- **代码丰富度与推理量不完全正相关**：Hy4 推理量中等，但文件最丰富（26K）。

## 口径说明

- **测试时间**取自各会话第一条消息的发出时间（比文件修改时间更接近真实测试时刻）。
- **推理 token**取自该会话首轮生成（创建 HTML 那一步）的 `reasoning_tokens`。
- **AI 平台**：全部在 WorkBuddy 的 CLI 客户端中运行（记录中的 `agent = cli`）。
- **思考强度档位**（低/中/高）未被系统写入记录，故无法直接显示，以推理 token 作为替代指标。
- 原始文件仍保留在各自的工作区目录中，本仓库为整理后的副本，未删除任何原文件。
