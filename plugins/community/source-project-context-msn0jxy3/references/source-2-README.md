# Caduceus 设计系统 · Liquid Glass（流光）

> 从「Web Prototype」源项目（`284b9560-1b33-421f-a9f0-9a1d8e5ae64c`）提取的完整 Open Design 设计系统工作区。
> 设计系统 id：`user:web-prototype-design-system`。

## Product Overview

**Caduceus** 是 Hermes Agent 的原生跨端客户端（Flutter，连接自托管后端），定位「你真正看着的东西」。**Built** for developers who drive a self-hosted backend from laptop and phone: the client **provides** streaming conversations, tool approvals, runtime panels and multi-profile management, and **supports** desktop and mobile surfaces with the same token set. 核心能力：

- **会话控制台**：3000 token 流式长回答不卡、工具审批（批准/拒绝）、中断、错误诊断。
- **连接不折腾**：mDNS 发现、QR 配对、Tailscale 诊断，403 时直接给出修复命令。
- **面板群**：Agents / Memory / Shared Memory / Skills / Jobs / Processes / Projects / Settings。
- **多后端 profile**：Home / Work / VPS 一处管理、切换明确。
- **主表面**：桌面 = 三栏工作台；移动（iOS/Android）= 会话即屏幕（抽屉 + 底部 sheet）。两端同一套 token，仅壳层不同。

设计语言：**深空 · 极光 · 一处黄铜** —— voidBlack 底上三团极光漂移，三层玻璃只承载 chrome，长文永远在实心 slate 上，全界面只有一枚 brass 实心按钮。数据面（chat/responses/sessions/jobs）与控制面（tui_gateway：工具审批、记忆编辑、PTY）呈现为同一模型。

## Source Context

| 参考 | 位置 |
|---|---|
| 源项目交接说明（生成契约） | `context/source-context.md` |
| 提取记录与来源映射 | `context/provenance.md` |
| 源原型证据 | `desktop.html` · `mobile-ios.html` · `mobile-android.html` · `index.html` · `prototype-plan.md`（保留在根目录，未替换为 stub） |
| 权威设计文档 | `DESIGN.md` |
| 可复用令牌 | `colors_and_type.css` |

## Package Contents

```
colors_and_type.css   色彩与字体基础（源 :root 逐字 + 玻璃/焦点环/降级）
（preserved assets：以下为从源原型原样保留的品牌资产、font 接入说明与 component 套件）
  brand/              应用图标 caduceus-mark.svg · 字标 caduceus-logo.svg · 极光 aurora.svg · 颗粒 grain.svg
  icons/              12 枚 24px 线性 stroke 图标（menu/back/panel/gear/search/chat/user/wifi/alert/stop/close/send）
  README.md           资产清单与使用方式
fonts/README.md       Instrument Sans / Serif / IBM Plex Mono 接入说明（源未打包字体二进制，故无二进制）
ui_kits/app/          应用化界面套件：index（总览）· console · panels · connect · glass + README
preview/              评审预览卡（见下方 Preview Manifest）
```

## Preview Manifest

| 卡片 | 文件 | 看什么 |
|---|---|---|
| 预览总览 | `preview/index.html` | 全部卡片入口与包结构 |
| 色彩令牌 | `preview/colors-primary.html` | 基础表面、brass 渐变、语义色、InkLevel（加载 colors_and_type.css） |
| 字体标本 | `preview/typography-specimens.html` | Serif / Sans / Mono 三族与四档墨阶 |
| 间距·圆角·阴影 | `preview/spacing-tokens.html` | 间距刻度、圆角、三档玻璃、Motion |
| 组件形态 | `preview/components-buttons.html` | 按钮/开关/状态点/会话行/工具卡/面板行/进度（可交互） |
| 应用表面 | `preview/components-surfaces.html` | 内嵌保留的 desktop / mobile-ios / mobile-android 源原型 + ui_kits/app |
| 品牌资产 | `preview/brand-assets.html` | 加载 assets/brand + assets/icons 保留文件 |

## Reuse Workflow

1. 复制 `colors_and_type.css` 到新项目，绑定 `:root` 令牌（源值逐字，勿臆造）。
2. 组件形状从 `ui_kits/app/` 复制；状态与动效按 `DESIGN.md` §6/§7。
3. 生成后对照 `SKILL.md` 的校验清单自查（每屏一个 primary、长文在 slate、玻璃不嵌套等）。
4. 评审时先看 `preview/index.html`，再按需深入各卡片。

## 评审顺序建议

1. `preview/colors-primary.html` —— 确认令牌与对比度；
2. `preview/typography-specimens.html` + `preview/spacing-tokens.html` —— 字体/间距基础；
3. `preview/components-buttons.html` —— 组件形态与状态；
4. `preview/components-surfaces.html` —— 三端源原型整体观感（最先看也可以）。

## 已知边界

- 源原型未打包字体二进制与运行时图标，`fonts/` 仅说明接入方式，未建 `build/`（详见 `context/provenance.md`「未保留项」）。
- 原型内所有数字/指标均为示例数据（源文件自带标注）。
