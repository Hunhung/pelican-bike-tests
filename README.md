# 鹈鹕骑车动画 —— 跨平台 / 跨模型横向对比测试

同一条指令，在 **4 个 AI 平台**（WorkBuddy CLI、同济人工智能平台 API、豆包桌面端 Agent、ChatGPT Work）上的多个模型 / 档位进行测试，**共 18 条**，对比各自的 SVG 动画代码生成能力。

## 测试指令（所有测试共用）

> 创建一个 html，内容是用 svg 绘制一个鹈鹕骑自行车的 2d 动画

产出均为**纯手写 SVG + CSS / JavaScript 动画**（视差云层、滚动路面、车轮/脚踏旋转等），不是 AI 生成的位图。
所以对比的是**文本模型的代码生成能力**，而非绘图模型。

## 怎么看动画

GitHub 默认把 `.html` 当**源代码**显示，不会执行里面的动画。要看动画请点表格里的 **「▶ 看动画」** 链接（走在线预览）；「源码」链接才是原始文件。

> 想换成官方稳定链接：在仓库 **Settings → Pages → Source 选 main → Save**，开启后把下面的 `htmlpreview.github.io/?https://github.com/...` 换成 `https://hunhung.github.io/pelican-bike-tests/<文件名>` 即可，点开即播。

## 横向对比表（18 条，按平台 / 模型横向比较）

> **思考强度说明**：早期记录未保存界面上选择的档位（低/中/高），无法直接读取。
> 下表用**首轮生成所消耗的推理 token 数（reasoning tokens）**作为可量化参考——数值越高代表该次生成实际"想得越多"。
> 注意这不完全等于档位（也受模型实现和任务复杂度影响）；个别模型（如 Qwen）不回报该指标，记为 0；豆包桌面端的 4 条、ChatGPT Work 的 2 条无推理 token 记录，记为「未记录」。ChatGPT Work 的思考档位由用户补充。
>
> **问题备注来源**：18 条全部是用户逐条观看动画后的**视觉审查结论**。豆包侧提供的源码核对描述另见文末「逐条详细备注」，仅供参照，不作为效果结论。

