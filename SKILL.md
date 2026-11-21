---
name: ai-design
description: 前端 UI 设计、实现与视觉评审。用于官网、SaaS 后台、Web App、Dashboard、H5 和移动端的方案、原型、按稿开发与设计系统维护。Use for visual UI work. Excludes backend-only and non-visual changes.
license: MIT
---

# AI Design

## 先判断这次需要做什么

- **评审、线框、方案**：按请求的交付物结束，例如「评审登录页」交证据和建议，「画结账线框」交页面与状态。可点击原型仅按需制作。
- **已有项目的明确局部修改**：先看现有页面、主题和组件，再按既有样式实现，例如「把筛选按钮间距调成项目标准」。新增页面也继承设计系统，明确改版时再定新方向。
- **新页面、新流程或改版**：执行下列四步。仅做调研、方案或草图时留在设计阶段。

## 1. 确认需求与风格

读已有材料；合并问最多三个会改变方案的问题。优先确认场景与主任务、目标屏幕和交付物、视觉偏好或参考。已经明确的条件直接采用。按 [场景选型](references/scenario-routing.md) 定布局、状态和平台约束。

新视觉、改版、高保真实现与视觉打磨按 [外部设计 Skill 调用](references/external-design.md) 选一个主 Skill，必要时加一个专项。优先打开用户参考和已有界面；方向开放或缺少视觉依据时，主动找 **1–2 个真实外部案例**，说明本项目借鉴的决定。已有完整方向时直接给方案。

## 2. 提交 Design Spec 并等待确认

用 [Design Spec 模板](templates/design-spec.template.md) 提交一套方案，复杂页面标出用来校准的代表区域。**确认前可读取项目和参考、出草图及规格；用户确认后才写产品代码、搭建项目或改依赖。** 外部 Skill 也遵循当前阶段。若用户已提交并明确批准同范围的可实施规格，直接继承。

## 3. 按已确认的规格开发

按确认的规格实施，沿用已选主 Skill 与项目框架、组件和 token。复杂页面先实现代表区域，核对后再扩展。按需读 [前端实现](references/frontend-eng.md) 和 [动效与材质](references/effects.md)。跨页共享排版、形状、材质与状态规则。中途变更先更新规格；用户明确给出新决定并要求实施时视为确认，其余会影响视觉或范围的决定先提交确认。

## 4. 对照规格验收

用 [验收手册](references/quality-gates.md) 打开实际渲染，核对色彩、字阶、栅格、组件、宽窄屏及关键交互；修正具体偏差后复看。把实现偏差和设计判断分开。无法运行时明确未验证。

### 按需读取场景手册

| 条件 | 手册 |
|---|---|
| 官网、落地页、作品集 | [营销构图](references/section-playbook.md) |
| 企业后台、SaaS、列表管理 | [业务界面](references/product-ui.md) |
| Web App、工具、编辑器 | [工具工作区](references/workspace-ui.md) |
| Dashboard、数据报告或图表 | [看板与图表](references/data-viz.md)；需要处置、筛选或批量操作时加 [业务界面](references/product-ui.md) |
| 登录、注册、找回 | [账户流程](references/account-flows.md) |
| H5、原生移动端、小程序 | [移动平台](references/mobile-ui.md) |
| 预约、结账、多步表单 | [多步任务](references/task-flows.md) |
| 线框、可点击原型 | [原型](references/prototyping.md) |
| 维护设计系统、跨页 token 与组件规范 | [项目主规范](references/design-md-schema.md) |
| 新做或打磨按钮、表单、卡片、弹层等组件的可视样式 | [组件细节](references/visual-details.md)，选一个主控件和一个实际相邻边缘核对 |
| 有视觉难点或需审美评审 | [视觉诊断](references/visual-craft.md) |
