# 求职作品集

> UE5 作品集项目


## 项目简介

这是一个综合性的 UE5 作品仓库，总计开发时长约 **200h+**。包含了从底层系统架构、编辑器工程化工具，到前沿 AI 技术落地的完整闭环。

| 项目模块                               | 核心技术                                       | 开发周期        |
| :------------------------------------- | :--------------------------------------------- | :-------------- |
| **1. RPGBattlePrototype（长线打磨）**  | UE5 GAS / Behavior Tree / 数据驱动             | 21天 + V2.0重构 |
| **2. PURGE_PROTOCOL（极速交付）**      | 纯正 GAS / TimeScale 子弹时间 / 行为树调度     | 5天（约30h）    |
| **3. DataTable Editor Tool（工程化）** | C++ Editor Plugin / Slate / AssetActionUtility | 10天            |
| **4. LLM-Driven DDA（前沿探索）**      | DeepSeek API / JSON 校验 / 动态难度            | 3天             |

**RPGBattlePrototype 完整闭环**：实现了从 **输入 → Ability 激活 → AI 决策 → 技能执行 → 碰撞判定 → 伤害结算 → 战斗反馈 → 死亡/转阶段** 的完整管线。

**当前稳定版本**：V2.0。后续迭代目标见 [NEXT_STEPS.md](https://./docs/NEXT_STEPS.md)。


## 核心功能

| 模块       | 内容                                                         |
| :--------- | :----------------------------------------------------------- |
| 玩家系统   | 四段连招、空中攻击、闪避（无敌帧）、完美闪避（回复资源）、E/Q 技能、鼠标中键锁定、鼠标滚轮放大缩小画面 |
| Boss 系统  | 7 个技能（含转阶段解锁）、三段距离决策 AI、随机释放、CD 管理、转阶段演出 |
| AI 决策    | 近/中/远距离技能组 → CD 筛选 → 随机选择 → 释放，全 CD 时主动接近兜底 |
| 战斗反馈   | 伤害数字（30% 暴击）、CameraShake 分级、受击音效分级、受击粒子、BGM 切换 |
| UI 系统    | 双层血条缓动、技能冷却、开始/死亡/胜利/暂停/操作说明界面     |
| 数据驱动   | Excel → CSV → DataTable，Damage / Cost / Cooldown / CameraShake 全配置化 |
| 工程记录   | 连续 DevLog（V1.0 / V1.1 / V2.0 / Editor Tool / LLM+DDA），完整踩坑复盘 |
| 编辑器工具 | 资产批量操作、Content Browser 扩展、Slate 面板、Actor 批量操作、插件打包（**[点击查看源码](./EditorTool/SuperManager/README.md)**） |
| AI 实验    | 五维玩家画像采集、LLM 决策链路、三组对照实验、安全回退机制   |


## 操作说明

| 操作                 | 按键            |
| :------------------- | :-------------- |
| 移动                 | WASD            |
| 跳跃                 | Space           |
| 普通攻击（四段连招） | 鼠标左键        |
| 空中攻击             | 空中 + 鼠标左键 |
| 闪避                 | Shift           |
| E 技能               | E               |
| Q 技能               | Q               |
| 锁定 Boss            | 鼠标中键        |
| 暂停                 | P               |
| 调出鼠标             | Alt             |


## 技术栈

| 领域             | 方案                                                         |
| :--------------- | :----------------------------------------------------------- |
| 开发语言         | C++ + Blueprint                                              |
| 战斗框架         | GAS（Gameplay Ability System）                               |
| AI 框架          | Behavior Tree + Blackboard                                   |
| AI 集成          | LLM API 调用、JSON 校验、DDA 参数回退                        |
| 属性系统         | C++ AttributeSet + GE                                        |
| 数据驱动         | Excel → CSV → DataTable                                      |
| 编辑器扩展       | C++ Editor Plugin、Asset Action Utility、Content Browser / Level Editor 菜单扩展、Slate Widget、Editor Subsystem、Scene Outliner 列扩展、自定义图标与快捷键 |
| 输入系统         | Enhanced Input                                               |
| 动画系统         | Montage + Anim Notify State                                  |
| 攻击判定（玩家） | 武器碰撞体                                                   |
| 攻击判定（Boss） | Multi Sphere Trace + Box Trace（按技能配置检测形状）         |

## 实机演示

- **RPGBattlePrototype 演示视频（P1）**
  - B站（在线）：[V1.1 演示视频](https://www.bilibili.com/video/BV1knYx68E5M/)
  - GitHub Releases（下载）：[V1.1 演示视频](https://github.com/aq6-u/RPGBattlePrototype/releases)
  - 阿里云盘（备用）：[V1.1 演示视频](https://www.alipan.com/s/NcWjmQRJD9r)

- **Editor Tool 演示视频（P2）**
  - B站（在线）：[EditorTool 演示视频](https://www.bilibili.com/video/BV1knYx68E5M/)

- **LLM-Driven DDA 实验**
  - 说明：该项目核心为后台数据链路与工程验证，无特殊视觉表现，故未录制视频。详细数据与结论见仓库 `DevLog_LLM_DDA.md`。
- **极速开发Demo演示视频**
  - B站（在线）：[极速开发Demo演示](https://www.bilibili.com/video/BV1knYx68E5M/)

## 文档索引

| 文档                                                         | 说明                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [开发日志（DevLog_V1.0）](./docs/DevLog.md)                  | V1.0 阶段 Day 1-21 每日开发记录                              |
| [开发日志（DevLog_V1.1）](./docs/DevLog_V1.1.md)             | V1.1 阶段 Day 1-4 迭代修复记录                               |
| [开发日志（DevLog_V2.0）](./docs/DevLog_V2.0.md)             | V2.0 架构重构阶段每日开发记录                                |
| [开发日志（DevLog_EditorTool）](./docs/DevLog_EditorTool.md) | EditorTool 开发学习与实践记录                                |
| [开发日志（LLM_DDA）](./docs/DevLog_LLM_DDA.md)              | LLM + DDA 实验开发与验证记录                                 |
| [SuperManager 插件源码与说明](./EditorTool/SuperManager/README.md) | C++ Editor Plugin 源码，包含资产清理、Actor 批处理与快捷键扩展 |
| [LLM 驱动动态难度调整（DDA）可行性验证报告](./docs/LLM_DDA_Feasibility_Report.md) | LLM + DDA 实验报告，含三组对照实验与工程指标                 |
| [开发日志（DevLog_极速开发）](./docs/DevLog_极速开发.md)     | 5 天（约 30 小时）限时极限开发记录。涵盖双阶段 GAS 架构搭建、行为树调度、Q键全局减速与高伤激光机制的从 0 到 1 落地。 |
| [极速开发Demo设计文档](./docs/极速开发Demo设计文档.md)       | 限时 Demo 完整设计案。包含“传递”核心循环推演、GAS 底层执行管线、参考游戏拆解、以及未实现功能的技术取舍与数据结构建模。 |
| [项目开发总结](./docs/项目开发总结.md)                       | V2.0 完整总结，含设计意图说明                                |
| [性能观察报告](./docs/Demo性能观察报告.md)                   | V2.0 阶段 Demo 的性能基线分析                                |
| [迭代目标与结算](./docs/NEXT_STEPS.md)                       | 迭代结算与后续方向评估                                       |
| [RPG 设计草案](./docs/RPG_Design_Draft.md)                   | 项目设计规格与系统架构（draft_v2.0）                         |


## 游戏拆解分析报告

| 日期       | 游戏 | 主题                     | 链接                                                         |
| :--------- | :--- | :----------------------- | :----------------------------------------------------------- |
| 2026.06.14 | 鸣潮 | 北落野大决战剧情演出拆解 | [查看](./GameDesignNotes/20260614_鸣潮_北落野大决战剧情拆解.md) |
| 2026.06.15 | 鸣潮 | 今汐全技能组拆解         | [查看](./GameDesignNotes/20260615_鸣潮_今汐全技能组拆解.md)  |
| 2026.06.17 | 鸣潮 | 燎照之骑 Boss 拆解       | [查看](./GameDesignNotes/20260617_鸣潮_燎照之骑Boss拆解.md)  |
| 2026.06.19 | 鸣潮 | 庭际刀刃鸣剧情拆解       | [查看](./GameDesignNotes/20260619_鸣潮_庭际刀刃鸣(今汐漂泊者正式见面)剧情拆解.md) |
| 2026.06.21 | 鸣潮 | 长离全技能组拆解         | [查看](./GameDesignNotes/20260621_鸣潮_长离全技能组拆解.md)  |
| 2026.06.23 | 鸣潮 | 无冠者 Boss 拆解         | [查看](./GameDesignNotes/20260623_鸣潮_无冠者Boss拆解.md)    |
| 2026.11.07 | 鸣潮 | 切人系统与合轴机制拆解   | [查看](./GameDesignNotes/20261107_鸣潮_延奏变奏、切人系统与合轴机制拆解.md) |

> 更多拆解报告持续更新中。


## 版本记录

| 版本 | 日期       | 说明                                                         |
| :--- | :--------- | :----------------------------------------------------------- |
| V1.0 | 2026.08.15 | 核心战斗闭环完成，21 天开发周期结束                          |
| V1.1 | 2026.08.20 | 修复 V1.0 全部已知 Bug，补双层血条、受击粒子、场景与 UI 优化 |
| V2.0 | 2026.09.06 | 架构重构：Ability 与动画解耦、统一 Damage Pipeline、UI 数据绑定迁移至 C++、SkillData 扩展与 DDA 接入 |


## License

- **代码部分**：MIT License
- **引擎美术/动画/音频素材**：版权归原权利人所有，本项目仅作个人学习与技术策划求职展示，不用于商业用途。

**最后更新**：2026.11.08
