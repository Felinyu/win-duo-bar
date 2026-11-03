# Win Duo Bar

[![Windhawk](https://img.shields.io/badge/Windhawk-mod-7c3aed)](https://windhawk.net/)
[![License: GPL-3.0](https://img.shields.io/badge/license-GPL--3.0-blue)](LICENSE)
[![Platform: Windows 11](https://img.shields.io/badge/platform-Windows%2011-0078d4)](#compatibility--兼容性)

Source: https://github.com/Felinyu/win-duo-bar

> Status: the mod is **not in the official Windhawk catalog yet** — the submission is in review ([PR #6884](https://github.com/ramensoftware/windhawk-mods/pull/6884)). Until it is merged, install it manually as described below.

<p align="center">
  <img src="screenshots/hero.png" width="360" alt="Win Duo Bar - charging state">
</p>

A compact ring widget for the Windows 11 taskbar clock: a battery gauge ring,
a Wi-Fi symbol and the time/date as two rows of four bold digits, with a
smooth charging animation. Every visual parameter can be tuned from the
settings page, which is localized (English / Simplified Chinese). One widget is
created for every taskbar clock, so multi-monitor setups keep a clock on every
taskbar.

一个替换 Windows 11 通知区域时钟的圆环小组件：电量圆环 + Wi-Fi 图标 + 两行四位
的时间/日期数字，带平滑的充电动画。所有视觉参数都能在设置里调整（设置项已本地化，
英文/简体中文）。每个任务栏时钟都会创建独立的小组件，多显示器任务栏都能显示。

This mod replaces the clock only. To hide the system battery and network tray
icons, which the widget makes redundant, use the
[Taskbar tray system icon tweaks](https://github.com/ramensoftware/windhawk-mods/blob/master/mods/taskbar-tray-system-icon-tweaks.wh.cpp)
mod instead.
本模组只替换时钟。如需隐藏系统托盘的电量和网络图标，请使用
[Taskbar tray system icon tweaks](https://github.com/ramensoftware/windhawk-mods/blob/master/mods/taskbar-tray-system-icon-tweaks.wh.cpp)
模组。

## Features / 功能

**English**

- **Battery ring** – 263° gauge with round caps and a translucent track. The
  filled part follows the battery level. Green while plugged in, red when the
  battery is low (≤20%), yellow in battery saver mode, otherwise the taskbar
  text colour.
- **Wi-Fi symbol** – two thick rounded arcs plus a solid dot (geometry traced
  from the original 09 icon). It switches to the wired/VPN icon when the active
  connection is not wireless and dims when offline.
- **Time and date** – two rows of four bold digits, e.g. `1427` = 14:27 and
  `1102` = November 2nd, no separators.
- **Charging animation** – the top notch opens, a white lightning bolt grows
  out of the ring, the Wi-Fi symbol slides down slightly and the colours
  cross-fade (≈0.5 s at 60 fps).
- **One widget per taskbar** – every taskbar clock (primary and secondary) gets
  its own widget, and all of them are restored when the mod is disabled.
- **Fully adjustable** – ring diameter/thickness/gauge span/track opacity/
  notch angle/bolt size, Wi-Fi size/thickness/opening/position, digits size
  and row positions, letter spacing. DIP values are relative to the default
  38 DIP widget and scale with the "Widget size" setting.
- **Lightweight** – the network state follows the system's
  `NetworkStatusChanged` event instead of polling, so no out-of-process calls
  run on the taskbar UI thread every second.

**中文**

- **电量圆环**：263° 圆环，圆头、带半透明轨道，填充部分随电量变化。插电时绿色、
  低电量（≤20%）红色、节电模式黄色，其他情况跟随任务栏文字颜色。
- **Wi-Fi 图标**：两条粗圆头弧线 + 实心圆点（按原版 09 图标几何描出）；当前连接
  不是无线时显示有线/VPN 图标，断网时变暗。
- **时间日期**：两行四位粗体数字，例如 `1427` = 14:27、`1102` = 11月2日，
  不带分隔符。
- **充电动画**：顶部张开豁口、白色闪电长出、Wi-Fi 图标轻微下移、颜色渐变
  （约 0.5 秒，60fps）。
- **每个任务栏一个小组件**：主任务栏和副任务栏的每个时钟都有独立的小组件，
  禁用 mod 时会全部恢复。
- **全部可调**：圆环外径/粗细/弧度范围/轨道透明度/豁口角度/闪电大小，Wi-Fi 尺寸/
  粗细/开口/位置，数字字号/两行位置/字间距。DIP 参数以默认 38 DIP 为基准，
  随「小组件尺寸」缩放。
- **轻量**：网络状态通过系统 `NetworkStatusChanged` 事件更新，不再轮询，
  任务栏 UI 线程上没有每秒一次的跨进程调用。

## Screenshots / 截图

| | |
|---|---|
| ![states](screenshots/states.png) | ![strip](screenshots/strip.png) |
| 各种状态：普通 / 充电 / 低电量 / 节电 / 断网 / 有线 | 任务栏中的效果（示意图） |

The screenshots are rendered by `preview/preview.html` from the same geometry
parameters as the widget (scaled up for readability). 截图由 `preview/preview.html`
按 widget 相同的几何参数放大渲染，不是任务栏截屏。

## Installation / 安装

> The mod is not in the official Windhawk repository yet (submission pending), so
> install it manually for now. / 尚未上架 Windhawk 官方仓库（已提交审核），先手动安装。

**English**

1. Install [Windhawk](https://windhawk.net/).
2. Open Windhawk → **Mods** → the **"..."** menu → **Create a New Mod**
   (enable development mode if prompted).
3. Use `Win Duo Bar` as the name and `win-duo-bar` as the mod identifier.
4. Replace the generated source with the complete contents of
   [`win-duo-bar.wh.cpp`](win-duo-bar.wh.cpp) and click **Compile**.
5. When compilation succeeds, install and enable the mod, then restart
   Explorer (the taskbar will blink once).

**中文**

1. 安装 [Windhawk](https://windhawk.net/)。
2. 打开 Windhawk → **Mods** → 右上角 **"..."** 菜单 → **Create a New Mod**
   （如提示需要开启开发模式，按提示开启）。
3. 名称填 `Win Duo Bar`，Mod identifier 填 `win-duo-bar`。
4. 用 [`win-duo-bar.wh.cpp`](win-duo-bar.wh.cpp) 的完整内容替换编辑器里的源码，
   点击 **Compile**。
5. 编译成功后安装并启用 mod，然后重启一次 Explorer（任务栏会闪一下）。

After installation the widget replaces the notification-area clock on every
taskbar. To get the normal clock back, turn the mod off in Windhawk.
安装后所有任务栏的时钟都由这个 mod 接管；在 Windhawk 中关闭 mod 即可恢复系统时钟。

Once [PR #6884](https://github.com/ramensoftware/windhawk-mods/pull/6884) is merged,
the mod will also be installable from the official catalog with one click.
PR 合并后，也可以从 Windhawk 官方目录一键安装。

## Settings / 设置

The settings are localized (English / Simplified Chinese) and every visual
parameter is adjustable. 设置项已本地化（英文/简体中文），所有视觉参数都可调。

| Group | Settings (default) |
| --- | --- |
| Widget / 小组件 | Size / 尺寸 (38 DIP), Time format / 时间格式, Date format / 日期格式, Show date row / 显示日期行 (on), Show network icon / 显示网络图标 (on) |
| Ring / 圆环 | Outer diameter / 外径 (35 DIP), Thickness / 粗细 (3.7 DIP), Arc span / 电量弧范围 (263°), Track opacity / 轨道透明度 (28%), Charging notch / 充电豁口 (48°), Bolt width-height / 闪电宽高 (7.2 × 9.1 DIP) |
| Wi-Fi | Height / 高度 (10.5 DIP), Width / 宽度 (14.5 DIP), Line thickness / 线条粗细 (2 DIP), Opening angle / 开口角度 (75°), Vertical position / 垂直位置 (41%), Drop while charging / 充电时下移量 (1.5 DIP) |
| Digits / 数字 | Font size / 字号 (7 DIP), Time row position / 时间行位置 (73%), Date row position / 日期行位置 (89.5%), Letter spacing / 字间距 (110) |

DIP values are relative to the default 38 DIP widget and scale with the widget
size. DIP 参数以默认 38 DIP 小组件为基准，并随小组件尺寸一起缩放。

## Compatibility / 兼容性

- Windows 11 only (tested on Windows 11 26H2, build 26300). / 仅支持 Windows 11
  （在 Windows 11 26H2 build 26300 上测试）。
- Requires Windhawk 1.6+ (development mode to install a local mod). / 需要
  Windhawk 1.6+（本地安装 mod 需开发模式）。
- Windows updates may change taskbar internals; if the widget disappears after an
  update, check for an updated version of this mod. / Windows 更新可能改动任务栏
  内部结构；如果更新后 widget 不显示，请检查是否有新版本。

## Credits / 致谢

- [Windhawk](https://windhawk.net/) by ramensoftware / m417z.
- The taskbar XAML access code (XamlRoot lookup, symbol hooks, running code on
  the taskbar thread) is derived from the Windhawk mods by
  [m417z](https://m417z.com/), licensed under GPLv3.
  任务栏 XAML 访问代码（XamlRoot 获取、符号挂钩、任务栏线程执行）派生自
  [m417z](https://m417z.com/) 的 Windhawk 模组（GPLv3）。
- The Wi-Fi symbol geometry is traced from a "09"-style Wi-Fi icon reference.
  Wi-Fi 图标几何按 09 风格参考图标描出。

## Changelog / 更新日志

See [CHANGELOG.md](CHANGELOG.md). / 见 [CHANGELOG.md](CHANGELOG.md)。

## License / 许可证

[GPLv3](LICENSE). Because this mod contains code derived from a GPLv3 mod, it is
licensed under GPLv3 as well. / 因为包含派生自 GPLv3 模组的代码，本项目同样使用
GPLv3 许可证。
