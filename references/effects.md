# 视觉效果与动效：按需选用

先确认内容、布局和交互是否需要效果。效果应帮助识别层级、状态或空间关系；可静态表达时无需添加。不要让装饰遮挡正文、导航、焦点环或操作，不用固定遮罩截获滚动或点击。

## 材质与渐变

- **玻璃**：优先用于浮于内容上方的少量导航、工具栏或关键控制，不把正文、列表和每张卡片都做成玻璃，也不叠放玻璃层。Apple 的 Liquid Glass 是原生系统材质；网页模糊只是视觉借鉴。
- 先设足够不透明的纯色背景，再用 `@supports (backdrop-filter: blur(12px))` 渐进增强为半透明背景和模糊。媒体内容下方明暗变化时，使用局部遮罩或更不透明的底色，检查文字与图标在最差背景上的对比；普通文字至少 4.5:1，大号文字至少 3:1。较大面板通常需要更不透明的底色。`prefers-reduced-transparency` 支持有限，不能作为唯一保障。
- **CSS 渐变**：用少量相邻色、柔和变化和稳定的文字底色营造氛围；避免多层高饱和光斑争抢标题。渐变可静态存在，无需持续运动。图像缺失时仍应有可读的底色。

## 交互与运动

- **微交互**：按钮和表单的悬停、按压、焦点及尺寸稳定性见 [组件细节](visual-details.md)。本手册的时长建议针对编排与过渡，控件反馈优先沿用项目 token 或组件手册的较短时长。
- **频次与中断**：高频切换和键盘连续操作时，内容与焦点立即可用。可反复切换的两态优先用能从中间状态反向的过渡。弹层的视觉退场可短暂保留画面；焦点约束和点击拦截按当前打开状态管理。走一遍打开 → 关闭 → 立刻重开，再在减少动效模式复查，确认无闪帧、残留遮罩或焦点丢失。
- **滚动与页面切换**：只给少数关键段落使用短暂的淡入或小幅位移；内容默认可见，脚本、观察器或动画失败时仍可阅读和操作。不要把首屏、主标题、按钮或键盘焦点藏在延迟动画中；用户滚得快时直接显示终态。页面切换避免阻止导航，返回与深链接应正常工作。
- **视差**：仅在确有叙事价值时用于少量非关键背景，限制位移幅度，不影响正文和操作。移动端、低性能设备、后台标签页或用户要求减少动态效果时，停用并显示静态画面。不得将视差与滚动劫持绑定。
- **建议起点**：展开或页面状态变化 200–350 ms，使用自然缓出曲线如 `cubic-bezier(.2,.8,.2,1)`。同屏同时运动的元素宜少，避免长序列和无限循环；重要操作可立即响应。以实际设备流畅度为准，连续动画以接近设备刷新率为目标，掉帧时先减少面积、层数和效果。
- 遵循 `prefers-reduced-motion: reduce`：移除视差、循环、长距离位移和缩放，必要的状态变化改为即时切换或短淡入；用户仍能获得相同信息和操作。自动播放的背景视频应停止或替换为静态图；需要持续播放的内容提供可访问的暂停或关闭控制。

## 实现与验收

优先用 CSS transition、animation 和原生浏览器能力完成简单效果；仅在需求明确且收益超过包体及维护成本时引入依赖。复杂编排、手势和 React 状态联动可考虑 Motion；复杂时间线和跨元素编排可考虑 GSAP；真实三维、交互式场景才考虑 Three.js。选用前检查当前许可证、打包大小及资源许可；Motion 与 Three.js 的主仓库为 MIT，示例素材可能另有许可。

尽量动画化 `transform`、`opacity`，避免频繁触发布局或大面积重绘；模糊和多层透明效果要实机测量。仅在发现性能问题时谨慎使用 `will-change`。任何装饰层都不应覆盖操作或阻断指针事件；可关闭的效果应有清晰可聚焦的关闭控件，关闭后恢复正常阅读和操作。

验收时检查桌面与手机、键盘与触屏、窄屏及缩放、明暗背景、滚动中遮挡、弱设备、减少动态效果，以及不支持模糊、JavaScript 失败或资源未加载时的可用性。确认首屏和焦点始终可见，运动不会强制用户等待。

## 参考资料

- [Apple：Meet Liquid Glass](https://developer.apple.com/videos/play/wwdc2025/219/)
- [Apple：Adopting Liquid Glass](https://developer.apple.com/documentation/TechnologyOverviews/adopting-liquid-glass)
- [MDN：backdrop-filter](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/backdrop-filter)
- [MDN：prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/%40media/prefers-reduced-motion)
- [MDN：prefers-reduced-transparency](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/%40media/prefers-reduced-transparency)
- [MDN：透明度与文字对比](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/opacity)
- [W3C：Focus Appearance](https://www.w3.org/WAI/WCAG22/Understanding/focus-appearance)
- [web.dev：高性能 CSS 动画](https://web.dev/articles/animations-guide)
- [Motion：useReducedMotion](https://motion.dev/docs/react-use-reduced-motion)
- [Motion 许可证](https://github.com/motiondivision/motion/blob/main/README.md)；[Three.js 许可证信息](https://github.com/mrdoob/three.js/blob/dev/package.json)
- [Emil Kowalski 的设计工程 Skill](https://github.com/emilkowalski/skills/blob/main/skills/emil-design-eng/SKILL.md)；[Radix Presence](https://github.com/radix-ui/primitives/blob/main/packages/react/presence/src/presence.tsx)
