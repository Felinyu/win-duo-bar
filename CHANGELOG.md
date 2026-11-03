# Changelog

## 1.1.1

- Fix: the "Show the date row" setting is applied on settings changes again
  (it was only read when the widget was built).
- Restore the correct visibility when a leftover widget from a previous load is
  found (`WinDuoBarWidget` canvas): the native clock is treated as visible
  instead of keeping the leftover collapsed state.
- Start the widget when Explorer creates (or recreates) the taskbar, so it
  appears at login even if the optional clock hook isn't available; the clock
  that triggered the hook is now injected directly instead of only through the
  scan.
- 12/24-hour detection ignores quoted literals in `LOCALE_SSHORTTIME` (e.g.
  French (Canada) `HH 'h' mm`).
- README: link to the Taskbar tray system icon tweaks mod page instead of a
  `blob/master` URL; removed an unused include.

## 1.1.0

Addresses the review of the initial submission.

- Remove the tray icon tweaks copied from the "Taskbar tray system icon tweaks"
  mod: the hide volume/network/battery/microphone/location/Studio Effects/
  Recall/language bar/language supplementary icons/bell settings, the grayscale
  battery icon, the "Show desktop" button width override and the time/date
  hiding (`clockVisibility`) are gone. The mod is now only about the clock
  widget; the README points to the original mod for hiding the redundant tray
  icons.
- Remove the "Enable the Win Duo Bar widget" setting. Disabling the mod is the
  way to get the native clock back.
- Multi-monitor: keep one widget per taskbar clock instead of a single global
  widget. Each `SystemTray.DateTimeIconContent` gets its own canvas, host panel
  and saved visibility, and settings are applied to the primary and the
  secondary taskbars. All clocks are restored when the mod unloads.
- Teardown: the widget cleanup is now unconditional and always runs on the
  taskbar UI thread (`Wh_ModBeforeUninit` -> `ApplySettings` ->
  `StopWidgetUi`). `Wh_ModUninit` no longer touches XAML from the engine
  thread.
- Network: replace the 2 s out-of-process polling with a
  `NetworkInformation::NetworkStatusChanged` subscription that only sets a
  dirty flag, checked by the existing 1 s UI timer. The subscription is
  revoked on the UI thread during teardown.
- Localization: use Windhawk's localization syntax. English is the default and
  all names/descriptions/options have `:zh-CN` variants instead of inline
  bilingual strings.
- The widget size now scales the whole widget: ring diameter, stroke widths,
  bolt, Wi-Fi symbol and digits are proportional to the size.
- Desktop PCs without a battery no longer show the permanent charging state.
- 12/24-hour detection now reads `LOCALE_SSHORTTIME` instead of scanning the
  formatted time for "AM"/"PM".
- Use `WindhawkUtils::StringSetting` instead of manual
  `Wh_GetStringSetting`/`Wh_FreeStringSetting` pairs.
- Code fallback defaults now match the settings block (263° arc, 3.7 DIP ring
  thickness, 2 DIP Wi-Fi thickness, 75° opening, 7 DIP digits), and stale
  comments were fixed.
- Remove dead code: `DateFormatSetting::chinese`, unused XAML tree helpers, the
  unneeded `UpdateTheme` forward declaration, `BatteryInfo::charging` and
  `NetworkInfo::bars`.
- README: embed a screenshot from the repository.

## 1.0.0

First public release.

- Duo-style ring widget for the Windows 11 notification-area clock: battery
  gauge ring with translucent track, Wi-Fi symbol (09 icon geometry), two rows
  of four digits for time and date.
- Charging animation: top notch opens, lightning bolt grows out of the ring,
  Wi-Fi symbol slides down slightly, ring colours cross-fade.
- Fully adjustable geometry (ring, Wi-Fi, digits) from the settings page.
- Bilingual (English / Chinese) settings.
- Tray icon tweaks from the "Taskbar tray system icon tweaks" mod: hide volume,
  network, battery, microphone, location/GPS, Studio Effects, Recall, language
  bar, language supplementary icons and bell; grayscale battery icon; hide
  time/date when the widget is disabled; "Show desktop" button width.
- GPLv3, credited to m417z for the tray icon tweaks base.
