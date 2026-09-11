# chukong-design-skill

面向设计师、前端工程师和 AI Agent 的初空设计系统入口。安装它之后，支持 Agent Skills 的工具可以在设计、实现和评审界面时，按初空的视觉、组件、动效、无障碍和质量约束工作。

> This is a reference-led Agent Skill, not a runtime component library. It is designed to be useful for people who do not already know the Chukong project context.

## 先选适合你的路径

| 你的目标 | 需要什么 |
| --- | --- |
| 让 AI 按初空方法设计或评审界面 | 安装本仓库的 `chukong-design` skill |
| 在产品中使用真实组件和 token | 访问并接入私有的 [`chukong-design-system`](https://github.com/chukong-creator/chukong-design-system) |
| 快速生成 HTML 原型、预览和设计检查 | 使用公开的 [`chukong-design`](https://github.com/chukong-creator/chukong-design) 工作流 |

本仓库只负责把 Agent 引导到正确的参考和决策边界，不复制私有 token、组件源码、字体或品牌资产。

## 快速开始

### 安装

全局安装（让你的多个项目都能使用）：

```bash
npx skills add chukong-creator/chukong-design-skill -g
```

只在当前项目安装：

```bash
npx skills add chukong-creator/chukong-design-skill
```

查看仓库里可安装的 skill，或确认已经安装：

```bash
npx skills add chukong-creator/chukong-design-skill --list
npx skills ls -g
```

安装后，在支持 `$skill-name` 调用的 Agent 中直接说：

```text
Use $chukong-design to review this settings page on desktop and mobile.
先用 $chukong-design 设计这个空状态、加载态和错误恢复路径，并说明你参考了哪些规则。
```

如果你的 Agent 不支持显式 `$skill-name`，只要在任务中说明“按 Chukong Design System 设计/评审”，让它自动发现已安装的 skill 即可。

### 第一次使用建议

给 Agent 提供以下最小上下文，结果会明显更稳定：

1. 产品类型、用户和当前任务。
2. 目标平台（桌面、移动端或响应式）以及需要覆盖的状态。
3. 当前项目的技术栈、已有组件和真实/脱敏数据样本。
4. 你希望验收的路径，例如键盘操作、深色模式或错误重试。

## 这个 skill 如何工作

它会先判断当前处于哪一种访问模式，再按任务加载最少的参考：

### 1. Full reference mode

你能访问私有 canonical 仓库时，`DESIGN.md` 是设计契约，token 与 React 源码是实现事实源。需要精确的视觉值或组件 API 时，必须读取对应源文件，而不是凭记忆重建。

### 2. Consumer project mode

你的项目已经接入 `@chukong-design/react` 或包含本地 token/组件文档时，skill 会优先检查项目中的真实 API、版本和主题配置，再提出改动。它不会为了“看起来像”而在页面里重定义一套品牌变量。

### 3. Public guidance mode

你没有私有仓库权限时，skill 仍可以帮助你做任务拆解、信息层级、状态设计、交互审查和视觉方向讨论，但会明确标记“canonical 状态未核验”。需要精确 token、组件 API、版本行为或发布配置时，它会请求你提供权限、checkout 或相关文件，不会编造规则。

## 公开可用的设计基线

以下是便于陌生用户理解的公开摘要，不替代 canonical 契约：

- **克制、生命力、可信**：层级来自信息优先级、空间和状态，不靠装饰堆叠制造品质感。
- **结构先于装饰**：优先使用清楚的 surface、列表和排版；谨慎使用大面积渐变、发光装饰、卡中卡和无意义徽章。
- **低饱和生命色**：米白画布、雾蓝灰骨架、草木绿生命辅助和陶土暖意形成品牌氛围；功能性成功/警告颜色仍需独立表达。
- **功能性流动**：动效解释状态变化和因果，尊重 `prefers-reduced-motion`；不让 hover 成为移动端的必要信息入口。
- **可恢复的真实状态**：loading、empty、success、error、disabled、permission、retry 和移动端路径按任务覆盖；错误必须给出下一步。
- **可追溯的 AI 表达**：事实、推断和建议分开，说明依据和不确定性，不用夸张承诺替代证据。

## Claude Design 方法：从灵感到可验证界面

这个 skill 学习了 Claude Design 工作流里最有价值的部分，并把它改写成跨 Agent 可执行的方法。它不是把某个模型的隐藏 prompt 原样复制，也不是要求每个小改动都走完整流程。适用于新视觉方向、重要页面、高保真原型和质量敏感的重设计；小 bug、单个 token、纯无障碍审查或短文案修改可以直接处理。

完整的公开工作流参考见 [`references/ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/references/ai-design-loop.md)，Claude Code 的工具适配见 [`references/claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/references/claude.md)。方法本身分为七个相互衔接的环节：

| 环节 | 具体做法 | 产生的证据 |
| --- | --- | --- |
| **Context** 上下文 | 先说清用户、场景、主任务、固定约束、真正开放的选择和失败条件；已有界面先描述现状，不能用“现代/高级”这种空泛形容词替代观察。 | 一页约束简报、状态清单、验收标准 |
| **Discover** 探索 | 在方向开放时只提出 2–3 个真正不同的高层方向，说明感觉、构图、材质/排版和记忆点；收集参考，必要时用私有随机 seed 打破惯性，但不把 seed 带进产品。 | 方向卡、参考来源、选择/拒绝理由 |
| **Define** 定义 | 将选中的方向冻结为设计身份：情绪意图、布局拓扑、色彩/字体/表面/动效职责、密度、一个主动作和 anti-reference（明确不要变成什么）。 | 可复述的 build brief、稳定的质量 rubric |
| **Build** 构建 | 先用真实设计系统组件和 token，再用代表性脱敏数据做可运行渲染；图片、3D、shader 或视频只有在确实传达概念时才加入。 | 可打开的 HTML/应用页面、组件状态和数据样本 |
| **Critique** 批评 | 实现者和视觉批评者分离；批评者只看新鲜渲染结果和同一套 rubric，不被代码或实现者解释说服。反馈固定为“有效之处 → 最大缺口 → 按优先级的修复 → 有证据的评分 → 未核验问题”。 | 截图/页面、优先级反馈、未核验问题 |
| **Deliver** 交付减法 | 逐项询问每个元素是否提升理解、行动、信任、定位、反馈或目标感受；删除无层级作用的渐变、光晕、阴影、徽章、容器、重复文案和无意义动效。 | 减法记录、保留/删除理由 |
| **Verify** 验证 | 检查真实渲染路径和运行时错误，而不是只看源代码或静态图；覆盖桌面/移动、鼠标/触摸/键盘、焦点、对比度、reduced-motion、loading/empty/error/disabled，并做 5 秒主信息检查。 | 浏览器检查、状态证据、剩余风险、用户 review 点 |

这套方法的核心不是“多做几版”，而是让每轮迭代都有明确问题、稳定评价尺和可回看的证据；如果质量不收敛，应回到方向或 rubric，而不是无限微调。

## Reference map

### 1. Canonical：初空设计系统（优先级最高）

[`chukong-creator/chukong-design-system`](https://github.com/chukong-creator/chukong-design-system) 是实现与决策的唯一事实源，目前为私有仓库。按任务读取：

| Reference | 用途 |
| --- | --- |
| [`DESIGN.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/DESIGN.md) | AI 设计契约：人格、token 层级、组件边界、状态、无障碍、内容与完成信号 |
| [`docs/style-brief.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/style-brief.md) | 视觉方向：低饱和雾蓝灰骨架、草木绿生命辅助、陶土暖色、米白画布、密度与材质 |
| [`docs/components.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/components.md) | 组件选择、组合方式、状态和禁用/错误边界 |
| [`docs/motion.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/motion.md) | 功能性运动、节奏、退出速度与 reduced-motion |
| [`docs/adoption.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/adoption.md) | 消费项目接入、升级和迁移 |
| [`packages/tokens/src`](https://github.com/chukong-creator/chukong-design-system/tree/main/packages/tokens/src) | DTCG token 源；不要在页面里重定义品牌变量 |
| [`packages/react/src`](https://github.com/chukong-creator/chukong-design-system/tree/main/packages/react/src) | React 组件与行为实现；需要精确 API 时读取 |

### 2. Workflow：公开版 chukong-design

[`chukong-creator/chukong-design`](https://github.com/chukong-creator/chukong-design) 用于 HTML 设计产出、交互原型、设计系统编译/checker、浏览器预览和 AI 设计循环。它的 `references/ai-design-loop.md` 以及 `references/quality/` 可作为重要工作的过程参考，但不能替代 canonical token 与组件契约。

### 3. 外部研究与灵感

这些资料用于提出问题、比较机制和训练审美；最终决策必须回到初空契约、产品约束和用户反馈。

| Reference | 借鉴边界 |
| --- | --- |
| [Vercel Design](https://vercel.com/design.md) / [Dark](https://vercel.com/design.dark.md) | 设计文档的组织方式、明暗主题表达、系统化说明；不直接复制品牌视觉 |
| [Meta Design](https://design.facebook.com/) | 大型产品系统的可读性、可扩展性与组件/内容关系；不把 Meta 品牌当作初空规则 |
| [Fluid Functionalism](https://github.com/mickadesign/fluid-functionalism) | 流体布局、空间关系、功能性动效和组件组合的研究样本；先理解机制再适配 |
| [Claude Design workflow](https://github.com/chukong-creator/chukong-design/tree/main/references) | 上下文→探索→定义→构建→批评→减法→验证的设计闭环；借鉴方法，不复制 Claude/Anthropic 品牌或专有内容 |
| [How I Design with AI](https://x.com/reactiverobot/status/2092638003789439075) / [可读镜像](https://www.linkedin.com/pulse/how-i-design-ai-matt-dailey-cfe1e) | 先看整体约束、删除多余元素、隔离迭代、组件库、真实数据预览、收集参考、持续训练审美 |

## Reference precedence

当参考之间冲突时，按以下顺序处理：

1. 用户明确的产品、平台、技术、无障碍和隐私约束。
2. `chukong-design-system/DESIGN.md` 及其实现 token/组件。
3. 已批准的项目视觉方向与真实消费代码。
4. 本 README 列出的外部研究。

外部截图、代码或文案不是产品事实。借鉴时记录来源、观察到的机制、要迁移的部分和要避免复制的部分；不得复制私有内容、品牌标志、受版权保护的独特素材或未获许可的实现。

## 一个好的任务提示

```text
Use $chukong-design.
这是一个面向长期关系维护的桌面 + 移动端工具。请先确认用户、主任务和关键状态，
然后基于 Chukong 的组件/动效约束设计列表页。请使用脱敏的真实数据预览，覆盖
loading、empty、error、permission、retry、键盘 focus 和 reduced-motion，最后列出
你读取的 reference、未核验的假设，以及最值得我 review 的三个取舍。
```

## 质量与验收

skill 给出的“完成”不等于静态代码通过。重要任务至少要在真实渲染表面检查：

- 桌面与移动端布局、light/dark/high-contrast 主题（适用时）。
- 键盘 focus、可访问名称、触摸目标和 Dialog/Popover 的焦点回收。
- loading、empty、error、disabled、permission、retry 等适用状态。
- 代表性脱敏数据下的信息密度、文案长度和恢复路径。
- 动效是否解释状态变化，以及 reduced-motion 是否安全降级。

## 维护、反馈与边界

- canonical token、组件、文档和实现只在 [`chukong-design-system`](https://github.com/chukong-creator/chukong-design-system) 中更新；本仓库随后更新链接、路由和公开摘要。
- 报告问题时请附：使用的 Agent、任务提示、目标平台、期望与实际结果；不要上传个人数据、凭据、私有 endpoint 或未脱敏截图。
- 本仓库是 skill 分发入口，不承诺提供运行时组件、npm 包、字体、品牌素材或私有仓库访问权限。
- GitHub 公开可见不等于自动授予复制和再发布许可。当前仓库尚未声明独立许可证；如需将其打包进其他产品或再发布，请先联系维护者确认授权。

## English quick start

Install globally with `npx skills add chukong-creator/chukong-design-skill -g`, then invoke `Use $chukong-design to ...`. The skill routes design, implementation, and review work to the canonical Chukong references when available, and clearly labels unverified assumptions when the private reference repository cannot be accessed. It does not ship runtime components or copied brand assets.
