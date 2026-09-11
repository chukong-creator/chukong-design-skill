# chukong-design-skill

面向设计师、前端工程师和 AI Agent 的**初空设计方法**。它提供一套从上下文、探索、构建、批评到验证的设计工作方式；初空设计系统只是可选的视觉与实现参考，并不是使用这个 skill 的前提。

> This is a method-first Agent Skill. You can use the Chukong design method with Chukong Design System, another design system, or no design system at all.

## 先理解两个独立层次

| 层次 | 解决什么问题 | 是否必须 |
| --- | --- | --- |
| **初空设计方法** | 如何理解任务、探索方向、建立 rubric、真实渲染、独立批评、做减法和验证 | 安装本 skill 后默认使用 |
| **初空设计系统** | 使用哪些 token、组件、视觉语言、动效值和实现 API | 可选；只有明确选择时才使用 |

安装 `chukong-design` 不会自动把任何项目改成初空的颜色、组件或品牌风格。项目已有其他设计系统时，以项目实际绑定的系统为实现事实源，初空方法仍然可以完整工作。

## 选择适合你的路径

| 你的目标 | 需要什么 |
| --- | --- |
| 只使用初空设计方法 | 安装本仓库；不需要访问初空私有仓库 |
| 使用初空方法 + 初空设计系统 | 安装本仓库，并访问 [`chukong-design-system`](https://github.com/chukong-creator/chukong-design-system) |
| 使用初空方法 + 其他设计系统 | 安装本仓库，再提供项目已有系统的文档、token 或组件 API |
| 快速生成 HTML 原型和预览 | 额外使用公开的 [`chukong-design`](https://github.com/chukong-creator/chukong-design) 工作流 |

## 快速开始

### 安装

全局安装（让多个项目都能使用）：

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
Use $chukong-design to apply the Chukong design method to this settings page.
请用 $chukong-design 设计这个空状态、加载态和错误恢复路径，并说明每轮验证证据。
```

如果你还要使用某个设计系统，请把选择说清楚：

```text
Use $chukong-design. Apply the method, and use our existing Material 3 components
and tokens as the implementation truth. Do not introduce Chukong visual tokens.
```

如果 Agent 不支持显式 `$skill-name`，说明“按 Chukong 设计方法设计/评审”即可；方法不要求项目安装初空组件库。

### 第一次使用建议

给 Agent 提供以下最小上下文：

1. 产品类型、用户、场景和当前任务。
2. 目标平台（桌面、移动端或响应式）以及需要覆盖的状态。
3. **选中的设计系统**（例如初空、Material、Spectrum、项目自有系统）或明确“无设计系统”。
4. 当前技术栈、已有组件、真实/脱敏数据样本和验收路径。

## 访问模式

### 1. Method-only：只用初空设计方法

这是默认模式。使用本 README 和 skill 中的方法完成任务，视觉实现由项目现有规范、平台原生组件或明确的产品方向决定。不读取也不假设初空 token、组件和颜色。

### 2. Chukong-system：选择初空设计系统

只有用户明确选择初空设计系统，或当前项目已经绑定它时，才读取私有 canonical reference。此时 `DESIGN.md` 是设计契约，token 与 React 源码是实现事实源。

### 3. Other-system：选择其他设计系统

初空方法照常运行，但 token、组件、主题、动效数值和 API 以所选系统及项目实际版本为准。不要为了使用初空方法而替换项目系统。

### 4. Requested-but-unavailable：用户选择初空系统但暂时无法访问

仍可以先做任务拆解、信息层级、状态设计、交互审查和视觉方向讨论，并明确标记“初空系统规则未核验”。需要精确 token、组件 API、版本行为或发布配置时，请求权限、checkout 或相关文件；不要编造规则。

## 公开可用的设计方法基线

这些原则属于方法层，不规定品牌颜色或组件库：

- **上下文先于风格**：先确认用户、任务、约束、开放选择和失败条件；不要用“现代/高级”替代观察。
- **结构先于装饰**：先建立信息层级、布局拓扑、内容密度和主动作，再决定视觉丰富度。
- **状态是真实产品的一部分**：按任务覆盖 loading、empty、success、error、disabled、permission、retry 和响应式路径。
- **动效服务于理解**：动效解释状态变化和因果，尊重 `prefers-reduced-motion`，不让 hover 承担移动端必需信息。
- **证据优先**：用代表性脱敏数据和真实渲染表面评审；区分事实、推断、建议和未核验风险。
- **减法提升品质**：删除没有层级作用的渐变、光晕、容器、徽章、重复文案和无意义动效。
- **验证交付路径**：检查运行时、桌面/移动、鼠标/触摸/键盘、焦点、对比度和恢复路径；静态图和评分都不是产品就绪证明。

## 可选的初空设计系统 profile

以下内容只在用户选择初空设计系统时生效，不是初空设计方法的强制视觉结论：

- 人格为**克制、生命力、可信**。
- 视觉倾向低饱和米白、雾蓝灰、草木绿和陶土暖色；具体色值以 canonical token 为准。
- 组件和页面遵循 `primitive → semantic → component` token 路径、明确状态、可访问焦点和功能性动效。
- 私有系统的实现、API、token 和迁移规则见 [`chukong-design-system`](https://github.com/chukong-creator/chukong-design-system)，不可访问时不应猜测。

## 初空设计方法：从灵感到可验证界面

这套方法借鉴 Claude Design 工作流里最有价值的部分，并改写成跨 Agent、跨设计系统可执行的闭环。它不是某个模型的隐藏 prompt，也不是要求每个小改动都走完整流程。适用于新视觉方向、重要页面、高保真原型和质量敏感的重设计；小 bug、单个 token、纯无障碍审查或短文案修改可以直接处理。

完整公开参考：[`ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/ai-design-loop.md)；Claude Code 的工具适配：[`claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/claude.md)。

| 环节 | 具体做法 | 产生的证据 |
| --- | --- | --- |
| **Context** 上下文 | 说清用户、场景、主任务、固定约束、真正开放的选择和失败条件；已有界面先描述现状。 | 约束简报、状态清单、验收标准 |
| **Discover** 探索 | 方向开放时只提出 2–3 个真正不同的高层方向，说明感觉、构图、材质/排版和记忆点；让用户选择，不为凑数制造变体。 | 方向卡、参考来源、选择/拒绝理由 |
| **Define** 定义 | 将选中的方向冻结为设计身份：情绪意图、布局拓扑、视觉角色、密度、主动作和 anti-reference。 | build brief、稳定的质量 rubric |
| **Build** 构建 | 使用用户选中的设计系统；没有系统时使用项目规范或平台原语。用代表性脱敏数据做可运行渲染，只有在有意义时才加入图片、3D、shader 或视频。 | 可打开的页面、组件状态、数据样本 |
| **Critique** 批评 | 实现者与视觉批评者尽量分离；批评者只看新鲜渲染结果和同一套 rubric，不被代码或实现者解释说服。反馈固定为“有效之处 → 最大缺口 → 按优先级的修复 → 有证据的评分 → 未核验问题”。 | 截图/页面、优先级反馈、未核验问题 |
| **Deliver** 交付减法 | 逐项询问元素是否提升理解、行动、信任、定位、反馈或目标感受；删除装饰性复杂度。 | 减法记录、保留/删除理由 |
| **Verify** 验证 | 检查真实渲染路径和运行时错误，覆盖桌面/移动、鼠标/触摸/键盘、焦点、对比度、reduced-motion 和适用状态，并做 5 秒主信息检查。 | 浏览器检查、剩余风险、用户 review 点 |

核心不是“多做几版”，而是让每轮迭代都有明确问题、稳定评价尺和可回看的证据；如果质量不收敛，应回到方向或 rubric，而不是无限微调。

## Reference map

### 1. 初空设计方法（主要入口）

- 本仓库的 [`skills/chukong-design/SKILL.md`](skills/chukong-design/SKILL.md)：跨 Agent 的最小可执行入口。
- 公开版 [`chukong-design`](https://github.com/chukong-creator/chukong-design)：包含 HTML 原型、预览、设计检查和更完整的工作流参考。
- Claude Code 方法适配：[`ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/ai-design-loop.md)、[`claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/claude.md)。

### 2. 可选：初空设计系统

[`chukong-creator/chukong-design-system`](https://github.com/chukong-creator/chukong-design-system) 是初空系统的实现与决策事实源，目前为私有仓库。只在选择初空系统时按任务读取：

| Reference | 用途 |
| --- | --- |
| [`DESIGN.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/DESIGN.md) | 设计契约：人格、token 层级、组件边界、状态、无障碍、内容与完成信号 |
| [`docs/style-brief.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/style-brief.md) | 视觉方向、表面、类型、色彩和密度 |
| [`docs/components.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/components.md) | 组件选择、组合方式和状态边界 |
| [`docs/motion.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/motion.md) | 功能性运动、节奏和 reduced-motion |
| [`docs/adoption.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/adoption.md) | 消费项目接入、升级和迁移 |
| [`packages/tokens/src`](https://github.com/chukong-creator/chukong-design-system/tree/main/packages/tokens/src) | DTCG token 源 |
| [`packages/react/src`](https://github.com/chukong-creator/chukong-design-system/tree/main/packages/react/src) | React 组件与行为实现 |

### 3. 外部研究与灵感

这些资料用于提出问题、比较机制和训练审美；它们不决定项目 token，也不能替代用户选中的设计系统。

| Reference | 借鉴边界 |
| --- | --- |
| [Vercel Design](https://vercel.com/design.md) / [Dark](https://vercel.com/design.dark.md) | 设计文档组织、明暗主题表达和系统化说明；不直接复制品牌视觉 |
| [Meta Design](https://design.facebook.com/) | 大型产品系统的可读性、可扩展性与组件/内容关系；不把 Meta 品牌当作规则 |
| [Fluid Functionalism](https://github.com/mickadesign/fluid-functionalism) | 流体布局、空间关系、功能性动效和组件组合；先理解机制再适配 |
| [How I Design with AI](https://x.com/reactiverobot/status/2092638003789439075) / [可读镜像](https://www.linkedin.com/pulse/how-i-design-ai-matt-dailey-cfe1e) | 先看整体约束、删除多余元素、隔离迭代、真实数据预览、收集参考和持续训练审美 |

## 方法与设计系统的决策顺序

方法和系统不互相替代：方法规定如何工作，系统规定在选中它之后如何落地视觉和组件。发生冲突时：

1. 用户明确的产品、平台、技术、无障碍、隐私和品牌约束。
2. 用户选中的设计系统、项目实际版本和现有组件 API；如果没有系统，则使用项目规范或平台原语。
3. 已批准的项目视觉方向和真实消费代码。
4. 初空设计方法的过程启发与外部研究。

除非用户明确选择初空设计系统，否则不要强制使用初空颜色、token、组件或品牌人格。

## 一个好的任务提示

```text
Use $chukong-design.
这是一个面向长期关系维护的桌面 + 移动端工具。项目使用 [填写你的设计系统，或写“无设计系统”]。
请先确认用户、主任务、固定约束和关键状态，再用 Context → Discover → Define → Build →
Critique → Deliver → Verify 完成列表页设计。请使用脱敏真实数据预览，覆盖 loading、empty、
error、permission、retry、键盘 focus 和 reduced-motion，最后列出你读取的 reference、未核验
的假设，以及最值得我 review 的三个取舍。
```

## 质量与验收

重要任务至少在真实渲染表面检查：

- 桌面与移动端布局，以及所选设计系统支持的主题/对比度模式。
- 键盘 focus、可访问名称、触摸目标和 Dialog/Popover 的焦点回收。
- loading、empty、error、disabled、permission、retry 等适用状态。
- 代表性脱敏数据下的信息密度、文案长度和恢复路径。
- 动效是否解释状态变化，以及 reduced-motion 是否安全降级。

## 维护、反馈与使用边界

- **方法更新**：更新本仓库的 `SKILL.md`、方法摘要和工作流链接。
- **初空系统更新**：只在 [`chukong-design-system`](https://github.com/chukong-creator/chukong-design-system) 更新 token、组件、文档和实现，再同步本仓库的可选 profile 与链接。
- **其他系统项目**：以对方系统的文档和实际版本为准，不要把项目决策回写成初空规则。
- 报告问题时请附使用的 Agent、任务提示、目标平台、期望与实际结果；不要上传个人数据、凭据、私有 endpoint 或未脱敏截图。
- 本仓库是 skill 分发入口，不承诺提供运行时组件、npm 包、字体、品牌素材或任何设计系统的访问权限。
- GitHub 公开可见不等于自动授予复制和再发布许可。当前仓库尚未声明独立许可证；如需将其打包进其他产品或再发布，请先联系维护者确认授权。

## English quick start

Install globally with `npx skills add chukong-creator/chukong-design-skill -g`, then invoke `Use $chukong-design to apply the method to this interface`. The method is independent of the Chukong Design System: select Chukong, another system, or no system. When a system is selected, its real project tokens and component APIs are the implementation truth. The skill does not ship runtime components or copied brand assets.
