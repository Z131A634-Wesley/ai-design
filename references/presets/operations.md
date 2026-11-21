# 业务工作台 · Operations

适合高频处理、列表详情、审阅和 Dashboard 的操作区。以清晰的分组和可扫描的异常队列建立识别度。品牌叙事与大图展示用其他预设。

~~~css
--canvas: #f3f5f8;
--surface: #ffffff;
--surface-hover: #edf2f8;
--text: #182536;
--muted: #52647a;
--line: #d5dde7;
--control-line: #697a90;
--accent: #254f9e;
--accent-hover: #1f407e;
--on-accent: #ffffff;
--focus: #254f9e;
--accent-soft: #e4edff;
--warning: #854114;
--warning-soft: #ffeed5;
--success: #176149;
--success-soft: #e3f4eb;
~~~

- **字阶**：system-ui 加项目语言后备；页标题 32/38、区标题 18/24、表格与正文 14/20、字段与辅助 12/16。标题 650–700，正文 400；数字用 tabular-nums。
- **布局**：4/8/12/16/24/32/48 px，桌面侧栏 216–240 px，内容区边距 24–32 px。结构为导航 → 标题与首要任务 → 扁平摘要 → 筛选条与工作表。表格默认 44 px 行高、12–16 px 单元格边距、精密比较保留列对齐。适合一侧详情时留 320–400 px；宽度不足 900 px 时折叠导航，低于 600 px 按任务压缩字段并在详情保留完整信息，边距 16 px。
- **组件**：按钮 40 px，圆角 6 px，主操作实色；表单边界用 control-line，焦点 2 px 实线外偏移。卡片 8 px、1 px line，普通层无阴影；浮层可用 0 12px 32px #18253620。选中行使用 accent-soft 加明确文本或图标。状态色配文字和浅底，可读性比颜色数量优先。移动主触点 44 px 起。
- **动效**：hover/active 120 ms ease-out，面板约 180 ms，变化时保留位置或焦点；减少动态效果下即时。确定局部密度或品牌色变化后，在同一规格中补齐交互状态。
