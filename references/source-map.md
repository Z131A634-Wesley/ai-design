# 多源整合索引与取材地图

**定位**：本 Skill 已整合工作方法；下方是证据链与查找入口，不是必装清单。用户参考与项目成品优先；需要找视觉方向、对照交互或核实当前平台惯例时主动取材。遵守项目和用户的网络、依赖及素材约束；联网看案例与复用外部素材是两个不同的决定。

## 上游 Skill → 本 Skill 中可直接执行的动作

| 来源 | 已吸收的方法 | 执行位置 |
|---|---|---|
| [Refero Skill](https://doc.refero.design/skill/overview.md) | 风格／具体界面／流程分别查证；挑一个主方向，其他参考只解决一个问题；把观察变成决定 | [视觉设计方法](visual-craft.md) 取材与定方向 |
| [Anthropic frontend-design](https://github.com/anthropics/skills/tree/main/skills/frontend-design) 与 [Block frontend-design](https://github.com/block/agent-skills/tree/main/frontend-design) | 先按真实内容定字体、配色、构图和识别点，再复查是否只换品牌名就能复用。明确方向，不照搬字体和风格禁令 | [视觉方法](visual-craft.md)、[风格取舍](style-direction.md) |
| [Impeccable](https://impeccable.style/docs/new-work/) | 新方向比较与变化范围，区分先做稿和直接实现；对照方向做视觉复审，技术验证单独跑 | [视觉方法](visual-craft.md)、[质量闸门](quality-gates.md) |
| [Taste Skill](https://github.com/Leonxlnx/taste-skill) | 按场景选择内容主导的首屏、克制装饰效果；用真实内容和宽窄画面查空视觉、坏断行、错位、占位文案 | [营销页面](section-playbook.md)、[视觉方法](visual-craft.md)、[质量闸门](quality-gates.md) |
| [UI UX Pro Max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | 以项目主规范管共性，页面只记录不同的决定，不复制整个设计数据库 | [设计规范约定](design-md-schema.md) |
| [Vercel Web Interface Guidelines](https://github.com/vercel-labs/web-interface-guidelines) | 将表单、键盘、适配等经验落成有证据的检查条目，不套技术栈或固定阈值 | [交互手册](interaction-ux.md)、[质量闸门](quality-gates.md) |

## 有视觉问题时，直接选专项站点

| 来源 | 看什么 | 如何决定 |
|---|---|---|
| [Refero Styles](https://styles.refero.design/) | 成品风格、排版、表面和图片角色；[Refero MCP](https://doc.refero.design/mcp/tools.md) 可按已有权限找界面和流程 | 提取成一套字体、语义色与构图规则；MCP 不是前置依赖 |
| [VibeFather](https://github.com/liyupi/awesome-vibe-coding-websites) | 看可运行结果与对应 `DESIGN.md`、公开 prompt 如何对上 | 只链接上游并提炼通用方法；上游 prompt、DESIGN.md 与仓库文字适用 [CC BY-NC 4.0](https://github.com/liyupi/awesome-vibe-coding-websites/blob/main/LICENSE)，不随本项目再发布。预览图、截图和演示源码也不打包 |
| [Supahero](https://supahero.io/) | 标题在视觉左边、覆盖图像还是由产品界面主导 | 记第一眼看哪、图片占比、窄屏怎么叠放；不抄品牌文案 |
| [Navbar Gallery](https://navbar.gallery/) | 顶部、侧边、下拉、全屏如何容纳不同信息架构 | 选结构后核当前项、窄屏和键盘；不能由截图猜出行为 |
| [Footer Design](https://footer.design/) | 底部信息分组、导航与品牌收束 | 只借对当前站点有用的列结构和层级；非营销任务不强套 |
| [CTA.gallery](https://cta.gallery/) | 行动语义与主次位置、状态反馈 | 先确定动作和上下文，再借形式；不套竞争性按钮或动效 |
| [Scrolltide](https://scrolltide.co/) | 滚动叙事、微交互、特殊组件的节奏 | 看触发、进出、手机与静态回退；示例或代码授权需单独核对 |
| [3dicons](https://3dicons.co/about) | 统一材质、角度、光照的图标语言 | 只在确实服务产品时用；核对所用资源条目的许可，不把 V1 授权延伸至全站 |
| [Liquid Glass](https://glass.samasante.com/) | Web 折射、半透明层的边界和文字对比 | 实时折射是可选做法，不替代系统 App 组件；无必要优先静态方案 |

## 场景规范与原型

| 要解决的问题 | 权威参考 | 已整合到 |
|---|---|---|
| 登录、表单恢复、多步确认 | [Carbon Login](https://www.carbondesignsystem.com/building-blocks/core/patterns/login)、[GOV.UK](https://github.com/alphagov/govuk-design-system)、[WCAG 可访问认证](https://www.w3.org/WAI/WCAG22/Understanding/accessible-authentication-minimum.html) | [账户](account-flows.md)、[多步操作](task-flows.md) |
| 业务表格、图表与主题 | [Carbon Data Table](https://www.carbondesignsystem.com/building-blocks/core/components/data-table/guidelines)、[Chartability](https://chartability.github.io/POUR-CAF/)、[Primer Primitives](https://github.com/primer/primitives)、[Spectrum Design Data](https://github.com/adobe/spectrum-design-data) | [业务界面](product-ui.md)、[图表](data-viz.md)、[主题与布局](foundations.md) |
| 原生、小程序、H5 | [Apple HIG](https://developer.apple.com/design/human-interface-guidelines/)、[Android Adaptive](https://developer.android.com/develop/ui/compose/layouts/adaptive)、[微信小程序](https://developers.weixin.qq.com/miniprogram/design/)、[WeUI](https://github.com/Tencent/weui) | [移动端](mobile-ui.md)；系统行为以目标平台为准 |
| 线框、可点流程 | [NN/g Wireflows](https://www.nngroup.com/articles/wireflows/)、[Penpot Prototyping](https://help.penpot.app/user-guide/prototyping-testing/prototyping/) | [原型手册](prototyping.md)；流程节点、触发、转移与返回，不绑定工具 |
| 无障碍、响应式、工程质量 | [WCAG](https://www.w3.org/TR/WCAG22/)、[ARIA APG](https://www.w3.org/WAI/ARIA/apg/)、[Radix Primitives](https://www.radix-ui.com/primitives)、[MDN 容器查询](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Containment/Container_queries)、[Front-End Checklist](https://github.com/thedaviddias/Front-End-Checklist) | [交互](interaction-ux.md)、[共享基础](foundations.md)、[前端工程](frontend-eng.md)、[验收](quality-gates.md) |

这些方法重写为同一套规则，没有打包第三方 Skill 全文、代码、设计稿、截图或许可不清的资产。动效库、组件库和素材是否引入，按项目另作决定。
