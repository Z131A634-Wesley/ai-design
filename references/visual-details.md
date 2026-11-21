# 组件细节：边缘、材质与反馈

用于新做可见组件、实现高保真稿或专门打磨按钮、表单、卡片、弹层。先看参考中**一个主控件和一个相邻边缘**，例如弹窗里的输入框与按钮、连排筛选或卡片图片。沿用现有组件和 token；只有缺少状态或边缘规则时才补。下面的值供缺少规范时起步。

## 边角和表面

| 部位 | 写进规格并实现 |
|---|---|
| 形状角色 | 为紧凑控件、内容容器、浮层以及实际需要的胶囊分别选圆角。相同角色和尺寸共用值。已有 6 px 按钮、10 px 容器、16 px 浮层可作为一组；直角、细圆角和大圆角按选中风格使用。短状态标签与分段控件才按内容决定胶囊。 |
| 嵌套与裁切 | 同心且等距的内外角，内角可从 `max(0px, 外角 - 边缘到内层的距离)` 起步。外角 16 px、内层外缘距外边缘 5 px 时先试 11 px，再看实际渲染。铺到容器边缘的图片继承对应外角；只裁切图片或装饰层，留出焦点外描边。 |
| 相邻控件 | 分段按钮、组合输入和 Split Button 用逻辑边角（如 `border-start-end-radius`）。外侧跟随控件形状，接缝只画一次。键盘聚焦时让当前控件的轮廓在同组可见，检查相邻层和容器裁切。 |
| 线与阴影 | 平级区域从一道稳定的 1 CSS px 边线或背景差开始，浮层才增加外阴影。控件需要光学边缘或按下材质时，可用窄内描边或 inset shadow；避免同一边缘反复叠线。边框宽度在状态间保持一致。浅色和深色各核对边界、状态色与文字；有媒体背景时看最差位置。 |
| 光学对齐 | 先统一控件高度、文字行高、图标盒与间距，在真实尺寸下检查。箭头等不对称图标必要时在固定盒里微调约 1–2 px；保持点击面积、文字基线和同行间距。长译文或放大字号时允许高度自然增长。 |

## 按钮按用途定状态

| 状态 | 反馈规则 |
|---|---|
| 默认 | 主按钮用清楚的层级，次按钮按现有边线或低权重底色。布局用 `min-block-size`、稳定边线和图标槽位，加载文案或图标切换时保留同一占位。 |
| 悬停 | 只变化一两项：实色按钮换到明确的 hover 色；描边按钮可轻填背景或加深边线。桌面指针用 `@media (hover: hover) and (pointer: fine)` 或组件库的输入感知状态。进出约 100–160 ms、缓出，短促且可反向。后台和高频表单通常保持原位；展示 CTA 如已有方向可让图标在预留槽内移动 1–2 px。 |
| 按压 | 按下立即反馈，优先用确定的 active 色或轻微内阴影，松手约 100–140 ms 返回。触屏也有按压反馈。瞬时 `:active` 与切换按钮的持久 `aria-pressed` 分开；选中状态应在移开鼠标后保留。 |
| 键盘焦点 | `:focus-visible` 即时显示，不随 hover 淡入或闪退。可从 2 px 轮廓和 2 px 偏移起步，按底色验证。复杂背景可加一层分隔色；强制色模式保留系统轮廓，例如 `outline-color: Highlight`。输入错误与聚焦同时发生时，错误状态和焦点都应可见。 |
| 禁用与等待 | 禁用关闭悬停/按压，使用独立背景、文字和边线角色。保留焦点的等待态用既有组件与状态播报，避免重复提交，包含表单回车路径。`aria-disabled` 只表意，实际操作须被代码阻止。 |
| 减少动态效果 | 关闭非必要位移、缩放及过渡，颜色、边线、焦点和状态信息即时保留。 |

在 CSS 中只列变化的属性。默认用颜色、边框色，或单个小面积阴影；大范围元素优先用 opacity/transform。若仅按压需即时变化，可在 `:active` 设 `transition-duration: 0s`，默认规则负责释放后缓回。保持点击区域固定；整体位移会让指针反复出入热区时，只动内部图标。保持连续变换可中断，避免 `transition: all`、尺寸动画和长弹簧。触屏模拟下点击后不应卡在悬停态。

### 用局部实物判断

选一个组件组合看原尺寸和放大的局部。默认截图看边缘、对齐和层级；鼠标缓慢进入、快速移出、按下再松开看是否跳动、遮挡或丢状态；Tab、Shift+Tab、Enter/Space 看焦点和行为。需要时加触屏、强制色与减少动效。用浏览器计算样式定位问题，记录当前值与目标规则。连续录屏可证明节奏，截图只能证明所拍的状态。只打磨其中一处时，检查被影响的同类组件。

参考实现均用于提炼规则。圆角按角色和上下文推导，见 [Radix Themes 的圆角 token](https://github.com/radix-ui/themes/blob/main/packages/radix-ui-themes/src/styles/tokens/radius.css)、[Carbon 的组合按钮](https://github.com/carbon-design-system/carbon/blob/main/packages/react/src/components/Button/Button.mdx#radius)；稳定边线、独立状态和图标光学对齐，见 [Primer Brand 按钮](https://github.com/primer/brand/blob/main/packages/react/src/Button/Button.module.css)、[Polaris React 归档中的按钮](https://github.com/Shopify/polaris-react-archive/blob/main/polaris-react/src/components/Button/Button.module.css)；等待态、输入方式和焦点，见 [Adobe React Aria 按钮](https://github.com/adobe/react-spectrum/blob/main/packages/react-aria-components/src/Button.tsx)。
