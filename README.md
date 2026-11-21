# ai-design

把前端设计需求转成可以确认、实现和验收的 Design Spec。适用于官网、落地页、后台、Web App、Dashboard、H5、移动界面和设计评审。支持现有 Vue、React 或原生 Web 项目。

## 调用

在 Codex 中输入：

> $ai-design 为采购团队做一个桌面优先的订单后台。优先处理逾期项。请先推荐风格和 Design Spec，我确认后再开发。

有参考图、设计稿或项目页面时一起给出。已有完整方向可直接进入方案；新页或改版在确认规格后实现。局部改动沿用原系统。只想看方案、线框或评审时，直接说明交付物。

## 设计方法

[按场景选布局](references/scenario-routing.md)，按任务 [调用外部设计 Skill](references/external-design.md)。官网、SaaS、编辑器、移动端和看板各有结构与状态手册。高保真方案使用用户认可的参考、已有产品界面或本项目草案，写进同一份 Design Spec。

## 如何维护

- [调用流程](SKILL.md) → [Design Spec](templates/design-spec.template.md) → [浏览器验收](references/quality-gates.md)。
- [进阶视觉效果](references/effects.md) 按需加载，并按同一规格实现与验收。
- [研究与来源](references/source-map.md) 记录采用的设计方法与外部参考。
- 安装到其他环境可在目标项目运行 `npx skills add Z131A634-Wesley/ai-design --skill ai-design`，或复制整个目录。远程版本以仓库发布内容为准。

本项目采用 [MIT 许可证](LICENSE)。第三方链接、工具与素材遵循各自许可。