| # | 测试时间 | AI 平台 | 模型 / 档位 | 思考强度（推理 token） | 问题备注 | 看动画 / 源码 |
|---|---|---|---|---|---|---|
| 1 | 2026-11-15 23:29 | WorkBuddy · CLI | 均衡（GLM5.3，档位） | 132 | 轮子起飞，鹈鹕造型一般；腿和脚断连、车没有踏板；链条逻辑出错连在前轮；轮子飞到天上，自行车整体造型完全丢失，效果极差 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test01_20261115-2330_balanced.html) · [源码](test01_20261115-2330_balanced.html) |
| 2 | 2026-11-15 23:38 | 同济人工智能平台（API 接入） | DeepSeek-V4.1-Flash | 13,878 | 脚不在踏板上，踏板转动错误，膝盖逻辑错误 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test02_20261115-2338_deepseek-v4.1-flash.html) · [源码](test02_20261115-2338_deepseek-v4.1-flash.html) |
| 3 | 2026-11-15 23:40 | WorkBuddy · CLI | 快速（档位） | 24,023 | 效果出色，无明显逻辑错误 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test03_20261115-2340_fast.html) · [源码](test03_20261115-2340_fast.html) |
| 4 | 2026-11-15 23:40 | WorkBuddy · CLI（自带） | DeepSeek-V4.1-Flash | 19,717 | 无明显错误，屁股轻微离开板凳 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test04_20261115-2340_deepseek-v4.1-flash.html) · [源码](test04_20261115-2340_deepseek-v4.1-flash.html) |
| 5 | 2026-11-15 23:41 | WorkBuddy · CLI | Hy4 | 4,647 | 鹈鹕造型有点丑，踏板穿模 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test05_20261115-2341_hy4.html) · [源码](test05_20261115-2341_hy4.html) |
| 6 | 2026-11-15 23:45 | WorkBuddy · CLI | GLM-5.3-Flash | 87 | 鸟严重变形且身体部分分开，腿画错、脚和腿分开；地面运动反了，自行车结构错误，踏板运动不合逻辑，有一只脚粘在踏板上，效果极差 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test06_20261115-2345_glm-5.3-flash.html) · [源码](test06_20261115-2345_glm-5.3-flash.html) |
| 7 | 2026-11-16 00:01 | 同济人工智能平台（API 接入） | Qwen3.8-Flash-Next | 0（未回报） | 轮子转动错误且不在自行车上，踏板乱转；“鹈鹕”两个字都没写对；脚乱踩且不是骑车动作；自行车结构丢失，运动不连贯，效果极差 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test07_20261116-0001_qwen3.8-flash-next.html) · [源码](test07_20261116-0001_qwen3.8-flash-next.html) |
| 8 | 2026-11-16 00:06 | WorkBuddy · CLI | Hy3 | 6,171 | 脚和踏板穿模，图层关系不对 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test08_20261116-0006_hy3.html) · [源码](test08_20261116-0006_hy3.html) |
| 9 | 2026-11-16 00:16 | 同济人工智能平台（API 接入） | DeepSeek-V4.1-Flash | 24,424 | 脚穿模，地面运动方向错误 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test10_20261116-0016_deepseek-v4.1-flash.html) · [源码](test10_20261116-0016_deepseek-v4.1-flash.html) |
| 10 | 2026-11-16 10:58 | 未记录（下载副本） | 未记录 | 无法读取 | 地面运动方向不对 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/test11_20261116-1058_unknown.html) · [源码](test11_20261116-1058_unknown.html) |
| 11 | 2026-11-19 18:50 | 豆包桌面端 Agent | DeepSeek-V4.1-Flash（用户补充） | 未记录 | 轮子内部不完整。鹈鹕没有手动作错误，脚穿模，踏板穿模围巾断掉了 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/p01-sunset-ik-20261119.html) · [源码](p01-sunset-ik-20261119.html) |
| 12 | 2026-11-19 18:36 | 豆包桌面端 Agent | 豆包 2.1 Pro（用户补充） | 未记录 | 鹈鹕没有手动作错误，地面运动方向不对，鹈鹕嘴巴太大，踏板穿模，膝盖动作不够顺畅 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/p02-gear-ik-20261119.html) · [源码](p02-gear-ik-20261119.html) |
| 13 | 2026-11-19 18:32 | 豆包桌面端 Agent | 豆包 2.1 Lite（用户补充） | 未记录 | 腿和身体严重分离，鹈鹕动作错误，踏板不完整。踏板和脚穿模。没有链条 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/p03-pedal-fix-20261119.html) · [源码](p03-pedal-fix-20261119.html) |
| 14 | 2026-11-16 00:25 | 豆包桌面端 Agent | 未记录（豆包未披露） | 未记录 | 鹈鹕动作错误，踏板和脚转动错误。轮子速度太快。 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/p04-poster-raf-20261116.html) · [源码](p04-poster-raf-20261116.html) |
| 15 | 2026-11-19 23:18 | WorkBuddy · CLI | Kimi-K3.1-Pro | 8,435 | 出色，无明显逻辑问题 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/p15-kimi-k3.1-pro-20261119.html) · [源码](p15-kimi-k3.1-pro-20261119.html) |
| 16 | 2026-11-19 23:17 | WorkBuddy · CLI | Space-Bunny | 19,980 | 腿穿模，链条转动方向错误，踏板连接不完整，屁股没挨着椅子 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/p16-space-bunny-20261119.html) · [源码](p16-space-bunny-20261119.html) |
| 17 | 2026-11-26 16:00 | ChatGPT · Work | GPT-6.2 Sol（中） | 未记录 | 腿穿模，图层错误，踏板穿模 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/p17-gpt-6.2-sol-medium-20261126.html) · [源码](p17-gpt-6.2-sol-medium-20261126.html) |
| 18 | 2026-11-26 16:08 | ChatGPT · Work | GPT-6.2 Sol（高） | 未记录 | 踏板穿模 | [▶ 看动画](https://htmlpreview.github.io/?https://github.com/Hunhung/pelican-bike-tests/blob/main/p18-gpt-6.2-sol-high-20261126.html) · [源码](p18-gpt-6.2-sol-high-20261126.html) |

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
> 18 条均已按用户视觉审查结果填写。

| # | 平台 | 模型 | A 鹈鹕本体 | B 车架结构 | C 骑行姿态 | D 运动传动 | E 场景整体 | 发现的问题 | 结论 |
|---|---|---|---|---|---|---|---|---|---|
| 1 | WorkBuddy | 均衡（GLM5.3） | ✓（造型一般） | ✗ | ✗ | ✗ | ✗ | 轮子起飞，鹈鹕造型一般；腿和脚断连、车没有踏板；链条连在前轮；轮子飞到天上导致整车造型丢失 | 效果极差 |
| 2 | 同济 API | DeepSeek-V4.1-Flash |  |  | ✗ | ✗ |  | 脚不在踏板上，踏板转动错误，膝盖逻辑错误 | 有问题 |
| 3 | WorkBuddy | 快速 | ✓ | ✓ | ✓ | ✓ | ✓ | 效果出色，无明显逻辑错误 | 效果出色 |
| 4 | WorkBuddy | DeepSeek-V4.1-Flash | ✓ | ✓ | ✗ | ✓ | ✓ | 无明显错误，屁股轻微离开板凳 | 基本正常 |
| 5 | WorkBuddy | Hy4 | ✗ |  |  | ✗ |  | 鹈鹕造型有点丑，踏板穿模 | 有问题 |
| 6 | WorkBuddy | GLM-5.3-Flash | ✗ | ✗ | ✗ | ✗ | ✗ | 鸟严重变形、身体分开；腿画错、脚和腿分开；地面运动反了；自行车结构错误；踏板运动不合逻辑；一只脚粘在踏板上 | 效果极差 |
| 7 | 同济 API | Qwen3.8-Flash-Next | ✗ | ✗ | ✗ | ✗ | ✗ | 轮子转动错误且不在车上，踏板乱转；“鹈鹕”两字写错；脚乱踩非骑车动作；自行车结构丢失，运动不连贯 | 效果极差 |
| 8 | WorkBuddy | Hy3 |  |  | ✗ | ✗ | ✗ | 脚和踏板穿模，图层关系不对 | 有问题 |
| 9 | 同济 API | DeepSeek-V4.1-Flash |  |  | ✗ |  | ✗ | 脚穿模，地面运动方向错误 | 有问题 |
| 10 | 未记录 | 未记录 |  |  |  |  | ✗ | 地面运动方向不对 | 轻微问题 |
| 11 | 豆包桌面端 | DeepSeek-V4.1-Flash | ✗ | ✗ | ✗ | ✗ | ✗ | 轮子内部不完整；鹈鹕没有手、动作错误；脚穿模、踏板穿模；围巾断掉 | 效果差 |
| 12 | 豆包桌面端 | 豆包 2.1 Pro | ✗ |  | ✗ | ✗ | ✗ | 鹈鹕没有手、动作错误、嘴巴太大；地面运动方向不对；踏板穿模；膝盖动作不够顺畅 | 有问题 |
| 13 | 豆包桌面端 | 豆包 2.1 Lite | ✗ | ✗ | ✗ | ✗ |  | 腿和身体严重分离、鹈鹕动作错误；踏板不完整、没有链条；踏板和脚穿模 | 效果差 |
| 14 | 豆包桌面端 | 未记录 | ✗ |  |  | ✗ |  | 鹈鹕动作错误；踏板和脚转动错误；轮子速度太快 | 有问题 |
| 15 | WorkBuddy | Kimi-K3.1-Pro | ✓ | ✓ | ✓ | ✓ | ✓ | 出色，无明显逻辑问题 | 效果出色 |
| 16 | WorkBuddy | Space-Bunny |  |  | ✗ | ✗ |  | 腿穿模；链条转动方向错误；踏板连接不完整；屁股没挨着椅子 | 有问题 |
| 17 | ChatGPT Work | GPT-6.2 Sol（中） |  |  | ✗ | ✗ | ✗ | 腿穿模，图层错误，踏板穿模 | 有问题 |
| 18 | ChatGPT Work | GPT-6.2 Sol（高） |  |  |  | ✗ |  | 踏板穿模 | 有问题 |

## 快速观察

**推理量（仅 WorkBuddy / 同济有数据）**
- **推理量最高**：DeepSeek-V4.1-Flash（00:16，24,424）和「快速」档位（24,023）——生成前想得最多。
- **推理量最低**：GLM-5.3-Flash（87）、均衡档位（132）——几乎不假思索直接出代码。
- **同模型对比**：DeepSeek-V4.1-Flash 在 WorkBuddy / 同济共跑了 3 次（第 2/4/9 条），推理量在 13.8k～24.4k 之间波动。
- **第 15–16 条**：Kimi-K3.1-Pro（第 15 条，8,435）与 Space-Bunny（第 16 条，19,980），同为 WorkBuddy CLI。

**视觉审查结论（第 1–10 条）**
- **效果最好**：第 3 条（快速档位）——效果出色、无明显逻辑错误；第 4 条（DeepSeek 自带）仅屁股轻微离开板凳。
- **效果极差**：第 1、6、7 条——分别出现轮子飞出天际、鸟体严重变形结构分解、整车结构丢失且文字写错。
- **共性问题 · 穿模**：第 5、8、9 条都有踏板或脚的穿模 / 图层关系错误。
- **共性问题 · 地面方向**：第 6、9、10 条地面运动方向错误或反了。
- **推理量与效果不强相关**：推理量最高的第 3、9 条分别是「效果出色」和「脚穿模、地面方向错」；推理量最低的第 6 条（87）效果极差。

**视觉审查结论（第 11–14 条，豆包桌面端）**
- **效果最差**：第 13 条（豆包 2.1 Lite）——腿和身体严重分离、踏板不完整、没有链条、踏板和脚穿模；第 11 条轮子内部不完整、围巾断掉。
- **共性问题 · 鹈鹕动作**：4 条全部被指出动作错误（11/12 还提到"没有手"，12 嘴巴太大）。
- **共性问题 · 踏板/脚穿模**：第 11、12、13 条都有踏板或脚的穿模，第 14 条踏板和脚转动错误。
- **运动逻辑**：第 12 条地面运动方向不对、膝盖不顺畅；第 14 条轮子速度太快。
- **源码自检 ≠ 视觉效果**：豆包侧称第 14 条经多轮截图自检修了 7 处、第 12 条"无已知遗留问题"，但实际视觉审查仍发现多处错误——源码层面的自查不能替代观看验证。

**视觉审查结论（第 17–18 条，ChatGPT Work）**
- **中档**：腿部穿模、图层错误、踏板穿模。
- **高档**：踏板穿模。
- **两档共性问题**：踏板穿模；高档本次记录的问题少于中档。两次测试均未记录推理 token，不能据此比较推理量。

**档位 vs 模型**
- 「均衡」「快速」是产品内的档位名称，不是具体模型名；其余为模型版本号。
- 豆包侧以"内部版本信息"为由未披露模型名，第 11/12/13 条由用户按时间补充，第 14 条仍为未记录。
- 第 17/18 条为同一模型 GPT-6.2 Sol 的不同思考强度（中/高），档位由用户补充。

## 口径说明

- **测试时间**：第 1–10 条取自各会话第一条消息的发出时间（比文件修改时间更接近真实测试时刻）；第 11–14 条取文件最后写入时间——用户口头补充的时间（18:53 / 18:36 / 18:33）与写入时间相差 1~3 分钟，模型按最接近者对应；第 17–18 条取对应 HTML 文件的创建时间（北京时间，精确到分钟）。
- **推理 token**：第 1–10 条取自该会话首轮生成（创建 HTML 那一步）的 `reasoning_tokens`；豆包桌面端与 ChatGPT Work 无此数据。
- **AI 平台**：WorkBuddy 的记录按会话模型 ID 区分——`custom-local:DeepSeek-V4.1-Flash` 与 Qwen 为同济人工智能平台（API 接入），其余为 WorkBuddy 自带（CLI 客户端）；第 11–14 条为豆包 Windows 桌面端 Agent 模式；第 17–18 条为 ChatGPT Work 模式。
- **思考强度档位**（低/中/高）：早期测试档位未被系统写入记录，以推理 token 作为替代指标；第 17–18 条由用户明确提供中/高档位。
- 「问题备注 / 发现的问题」：18 条全部来自用户逐条观看动画后的视觉审查，已按 A–E 清单归类；豆包侧源码核对描述仅作技术参照，见文末。
- 原始文件仍保留在各自的工作区（本机豆包会话目录 `%USERPROFILE%\Doubao\chats\`）中，本仓库为整理后的副本，未删除任何原文件。
