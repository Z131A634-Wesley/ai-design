# 前端工程实现规范

用途：**界面做对之后，别在工程层面毁掉它。** 只管与 UI 质量相关的部分，不做通用前端架构评审。

原则：**优先适配项目已有的技术栈、组件库与设计系统**。下面的规则只在项目没有既定做法时采用。

---

## 一、目录与依赖方向

采用 feature-first（按功能分，不按文件类型分）：

```
src/
├── app/            # 应用装配、路由、provider
├── components/     # 跨应用共享组件
├── features/<域>/  # 每个域自包含：components / hooks / api / types / utils
├── hooks/  lib/  types/  utils/   # 共享底层
```

**单向依赖（硬规则）**：`shared → features → app`。反方向禁止。

- features 之间**不许互相 import**；组合放在 app 层
- 用 ESLint `import/no-restricted-paths` 强制，别靠自觉
- **不用 barrel 文件**（`index.ts` 全量 re-export）：影响 tree shaking，还会掩盖循环依赖

> 依据：`alan2207/bulletproof-react`（未核实许可，仅借鉴结构思路）。

## 二、组件复用判据

不要提前抽象，也不要复制到第四份。

| 信号 | 动作 |
|---|---|
| 出现第 2 次 | 先复制，观察差异点 |
| 出现第 3 次，且变体 ≤ 3 种 | 提取为组件，用 variant 参数控制 |
| 出现第 3 次，但变体在 4 种以上且差异大 | **不要合并**，抽公共基元（间距/边界/焦点），保留两个组件 |
| 只是样式相似、语义不同 | 不合并（按钮 ≠ 链接，视觉像也不行） |

**提取时必做**：把状态矩阵（见 `interaction-ux.md`）一并实现，否则提取出来的是个空壳。

## 三、Design Tokens 落地

- token 定义在**一个地方**：`:root` 的 CSS 自定义属性，或设计系统的 theme 配置
- 组件里**禁止硬编码色值/间距**：`#fff`、`bg-white`、`padding: 17px` 一律改 token
- 需要动画或类型约束的自定义属性，用 `@property` 注册（可拿到类型与初始值）
- 语义 token 优先于 primitive：组件消费 `--accent-background-color-default`，不要去引用 `--blue-900`
- 深色/浅色主题只换 token 值，**不改组件代码**

自检：全局搜 `#[0-9a-fA-F]{3,6}`，出现在组件文件里就是违规（token 定义文件除外）。

## 四、类型与正确性

- `strict: true` 必开
- 禁止 `any`：用 `unknown` + 类型守卫，或泛型
- 建议开 `noUncheckedIndexedAccess`，堵住越界访问
- 组件 props 用**判别联合**表达互斥状态（`loading` 时不该允许 `onClick`），而不是一堆可选布尔
- 事件处理器的类型从库里推导，不要手写 `any` 兜底

## 五、样式策略

- **低特异性**：优先单类名；不用 ID 选择器；嵌套 ≤ 2 层
- 复杂项目用 `@layer` 显式管理层叠顺序，别用 `!important` 打架
- 警惕**选择器互相抵消**：`.section { padding: 96px }` 与 `.cta { padding: 64px }` 作用在同一元素上时，后写的赢，靠顺序而不是靠意图——用手写工具类或显式组合避开
- 响应式优先 **container queries**（组件跟随容器），页面级才用媒体查询
- 颜色用 `oklch()` 时，阶梯等距才有感知等距；用 hex 时要手测对比度

## 六、性能（只列会毁掉 UI 的）

| 项 | 要求 |
|---|---|
| 动画属性 | 只动 `transform` / `opacity`；不动 `top/left/width/height` |
| 图片 | 必须写 `width`/`height`（防 CLS）；用 `srcset`；懒加载首屏以下的图 |
| 首屏大图 | `fetchpriority="high"`，别懒加载 LCP 元素 |
| 字体 | 自托管 + `font-display: swap` + 子集化；禁止外链 Google Fonts |
| 长列表 | 虚拟化或分页；别一次渲染 500 行 |
| 3D / shader | 必须懒加载 + 静态降级；WebGL 上下文 ≤ 4 |

## 七、语义与可访问

- 用对的元素：`button` 不是 `div`，`a` 不是 `onClick` 的 `span`，列表是 `ul/li`
- 一个页面一个 `h1`，标题层级不跳级
- 图片 `alt`：有信息就写描述，纯装饰写 `alt=""`
- 表单控件必须有可关联的 `label`
- 装饰性图标加 `aria-hidden="true"`

## 八、验证项目已有脚本

用项目实际工具链运行相关 build、typecheck、lint 和测试。无构建的 HTML 原型不强加 npm，纯 JavaScript 不强行装 TypeScript。不按通用命令名猜测脚本、不隐式联网下载安装。再按 [质量闸门](quality-gates.md) 验实际界面。

## 九、不要做的事

- 不为一个视觉小需求引入新的 UI 库 / 动画库 / CSS-in-JS
- 不为了"统一"重写项目已有的组件体系
- 不引入与当前栈冲突的样式方案（Tailwind 项目里塞 CSS Modules 之类）
- 不在组件里写业务数据（文案与数据走 content / props）

---

## 来源与许可

目录结构与单向依赖：思路来自 `alan2207/bulletproof-react`（**许可未核实**，仅借鉴结构）。
CSS/@property/container queries/性能条目：部分参考 `thedaviddias/Front-End-Checklist`（**MIT**）的 CSS 与 Images 类规则，**重写并裁剪为 UI 相关部分**；完整 386 条请直接用它。
`strict` / `noUncheckedIndexedAccess` / `no-any` 属通用 TS 实践。
