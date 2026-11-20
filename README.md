# ai-design

**一个 Skill，覆盖从 UI/UX 设计到界面实现与评审。**

`ai-design` 把不同项目的设计方法整合到一个入口。智能体按**平台、场景和交付物**选择规则：小改沿用现有设计系统，新设计先定方向，成品交付前再分别检查视觉、交互和技术质量。它不是组件库，也不要求另外安装上游 Skill。

[安装](#安装) · [怎么用](#怎么用) · [覆盖范围](#覆盖范围) · [贡献与维护](#贡献与维护)

## 安装

使用支持 [Skills CLI](https://github.com/vercel-labs/skills) 的环境，在目标项目目录执行：

```bash
npx skills add Z131A634-Wesley/ai-design --skill ai-design
```

按安装器提示选择客户端。需要跨项目使用，可加 `-g`。也可手动下载仓库，把整个 `ai-design` 目录放进客户端的 Skills 目录；不要只复制 [入口文件](SKILL.md)，它会按需读取相邻的手册和模板。

## 怎么用

在支持 Skills 的智能体里点名 `ai-design`，交代三件事：**做哪个平台、解决什么问题、要什么交付物**。如果只要评审，说明不改代码；如果要比较方向，明确要求先给方案、等你确认后再实现。需求清楚且允许直接做时，不必多等一轮。

1. **判断场景。** 读取项目已有界面、组件和设计规则；只问会改变方案的关键问题，再加载对应手册。
2. **确定方向。** 新设计或高保真任务会考虑构图、排版、素材和关键状态。已有参考可以直接用；缺少依据时按需查案例，不强制联网，也不会临时下载并运行其他 Skill。
3. **按要求交付。** 做线框、可点原型、高保真稿、生产界面或评审意见。局部修改沿用现有规则，不另建一套设计系统。
4. **用证据验收。** 有渲染环境时看实际画面、复查关键操作；浏览器模拟不等于真机验证，没验证的项目会明确标注。

详细规则见 [Skill 入口](SKILL.md)、[视觉设计方法](references/visual-craft.md) 和 [质量闸门](references/quality-gates.md)。

## 覆盖范围

| 场景 | 能做什么 |
|---|---|
| [官网、落地页、作品集](references/section-playbook.md) | 首屏构图、排版与素材选择、页面节奏、转化路径 |
| [登录、注册、找回密码](references/account-flows.md) | 表单层级、验证提示、失败恢复和返回流程 |
| [后台与 SaaS](references/product-ui.md)、[数据可视化](references/data-viz.md) | 列表、详情、筛选、表格、图表与信息密度 |
| [iOS、Android、小程序、H5](references/mobile-ui.md) | 按平台选择导航、返回行为、安全区和设备适配 |
| [引导、预约、结账、长表单](references/task-flows.md) | 分步骤、确认、返回保留和失败恢复 |
| [线框与可点击原型](references/prototyping.md)、[设计系统](references/design-md-schema.md) | 梳理任务流和保真度，整理可跨页面复用的视觉规则 |

覆盖范围指**设计指导**，不是内置各平台的运行环境。原型用模拟数据；生产实现及验证仍取决于项目技术栈、工具和权限。

## 贡献与维护

欢迎通过 [Issues](https://github.com/Z131A634-Wesley/ai-design/issues) 提交建议。反馈时请写清平台、场景、期望交付物，以及具体哪条设计规则没解决问题；附图前请去除真实凭据和个人数据。

更新手册时注明来源与适用条件，检查入口和相对链接，并复验受影响的路径。建议每月抽查上游链接与移动平台规范；不把未经渲染或真机验证的结果标成通过。

## 致谢

借鉴了 [Refero](https://doc.refero.design/skill/overview.md) 的取材方法、[Anthropic Frontend Design](https://github.com/anthropics/skills/tree/main/skills/frontend-design) 的视觉判断、[Impeccable](https://impeccable.style/docs/new-work/) 的方向选择与复审，以及 [Taste Skill](https://github.com/Leonxlnx/taste-skill) 的内容与渲染检查。完整出处及用法见 [来源地图](references/source-map.md)。本项目与上述项目无官方隶属关系。

## 许可

本项目采用 [MIT 许可证](LICENSE)。链接到的第三方内容及素材仍遵循各自许可，不受本项目许可证重新授权。
