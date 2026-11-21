# 轻透导航 · Light Glass

用于照片、视频、地图或媒体浏览，需要让导航与内容分层。受 Apple Liquid Glass 的材质分工启发，Web 采用 CSS 玻璃近似。原生平台优先使用系统组件。表格、长文本、密集后台和系统错误须有稳定的实底。

~~~css
--canvas: #eaf0f6;
--surface: #f8fbff;
--surface-hover: #e6eef9;
--text: #172637;
--muted: #46586f;
--line: #ccd8e5;
--control-line: #677a91;
--accent: #24518c;
--accent-hover: #1d3e6c;
--on-accent: #ffffff;
--focus: #24518c;
--accent-soft: #dce9fa;
--glass: rgb(248 251 255 / 88%);
~~~

- **字阶**：system-ui，主标题 52–72 px / 1.03，窄屏 36–44 px / 1.08，分区 26/32、正文 16/24、辅助 13/19。
- **布局**：4/8/12/16/24/32/48/64 px；桌面构图可让原始媒介占上半屏，下方是实底内容。桌面内容不超 1200 px，窄屏 ≤720 px 保留一条导航并给安全区和滚动内容留空间。
- **组件**：圆角 999 px 的浮动导航，按钮 44–48 px、12 px 或胶囊圆角，实底内容面 16 px、1 px line。焦点用 2 px focus 外描边。导航边线 1 px，阴影 0 8px 24px #17263724。先用 surface 兜底；仅在 @supports 下为一个功能导航层用 glass + blur(12px)，更复杂的背景退回实底；表单和卡片沿用稳定实底。
- **动效**：高亮与触控反馈 160 ms，浮层 220–280 ms cubic-bezier(.2,.7,.2,1)，禁重叠玻璃和持续大幅模糊。减少动效下即时；支持降低透明度时恢复实底，并测浅/深/高纹理底的文字对比。详见 [材质验收](../effects.md)。
