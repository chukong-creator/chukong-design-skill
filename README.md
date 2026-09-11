# chukong-design-skill

一个轻量、独立的 `chukong-design` Agent Skill。它不复制 token、组件源码、字体或品牌资产，
只把初空设计系统和外部研究整理成清晰的 reference map，供 Agent 在设计前按需读取。

## 这是什么

- Skill 名称：`chukong-design`
- GitHub 仓库：`chukong-creator/chukong-design-skill`
- 安装：

  ```bash
  npx skills add chukong-creator/chukong-design-skill
  ```

- 核心原则：先读取 canonical reference，再使用真实 token、组件、状态和行为；不在项目里另起一套“看起来相似”的系统。
- 访问边界：核心设计系统仓库目前是私密仓库，使用者需要相应 GitHub 权限或本地 checkout。

这不是完整的 UI 组件库，也不是 `chukong-creator/chukong-design` 的副本。完整的 HTML 原型、设计系统编译和预览工作流仍参考[公开版 chukong-design](https://github.com/chukong-creator/chukong-design)。

## References

### 1. Canonical：初空设计系统（优先级最高）

[chukong-creator/chukong-design-system](https://github.com/chukong-creator/chukong-design-system)

这是实现与决策的唯一事实源。按任务读取：

| Reference | 用途 |
|---|---|
| [`DESIGN.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/DESIGN.md) | AI 设计契约：人格、token 层级、组件边界、状态、无障碍、内容与完成信号 |
| [`docs/style-brief.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/style-brief.md) | 视觉方向：低饱和雾蓝灰骨架、草木绿生命辅助、陶土暖色、米白画布、密度与材质 |
| [`docs/components.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/components.md) | 组件选择、组合方式、状态和禁用/错误边界 |
| [`docs/motion.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/motion.md) | 功能性运动、节奏、退出速度与 reduced-motion |
| [`docs/adoption.md`](https://github.com/chukong-creator/chukong-design-system/blob/main/docs/adoption.md) | 消费项目接入、升级和迁移 |
| `packages/tokens/src` | DTCG token 源；不要在页面里重定义品牌变量 |
| `packages/react/src` | React 组件与行为实现；需要精确 API 时读取 |

### 2. Workflow：公开版 chukong-design

[chukong-creator/chukong-design](https://github.com/chukong-creator/chukong-design)

用于 HTML 设计产出、交互原型、设计系统编译/checker、浏览器预览和 AI 设计循环。
其中的 `references/ai-design-loop.md` 以及 `references/quality/` 可作为重要工作的过程参考，
但不能替代初空设计系统的 canonical token 与组件契约。

### 3. 外部研究与灵感

这些资料只用于提出问题、比较机制和训练审美；最终决策必须回到初空设计契约、产品约束和用户反馈。

| Reference | 借鉴边界 |
|---|---|
| [Vercel Design](https://vercel.com/design.md) / [Dark](https://vercel.com/design.dark.md) | 设计文档的组织方式、明暗主题表达、系统化说明；不直接复制品牌视觉 |
| [Meta Design](https://design.facebook.com/) | 大型产品系统的可读性、可扩展性与组件/内容关系；不把 Meta 品牌当作初空规则 |
| [Fluid Functionalism](https://github.com/mickadesign/fluid-functionalism) | 流体布局、空间关系、功能性动效和组件组合的研究样本；先理解机制再适配 |
| [How I Design with AI](https://x.com/reactiverobot/status/2092638003789439075) / [可读镜像](https://www.linkedin.com/pulse/how-i-design-ai-matt-dailey-cfe1e) | 先看整体约束、删除多余元素、隔离迭代、组件库、真实数据预览、收集参考、持续训练审美 |

## Reference precedence

1. 用户明确的产品、平台、技术、无障碍和隐私约束。
2. `chukong-design-system/DESIGN.md` 及其实现 token/组件。
3. 已批准的项目视觉方向与真实消费代码。
4. 本 README 列出的外部研究。

外部截图、代码或文案不是产品事实。借鉴时记录来源、观察到的机制、要迁移的部分、要避免复制的部分；
不得复制私有内容、品牌标志、受版权保护的独特素材或未获许可的实现。

## 使用约定

- 私有 canonical reference 不可读取时，停止猜测并请求权限或本地文件。
- 设计系统消费项目优先使用 `@chukong-design/react/styles.css` 和公开组件 API。
- 完成前检查 desktop/mobile、light/dark、high-contrast、键盘/focus、reduced-motion 及适用的 loading/empty/error/permission/retry 状态。
- 真实数据验证使用脱敏 staging 或代表性 fixture；不要把 mock 当成已完成的后端集成。
- 这个仓库只维护 reference map 和 Skill 入口；token、组件和实现更新应在 `chukong-design-system` 中完成，然后更新本 README 的链接说明。
