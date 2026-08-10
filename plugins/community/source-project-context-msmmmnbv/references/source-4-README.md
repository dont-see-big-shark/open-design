# ui_kits/app —— 应用化界面套件

Caduceus「Liquid Glass」设计系统的**应用化组件参考**，组件形状与行为从源原型提取，可直接复制到新项目。

## Structure

| 页面 | 内容 | Source basis（源依据） |
|---|---|---|
| `index.html` | 套件总览 + 导航 + 铁律摘要 | `index.html`（三端总览语义） |
| `console.html` | ConsoleHeader、用户/助手气泡、slate 长文、代码块、工具卡审批（**可体验流式模拟 + rim light + 中断**）、Composer、PTY 块、错误块、空状态 | `desktop.html` / `mobile-ios.html` 的 transcript + composer + tool-card |
| `panels.html` | Agents / Memory / Shared / Skills / Jobs / Processes / Projects 的 panel-row、搜索框、GlassSwitch（可切换）、进度条、tag | `desktop.html` 的 `PANEL_ORDER` 面板群与 panel 模板 |
| `connect.html` | 连接表单、mDNS 发现行、403 诊断块（mono 修复命令）、profile radio（可切换）、Settings 降级材质开关（**即时生效**） | `desktop.html` / `mobile-*.html` 的 connect/settings 视图 |
| `glass.html` | thin / regular / thick 三档玻璃、slate 实底、平铺 tint、选中态、降级材质对比（可切换） | `desktop.html` 的 glass / slate / degraded 规则 |

所有页面 `<link>` 引入 `../../colors_and_type.css`，自包含、可独立打开（本套件平铺在 `ui_kits/app/` 根，未另建 `components/` 子目录；每个页面即一个组件族）。

## Usage

1. **Copy** `../../colors_and_type.css` 到目标项目（或内联其 `:root`），作为唯一色彩/字体来源。
2. **Copy** 本套件页面的目标组件 HTML/CSS 片段，**import** 到新页面。
3. **Use** `DESIGN.md` §7 绑定状态与动效：Standard 200ms / Emphasized 320ms / Exit 160ms；Ambient 2.4s 可关闭。
4. **Build** 完成后按 `SKILL.md` 校验清单自查，再交付。

## Design Notes

- 组件术语对齐源原型：Sidebar（会话侧栏）、MessageBubble（用户气泡）、assist-body（助手长文块）、Composer（输入区）、tool-card（工具审批卡）。
- 色彩与字体遵循 `colors_and_type.css` 的 tokens；typography 规范见 `DESIGN.md` §3。
- **每屏一个 primary**：`.btn-primary`（brass 渐变 + `--btn-ink`）每屏至多一个，其余用 `.btn-secondary` / 文字链且文案不重复。
- **长文只在 slate**：Transcript/长回答放 `.assist-body`（`--surface` 实底）；代码/PTY 用 `--code-bg`。
- **玻璃规则**：层级 = 厚度；不嵌套；同屏 ≤2 层模糊；选中态 = 玻璃变厚；`body.degraded` 一键降级为实心 slate。
- **状态色即语义**：jade=online/完成、azure=run/rim、coral=error；`.dot.pulse` 2.4s 呼吸（尊重 `prefers-reduced-motion`）。
- 机器内容（模型 id/地址/路径/耗时）一律 `.mono`；示例数据已标注，不伪造度量。

## 与 preview/ 的关系

`preview/components-buttons.html`（组件抽查）、`preview/components-surfaces.html`（内嵌源原型）提供评审视角；本套件提供可直接抄用的实现。
