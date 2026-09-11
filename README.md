# chukong-design-skill

面向设计师、前端工程师和 AI Agent 的**初空设计方法**。它专注于如何理解问题、探索方向、构建设计、独立批评、做减法和验证交付，而不是规定某一种品牌颜色、组件库或视觉模板。

> This is a method-first Agent Skill. It can be used with an existing product language, a platform's native patterns, or a blank canvas.

## 这个 skill 解决什么问题

AI 很容易直接生成一张“看起来完成”的界面，却没有先理解用户任务，也没有经过真实渲染、状态检查和视觉取舍。初空设计方法把设计工作变成一个可回看、可批评、可验证的闭环：

- 先定义用户、任务、约束和失败条件，再谈风格。
- 方向开放时探索少量真正不同的可能，不用无意义变体凑数量。
- 把选中的方向写成可执行的设计身份和质量 rubric。
- 用代表性数据渲染真实页面，而不是只看源代码或静态草图。
- 让视觉批评聚焦渲染结果，最后用减法提升品质。
- 验证桌面、移动、键盘、状态、动效和运行时，而不是把评分当成完成证明。

它可以套在已有品牌、产品规范、组件库、平台原语或没有既定规范的项目上；实现时遵循目标项目已经做出的明确决策。

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
Use $chukong-design to apply the design method to this settings page.
请用 $chukong-design 设计这个空状态、加载态和错误恢复路径，并说明每轮验证证据。
```

如果 Agent 不支持显式 `$skill-name`，说明“按初空设计方法设计/评审”即可。

### 第一次使用建议

给 Agent 提供以下最小上下文：

1. 产品类型、用户、场景和当前任务。
2. 目标平台（桌面、移动端或响应式）以及需要覆盖的状态。
3. 当前产品已有的品牌、布局、组件、内容和技术约束；没有就明确说明。
4. 真实/脱敏数据样本、验收路径和你希望保留或避免的感觉。

## 初空设计方法：从灵感到可验证界面

这套方法借鉴 Claude Design 工作流里最有价值的部分，并改写成跨 Agent、跨产品语言可执行的闭环。它不是某个模型的隐藏 prompt，也不是要求每个小改动都走完整流程。适用于新视觉方向、重要页面、高保真原型和质量敏感的重设计；小 bug、单个 token、纯无障碍审查或短文案修改可以直接处理。

完整公开参考：[`ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/ai-design-loop.md)；Claude Code 的工具适配：[`claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/claude.md)。

| 环节 | 具体做法 | 产生的证据 |
| --- | --- | --- |
| **Context** 上下文 | 说清用户、场景、主任务、固定约束、真正开放的选择和失败条件；已有界面先描述现状。 | 约束简报、状态清单、验收标准 |
| **Discover** 探索 | 方向开放时只提出 2–3 个真正不同的高层方向，说明感觉、构图、材质/排版和记忆点；让用户选择，不为凑数制造变体。 | 方向卡、参考来源、选择/拒绝理由 |
| **Define** 定义 | 将选中的方向冻结为设计身份：情绪意图、布局拓扑、视觉角色、密度、主动作和 anti-reference。 | build brief、稳定的质量 rubric |
| **Build** 构建 | 遵循目标项目已有规范；没有规范时使用清楚的布局、可访问的原语和可解释的默认值。用代表性脱敏数据做可运行渲染，只有在有意义时才加入图片、3D、shader 或视频。 | 可打开的页面、交互状态、数据样本 |
| **Critique** 批评 | 实现者与视觉批评者尽量分离；批评者只看新鲜渲染结果和同一套 rubric，不被代码或实现者解释说服。反馈固定为“有效之处 → 最大缺口 → 按优先级的修复 → 有证据的评分 → 未核验问题”。 | 截图/页面、优先级反馈、未核验问题 |
| **Deliver** 交付减法 | 逐项询问元素是否提升理解、行动、信任、定位、反馈或目标感受；删除装饰性复杂度。 | 减法记录、保留/删除理由 |
| **Verify** 验证 | 检查真实渲染路径和运行时错误，覆盖桌面/移动、鼠标/触摸/键盘、焦点、对比度、reduced-motion 和适用状态，并做 5 秒主信息检查。 | 浏览器检查、剩余风险、用户 review 点 |

核心不是“多做几版”，而是让每轮迭代都有明确问题、稳定评价尺和可回看的证据；如果质量不收敛，应回到方向或 rubric，而不是无限微调。

## 参考地图

### 方法参考

- 本仓库的 [`skills/chukong-design/SKILL.md`](skills/chukong-design/SKILL.md)：跨 Agent 的最小可执行入口。
- [`ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/ai-design-loop.md)：Context、Discover、Define、Build、Critique、Deliver、Verify 的完整操作说明。
- [`claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/claude.md)：将预览、截图、HTTP 服务和调试动作映射到 Claude Code 工具的说明。

### 外部研究与灵感

这些资料用于提出问题、比较机制和训练审美，不是项目事实，也不应被直接复制：

| Reference | 借鉴边界 |
| --- | --- |
| [Vercel Design](https://vercel.com/design.md) / [Dark](https://vercel.com/design.dark.md) | 设计文档组织、明暗主题表达和系统化说明；不直接复制品牌视觉 |
| [Meta Design](https://design.facebook.com/) | 大型产品的可读性、可扩展性与组件/内容关系；不把 Meta 品牌当作规则 |
| [Fluid Functionalism](https://github.com/mickadesign/fluid-functionalism) | 流体布局、空间关系、功能性动效和组件组合；先理解机制再适配 |
| [How I Design with AI](https://x.com/reactiverobot/status/2092638003789439075) / [可读镜像](https://www.linkedin.com/pulse/how-i-design-ai-matt-dailey-cfe1e) | 先看整体约束、删除多余元素、隔离迭代、真实数据预览、收集参考和持续训练审美 |

## 方法契约

方法规定工作方式，不替用户做未经授权的品牌或产品决策：

1. 用户明确的产品、平台、技术、无障碍、隐私和品牌约束优先。
2. 已有项目规范和真实消费代码优先于模型记忆或外部截图。
3. 事实、推断、建议和未核验风险分开表达。
4. 重要任务必须检查真实渲染表面、关键状态和交互路径。
5. 外部参考只迁移可解释的机制，不复制独特素材、品牌标志、私有内容或未获许可的实现。

## 一个好的任务提示

```text
Use $chukong-design.
这是一个面向长期关系维护的桌面 + 移动端工具。请先确认用户、主任务、固定约束和关键状态，
再用 Context → Discover → Define → Build → Critique → Deliver → Verify 完成列表页设计。请使用
脱敏真实数据预览，覆盖 loading、empty、error、permission、retry、键盘 focus 和 reduced-motion，
最后列出你读取的 reference、未核验的假设，以及最值得我 review 的三个取舍。
```

## 质量与验收

重要任务至少在真实渲染表面检查：

- 桌面与移动端布局，以及项目实际支持的主题/对比度模式。
- 键盘 focus、可访问名称、触摸目标和 Dialog/Popover 的焦点回收。
- loading、empty、error、disabled、permission、retry 等适用状态。
- 代表性脱敏数据下的信息密度、文案长度和恢复路径。
- 动效是否解释状态变化，以及 reduced-motion 是否安全降级。

## 维护、反馈与使用边界

- **方法更新**：更新本仓库的 `SKILL.md`、方法摘要和参考链接。
- 报告问题时请附使用的 Agent、任务提示、目标平台、期望与实际结果；不要上传个人数据、凭据、私有 endpoint 或未脱敏截图。
- 本仓库是 skill 分发入口，不承诺提供运行时组件、npm 包、字体、品牌素材或任何特定产品系统。
- GitHub 公开可见不等于自动授予复制和再发布许可。当前仓库尚未声明独立许可证；如需将其打包进其他产品或再发布，请先联系维护者确认授权。

## English quick start

Install globally with `npx skills add chukong-creator/chukong-design-skill -g`, then invoke `Use $chukong-design to apply the method to this interface`. The skill is method-first and system-agnostic: it focuses on context, exploration, critique, subtraction, and verification, while leaving brand and component decisions to the target project.
