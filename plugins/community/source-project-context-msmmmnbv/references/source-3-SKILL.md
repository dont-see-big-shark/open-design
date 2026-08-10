---
name: caduceus-liquid-glass
description: 使用 Caduceus「Liquid Glass · 流光」设计系统生成或修改界面。深空暗色、三层玻璃（thin/regular/thick）、实心 slate 承载长文、单一 brass 黄铜实心按钮、极光三色仅做背景光与状态指示。命中产品语境：Hermes / Caduceus 客户端、会话控制台、工具审批、面板、连接配对、深色玻璃质感界面。
user-invocable: false
---

# Caduceus · Liquid Glass（流光）

## What is inside

- `colors_and_type.css` —— 可复用令牌与字体基础（源文件 `:root` 逐字提取）：基础色板、InkLevel 四档、brass 渐变、极光三色、三档玻璃、动效曲线。
- `DESIGN.md` —— 权威设计文档：色彩/字体/间距/布局/组件/动效/语气/反模式。
- `ui_kits/app/` —— 应用化组件套件：console（会话控制台）、panels（面板群）、connect（连接与诊断）、glass（玻璃层级），每个页面自包含可独立打开。
- `preview/` —— 评审预览卡（颜色/字体/间距/组件/应用表面/品牌资产），内嵌源原型与保留文件。
- `assets/` —— 品牌资产（应用图标、字标、极光、颗粒）与 12 枚线性图标；`fonts/README.md` 为字体接入说明。

## Source context

源自「Web Prototype」源项目（`284b9560-1b33-421f-a9f0-9a1d8e5ae64c`）：Caduceus —— Hermes Agent 原生跨端客户端（Flutter）。证据文件：`desktop.html`（PC 三栏工作台）、`mobile-ios.html`（iOS 抽屉 + 底部面板）、`mobile-android.html`（Android Material 语义）、`index.html`（三端总览）、`prototype-plan.md`（锁定版规划）。产品语义：数据面（chat/responses/sessions/jobs）+ 控制面（tui_gateway：工具审批、记忆编辑、PTY）同一模型；连接「不折腾」（mDNS 发现、QR、403 诊断）；会话状态在服务端；多后端 profile（Home/Work/VPS）。详见 `context/provenance.md`。

## When to use

- 为 Caduceus 或同类「深色玻璃 + 精密工具」界面生成/修改页面。
- 适用产物：web prototypes、product interfaces、高保真 mockups，以及生产环境下的深色工具 UI。
- 需要会话控制台、工具审批卡、面板群、连接/诊断、降级材质开关等组件时。
- 桌面=三栏工作台；移动端=会话即屏幕（抽屉 + 底部 sheet）；两端同 token 分壳。

## How to use

1. 将 `colors_and_type.css` 的 `:root` 令牌逐字复制进页面首个 `<style>`（或直接 `<link rel="stylesheet" href=".../colors_and_type.css">`），**禁止臆造新色**。
2. 绑定字体：展示字 `--font-display`（Instrument Serif，**全片 ≤3 处**）、正文 `--font-body`、机器内容 `--font-mono`（地址/token/模型 id/路径/耗时）。
3. 组件形状与交互从 `ui_kits/app/` 复制，按 `DESIGN.md` §6/§7 绑定状态与动效（200/320/160ms、stagger ≤8、Ambient 可关闭）。
4. 生成后对照下方校验清单自查。

## Design-system highlights

- **Colors（色彩）**：单 accent（brass）每屏 ≤2 次；极光三色仅背景光与指示器；状态色即语义（jade/azure/coral）。
- **Typography（字体）**：Serif 展示 ≤3 处、Sans 正文、Mono 机器内容；InkLevel 四档封顶。
- **Spacing / Layout**：4–56px 刻度；桌面三栏、移动抽屉 + sheet；移动端无横向滚动。
- **Interaction**：hover/focus 前景永不变淡；`:focus-visible` 焦点环用 accent；按压 scale .94。
- **玻璃层级 = 厚度**：thin（blur 18/sat 1.6，列表行）→ regular（blur 28/sat 1.8，侧栏/工具栏/输入框）→ thick（blur 40/sat 2.0，弹层/命令面板）；选中态 = 玻璃变厚，未选中行平铺 tint；玻璃永不嵌套、同屏 ≤2 层模糊。
- **长文只在 slate**：Transcript/长回答用 `--surface` 实底，玻璃永不承载正文。
- **每屏一个黄铜实心按钮**（`.btn-primary`，brass 渐变 + `--btn-ink`），其余为次级/幽灵/文字链且文案不重复。
- **状态色即语义**：jade=online/完成、azure=run/rim light、coral=error/danger；`.dot.pulse` 2.4s 环境呼吸（可关闭）。
- **InkLevel 四档**（100/70/50/34）封顶；hover/focus 前景永不变淡；`:focus-visible` 焦点环用 accent。
- **降级材质**：`body.degraded` 把全部玻璃换实心 slate + 1px 边缘、关闭极光/颗粒；尺寸/圆角/时长/曲线不变。
- 示例数据显式标注；不伪造度量；机器内容 mono；CJK 回退有序（Latin → CJK → 平台默认）。

## 校验清单（P0）

- [ ] 每屏 ≤1 个 `.btn-primary`；长文在 `.slate` 上
- [ ] 玻璃不嵌套、≤2 层模糊；未选中行非 GlassPanel
- [ ] hover/focus 前景不变淡；焦点环存在；对比度达标（正文 ≥4.5:1，大文本/图标 ≥3:1）
- [ ] 移动端 360/390/430px 无横向滚动；触控 iOS ≥44pt / Android ≥48dp
- [ ] 机器内容 mono；衬线 ≤3 处；示例数据已标注
- [ ] 不用 `scrollIntoView`；不热链外部图片
