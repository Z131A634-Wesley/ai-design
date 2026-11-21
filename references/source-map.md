# 设计研究与外部参考

本文件用于维护规则证据和补充专业案例。新视觉、高保真与视觉打磨按 [外部设计 Skill 调用](external-design.md) 选主方法。优先打开用户图稿或参考链接；方向开放或缺少真实视觉依据时主动查找同类成品。场景手册决定任务和平台边界。

| 一手来源 | 提炼到本 Skill 的做法 |
|---|---|
| [Anthropic frontend-design](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md) | 用真实内容决定字阶、构图和主视觉，用换品牌测试识别通用模板。在 [视觉诊断](visual-craft.md) 中采用这个问题，保留用户指定的审美。 |
| [Impeccable](https://github.com/pbakaus/impeccable/blob/main/skill/SKILL.src.md) 与 [Critique rubric](https://github.com/pbakaus/impeccable/blob/main/skill/reference/critique-rubric.md) | 按界面用途分配表达强度，区分改版与保留身份的局部修订，分开审美评审与技术审计。对应 [视觉诊断](visual-craft.md) 和 [质量闸门](quality-gates.md)。 |
| [Taste Skill](https://github.com/Leonxlnx/taste-skill) | 用真实资产与浏览器实物校对布局。吸收素材真实性和复审思路；本 Skill 由页面用途决定是否需要动效或大图。 |
| [Carbon 代码](https://github.com/carbon-design-system/carbon)、[色彩角色](https://www.carbondesignsystem.com/building-blocks/foundations/color/tokens)、[网格](https://www.carbondesignsystem.com/building-blocks/foundations/2x-grid/overview) | 区分表面层次、选中、焦点、状态与强调，使用可压缩网格及紧凑尺寸。用于 [业务界面](product-ui.md) 和 [组件细节](visual-details.md)。 |
| [Primer Primitives](https://github.com/primer/primitives) 与 [布局](https://primer.style/product/getting-started/foundations/layout/) | 语义角色映射到实现 token，宽度变化由内容触发。用于 [项目主规范](design-md-schema.md) 和 [工具工作区](workspace-ui.md)。 |
| [Material Components Android](https://github.com/material-components/material-components-android) 与 [Android 自适应布局](https://developer.android.com/develop/adaptive-apps/guides/get-started-with-adaptive-apps) | 以可用窗口宽度和任务选择单栏、侧轨或列表详情；Web 与原生的单位、返回和焦点分别核对。用于 [移动平台](mobile-ui.md)。 |
| [Apple Liquid Glass](https://developer.apple.com/videos/play/wwdc2025/219/) 与 [CSS backdrop-filter](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/backdrop-filter) | 玻璃集中在浮动功能层，内容采用稳定实底；Web 从实色渐进增强。用于 [材质与动效](effects.md)。 |
| [Radix Primitives](https://github.com/radix-ui/primitives)、[ARIA APG](https://www.w3.org/WAI/ARIA/apg/) 与 [WCAG 2.2](https://www.w3.org/TR/WCAG22/) | 组件外观与行为分开，复用焦点、键盘和可访问名称惯例，实测对比与目标尺寸。对应 [交互](interaction-ux.md) 和 [质量闸门](quality-gates.md)。 |

需要外部案例时，先识别缺口是构图、组件还是流程，再找同类成品或平台官方模式。给一条主参考和必要的辅助参考，记录“看到什么 → 应用在哪里”。只有搜索摘要时注明未看到画面。选用第三方资产前逐项核对许可。
