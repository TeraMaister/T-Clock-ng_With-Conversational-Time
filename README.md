T-Clock-ng With Conversational Time


==========

**T-Clock-ng** by [DukeCorp1996](https://dukecorp1996.x35.in/) is a fork of
[White-Tiger's T-Clock Redux](https://github.com/White-Tiger/T-Clock) (last released 2018) brought up to date for
**Windows 11**. All credit for T-Clock Redux goes to White-Tiger, and before them to Stoic Joker, Two_toNe and Kazubon.

* **Download:** [latest release](https://github.com/Balls0fSteel/T-Clock-ng/releases/latest)
* **Website:** [dukecorp1996.x35.in](https://dukecorp1996.x35.in/)
* **Support the development:** [donate](https://dukecorp1996.x35.in/donations.html)
* **Bugs and feature requests:** [issue tracker](https://github.com/Balls0fSteel/T-Clock-ng/issues)

---

---

## Purpose of adding Conversational Time into t-clock

**TL;DR:** This fork adds six conversational time formats to T-Clock-ng: Turkish, British English, and American English, each with an exact and an approximate (nearest-five-minute) variant. Inspired by dual-scale military watch dials, it aims to make the relationship between 24-hour digital time and everyday spoken time more intuitive through continuous exposure.

This fork started as a personal project.

Having grown up primarily using digital clocks, I became accustomed to reading time in the 24-hour format. However, when communicating with people who were more accustomed to traditional 12-hour expressions, especially people of my parents' generation who grew up reading time on analog clocks, I sometimes had to mentally convert between the two formats. Even though the conversion itself is simple, having to perform this mental calculation adds a small delay of a second or two when processing what someone says.

For example, when someone says **"quarter to six"**, I may need to mentally translate it into **17:45**. Similarly, when I see a football match advertised as starting at **19:00**, I instinctively understand the digital notation, even though someone using the traditional 12-hour system would more naturally express it as **"seven o'clock in the evening"**.

I wanted to bridge this gap by making my taskbar clock display time in a more conversational way, allowing me to become familiar with these expressions through everyday exposure.

Another inspiration was the dual-scale dial found on military-style field watches, such as certain Hamilton Khaki Field models. These dials display both the traditional 1–12 hour scale and the corresponding 13–24 military time scale. This design aims to reduce the mental effort and time needed to convert between the two systems, eliminating the need for mental arithmetic when reading the time.

Inspired by this idea, I wanted to bring a similar concept to the digital Windows taskbar clock: preserving the familiar 24-hour digital display while also showing how the same time is naturally expressed in everyday speech.

The goal of this fork is to help users gradually internalize both 12-hour and 24-hour time representations, as well as the natural expressions people use when talking about time in everyday life. By displaying conversational time alongside the familiar digital clock, users can repeatedly associate numerical times with their spoken equivalents. Over time, this familiarity can make both time conversion and the recognition of spoken time expressions more instinctive, reducing the need for conscious mental calculations.

This fork extends [T-Clock-ng](https://github.com/Balls0fSteel/T-Clock-ng) with six conversational time formats:

- **TRTIME:** Turkish conversational time.
- **APPROXTRTIME:** Turkish conversational time, rounded to the nearest five minutes.
- **UKENTIME:** British English conversational time.
- **APPROXUKENTIME:** British English conversational time, rounded to the nearest five minutes.
- **USENTIME:** American English conversational time.
- **APPROXUSENTIME:** American English conversational time, rounded to the nearest five minutes.

For compatibility, **ENTIME** remains an alias for **UKENTIME**, and **APPROXENTIME** remains an alias for **APPROXUKENTIME**.

All original T-Clock-ng functionality and Windows 11 compatibility improvements are retained. This fork focuses on conversational time formatting while keeping the upstream project's development and original features intact.

---

## Türkçe gündelik saat biçimleri

Bu fork, T-Clock-ng'nin **Clock Text → Format** alanına doğrudan yazılabilen altı gündelik saat biçimi belirteci ekler. Belirteçleri büyük harfle ve **yüzde işareti olmadan** kullanın. Tek başlarına kullanılabildikleri gibi sabit metinlerle ve diğer T-Clock biçim belirteçleriyle birleştirilebilirler.

| Belirteç | Dil / biçim | Hassasiyet |
|---|---|---|
| `TRTIME` | Türkçe | Dakikayı aynen korur |
| `APPROXTRTIME` | Türkçe | En yakın beş dakikaya yuvarlar |
| `UKENTIME` | Britanya İngilizcesi | Dakikayı aynen korur |
| `APPROXUKENTIME` | Britanya İngilizcesi | En yakın beş dakikaya yuvarlar |
| `USENTIME` | Amerikan İngilizcesi | Dakikayı aynen korur |
| `APPROXUSENTIME` | Amerikan İngilizcesi | En yakın beş dakikaya yuvarlar |
| `ENTIME` | `UKENTIME` takma adı | Dakikayı aynen korur |
| `APPROXENTIME` | `APPROXUKENTIME` takma adı | En yakın beş dakikaya yuvarlar |

### Türkçe örnekler

| Gerçek saat | `TRTIME` | `APPROXTRTIME` |
|---|---|---|
| 13:07 | öğleden sonra biri yedi geçiyor | öğleden sonra biri beş geçiyor |
| 13:17 | öğleden sonra biri on yedi geçiyor | öğleden sonra biri çeyrek geçiyor |
| 13:28 | öğleden sonra biri yirmi sekiz geçiyor | öğleden sonra bir buçuk |
| 13:43 | öğleden sonra ikiye on yedi var | öğleden sonra ikiye çeyrek var |
| 20:30 | akşam sekiz buçuk | akşam sekiz buçuk |

`TRTIME` dakikayı aynen korur. `APPROXTRTIME` önce saati en yakın beş dakikaya yuvarlar; örneğin 13:17, 13:15 olarak gösterilir. Türkçe biçimde tam saatlerde yalnızca saat adı, :30'da `buçuk`, :30'dan önce `geçiyor`, :30'dan sonra ise sonraki saate kalan süreyle `var` kullanılır. Gün bölümleri yaklaşık varsayılanlardır: gece, sabah, öğlen, öğleden sonra ve akşam.

### İngilizce örnekler

| Gerçek saat | `USENTIME` | `UKENTIME` |
|---|---|---|
| 13:05 | five after one in the afternoon | five past one in the afternoon |
| 13:07 | seven minutes after one in the afternoon | seven minutes past one in the afternoon |
| 13:15 | quarter after one in the afternoon | quarter past one in the afternoon |
| 13:30 | half past one in the afternoon | half past one in the afternoon |
| 13:45 | quarter till two in the afternoon | quarter to two in the afternoon |
| 13:55 | five till two in the afternoon | five to two in the afternoon |

Amerikan biçimi **after / till**, Britanya biçimi ise **past / to** ifadelerini kullanır. Her ikisinde de tam saatlerde `o'clock`, tam 12:00'da `noon`, tam 00:00'da `midnight` kullanılır. Beşin katı olmayan dakika değerlerinde `minute` veya `minutes` sözcüğü eklenir; beş dakikalık aralıklarda eklenmez. Gün bölümleri yaklaşık varsayılanlardır: `in the morning`, `in the afternoon`, `in the evening` ve `at night`.

Yaklaşık belirteçler biçimlendirmeden önce dakikayı en yakın beş dakikaya yuvarlar. Yuvarlama bir sonraki saate geçebilir.


**Katkı:** Gündelik saat biçimi belirteçlerinin uygulanması ve Windows x86/x64 GitHub Actions derleme yapılandırması, bu forkun bakımını üstlenen **TeraMaister** ile iş birliği içinde **ChatGPT (OpenAI)** yardımıyla hazırlanmıştır.

---

---

## Windows 11 Compatibility

First of all, special thanks to [DukeCorp1996](https://dukecorp1996.x35.in/), the developer of [T-Clock-ng](https://github.com/Balls0fSteel/T-Clock-ng), for continuing the development of T-Clock Redux and bringing it up to date with modern Windows versions, current development tools, and ongoing improvements.

If you appreciate their work and would like to support the continued development of T-Clock-ng, consider making a donation through their [official donation page](https://dukecorp1996.x35.in/donations.html).

T-Clock-ng introduces an overlay clock for the redesigned Windows 11 taskbar. Since Windows 11 uses a XAML-based taskbar without the classic clock window used by older versions of T-Clock, this approach allows T-Clock-ng to display its own clock over the native clock area while preserving its calendar interaction.

According to the developer's [project roadmap](https://github.com/Balls0fSteel/T-Clock-ng/blob/master/PLAN.md), the overlay can become wider than the original clock area and overlap neighboring system tray icons when using longer clock formats. The suggested workaround is to use a shorter clock format and reduce the default padding.

I will keep an eye on the developer's ongoing work and look forward to seeing what new features and improvements they bring in future releases.

---

## Recommended Third-Party Tools for restoring traditional Windows interface

Personally, I prefer the traditional Windows interface and would rather not spend time tweaking or working around the redesigned Windows 11 taskbar, Start menu, and context menus. If you feel the same way, or simply want more control over your desktop, consider the following tools.

I recommend these tools to users of **all T-Clock versions and forks**, not just T-Clock-ng.

| Tool | Purpose | License / Pricing |
|---|---|---|
| [ExplorerPatcher](https://github.com/valinet/ExplorerPatcher) | Restores and customizes classic Windows taskbar behavior, Start menu, and system tray. | Free · Open Source · GPL-2.0 |
| [Open-Shell](https://github.com/Open-Shell/Open-Shell-Menu) | Provides a classic Start menu and additional File Explorer features. | Free · Open Source · MIT |
| [StartAllBack](https://www.startallback.com/) | Provides extensive Windows 11 taskbar, Start menu, system tray, and File Explorer customization. | Paid · Proprietary · Trial available |

These tools are entirely optional. Everyone has their own preferences, workflow, and idea of how their Windows desktop should look and behave. Feel free to use whichever tools suit your needs, combine them, customize your setup, or simply stick with the default Windows interface. There is no single setup that works best for everyone.
T-Clock-ng With Conversational Time


==========
[![build](https://github.com/Balls0fSteel/T-Clock-ng/actions/workflows/build.yml/badge.svg)](https://github.com/Balls0fSteel/T-Clock-ng/actions/workflows/build.yml)

**T-Clock-ng** by [DukeCorp1996](https://dukecorp1996.x35.in/) is a fork of
[White-Tiger's T-Clock Redux](https://github.com/White-Tiger/T-Clock) (last released 2018) brought up to date for
**Windows 11**. All credit for T-Clock Redux goes to White-Tiger, and before them to Stoic Joker, Two_toNe and Kazubon.

* **Download:** [latest release](https://github.com/Balls0fSteel/T-Clock-ng/releases/latest)
* **Website:** [dukecorp1996.x35.in](https://dukecorp1996.x35.in/)
* **Support the development:** [donate](https://dukecorp1996.x35.in/donations.html)
* **Bugs and feature requests:** [issue tracker](https://github.com/Balls0fSteel/T-Clock-ng/issues)

---

---

## Purpose

**TL;DR:** This fork adds six conversational time formats to T-Clock-ng: Turkish, British English, and American English, each with an exact and an approximate (nearest-five-minute) variant. Inspired by dual-scale military watch dials, it aims to make the relationship between 24-hour digital time and everyday spoken time more intuitive through continuous exposure.

This fork started as a personal project.

Having grown up primarily using digital clocks, I became accustomed to reading time in the 24-hour format. However, when communicating with people who were more accustomed to traditional 12-hour expressions, especially people of my parents' generation who grew up reading time on analog clocks, I sometimes had to mentally convert between the two formats. Even though the conversion itself is simple, having to perform this mental calculation adds a small delay of a second or two when processing what someone says.

For example, when someone says **"quarter to six"**, I may need to mentally translate it into **17:45**. Similarly, when I see a football match advertised as starting at **19:00**, I instinctively understand the digital notation, even though someone using the traditional 12-hour system would more naturally express it as **"seven o'clock in the evening"**.

I wanted to bridge this gap by making my taskbar clock display time in a more conversational way, allowing me to become familiar with these expressions through everyday exposure.

Another inspiration was the dual-scale dial found on military-style field watches, such as certain Hamilton Khaki Field models. These dials display both the traditional 1–12 hour scale and the corresponding 13–24 military time scale. This design aims to reduce the mental effort and time needed to convert between the two systems, eliminating the need for mental arithmetic when reading the time.

Inspired by this idea, I wanted to bring a similar concept to the digital Windows taskbar clock: preserving the familiar 24-hour digital display while also showing how the same time is naturally expressed in everyday speech.

The goal of this fork is to help users gradually internalize both 12-hour and 24-hour time representations, as well as the natural expressions people use when talking about time in everyday life. By displaying conversational time alongside the familiar digital clock, users can repeatedly associate numerical times with their spoken equivalents. Over time, this familiarity can make both time conversion and the recognition of spoken time expressions more instinctive, reducing the need for conscious mental calculations.

This fork extends [T-Clock-ng](https://github.com/Balls0fSteel/T-Clock-ng) with six conversational time formats:

- **TRTIME:** Turkish conversational time.
- **APPROXTRTIME:** Turkish conversational time, rounded to the nearest five minutes.
- **UKENTIME:** British English conversational time.
- **APPROXUKENTIME:** British English conversational time, rounded to the nearest five minutes.
- **USENTIME:** American English conversational time.
- **APPROXUSENTIME:** American English conversational time, rounded to the nearest five minutes.

For compatibility, **ENTIME** remains an alias for **UKENTIME**, and **APPROXENTIME** remains an alias for **APPROXUKENTIME**.

All original T-Clock-ng functionality and Windows 11 compatibility improvements are retained. This fork focuses on conversational time formatting while keeping the upstream project's development and original features intact.

---

## Türkçe gündelik saat biçimleri

Bu fork, T-Clock-ng'nin **Clock Text → Format** alanına doğrudan yazılabilen altı gündelik saat biçimi belirteci ekler. Belirteçleri büyük harfle ve **yüzde işareti olmadan** kullanın. Tek başlarına kullanılabildikleri gibi sabit metinlerle ve diğer T-Clock biçim belirteçleriyle birleştirilebilirler.

| Belirteç | Dil / biçim | Hassasiyet |
|---|---|---|
| `TRTIME` | Türkçe | Dakikayı aynen korur |
| `APPROXTRTIME` | Türkçe | En yakın beş dakikaya yuvarlar |
| `UKENTIME` | Britanya İngilizcesi | Dakikayı aynen korur |
| `APPROXUKENTIME` | Britanya İngilizcesi | En yakın beş dakikaya yuvarlar |
| `USENTIME` | Amerikan İngilizcesi | Dakikayı aynen korur |
| `APPROXUSENTIME` | Amerikan İngilizcesi | En yakın beş dakikaya yuvarlar |
| `ENTIME` | `UKENTIME` takma adı | Dakikayı aynen korur |
| `APPROXENTIME` | `APPROXUKENTIME` takma adı | En yakın beş dakikaya yuvarlar |

### Türkçe örnekler

| Gerçek saat | `TRTIME` | `APPROXTRTIME` |
|---|---|---|
| 13:07 | öğleden sonra biri yedi geçiyor | öğleden sonra biri beş geçiyor |
| 13:17 | öğleden sonra biri on yedi geçiyor | öğleden sonra biri çeyrek geçiyor |
| 13:28 | öğleden sonra biri yirmi sekiz geçiyor | öğleden sonra bir buçuk |
| 13:43 | öğleden sonra ikiye on yedi var | öğleden sonra ikiye çeyrek var |
| 20:30 | akşam sekiz buçuk | akşam sekiz buçuk |

`TRTIME` dakikayı aynen korur. `APPROXTRTIME` önce saati en yakın beş dakikaya yuvarlar; örneğin 13:17, 13:15 olarak gösterilir. Türkçe biçimde tam saatlerde yalnızca saat adı, :30'da `buçuk`, :30'dan önce `geçiyor`, :30'dan sonra ise sonraki saate kalan süreyle `var` kullanılır. Gün bölümleri yaklaşık varsayılanlardır: gece, sabah, öğlen, öğleden sonra ve akşam.

### İngilizce örnekler

| Gerçek saat | `USENTIME` | `UKENTIME` |
|---|---|---|
| 13:05 | five after one in the afternoon | five past one in the afternoon |
| 13:07 | seven minutes after one in the afternoon | seven minutes past one in the afternoon |
| 13:15 | quarter after one in the afternoon | quarter past one in the afternoon |
| 13:30 | half past one in the afternoon | half past one in the afternoon |
| 13:45 | quarter till two in the afternoon | quarter to two in the afternoon |
| 13:55 | five till two in the afternoon | five to two in the afternoon |

Amerikan biçimi **after / till**, Britanya biçimi ise **past / to** ifadelerini kullanır. Her ikisinde de tam saatlerde `o'clock`, tam 12:00'da `noon`, tam 00:00'da `midnight` kullanılır. Beşin katı olmayan dakika değerlerinde `minute` veya `minutes` sözcüğü eklenir; beş dakikalık aralıklarda eklenmez. Gün bölümleri yaklaşık varsayılanlardır: `in the morning`, `in the afternoon`, `in the evening` ve `at night`.

Yaklaşık belirteçler biçimlendirmeden önce dakikayı en yakın beş dakikaya yuvarlar. Yuvarlama bir sonraki saate geçebilir.


**Katkı:** Gündelik saat biçimi belirteçlerinin uygulanması ve Windows x86/x64 GitHub Actions derleme yapılandırması, bu forkun bakımını üstlenen **TeraMaister** ile iş birliği içinde **ChatGPT (OpenAI)** yardımıyla hazırlanmıştır.

---

---

## Windows 11 Compatibility

First of all, special thanks to [DukeCorp1996](https://dukecorp1996.x35.in/), the developer of [T-Clock-ng](https://github.com/Balls0fSteel/T-Clock-ng), for continuing the development of T-Clock Redux and bringing it up to date with modern Windows versions, current development tools, and ongoing improvements.

If you appreciate their work and would like to support the continued development of T-Clock-ng, consider making a donation through their [official donation page](https://dukecorp1996.x35.in/donations.html).

T-Clock-ng introduces an overlay clock for the redesigned Windows 11 taskbar. Since Windows 11 uses a XAML-based taskbar without the classic clock window used by older versions of T-Clock, this approach allows T-Clock-ng to display its own clock over the native clock area while preserving its calendar interaction.

According to the developer's [project roadmap](https://github.com/Balls0fSteel/T-Clock-ng/blob/master/PLAN.md), the overlay can become wider than the original clock area and overlap neighboring system tray icons when using longer clock formats. The suggested workaround is to use a shorter clock format and reduce the default padding.

I will keep an eye on the developer's ongoing work and look forward to seeing what new features and improvements they bring in future releases.

---

## Recommended Third-Party Tools

Personally, I prefer the traditional Windows interface and would rather not spend time tweaking or working around the redesigned Windows 11 taskbar, Start menu, and context menus. If you feel the same way, or simply want more control over your desktop, consider the following tools.

I recommend these tools to users of **all T-Clock versions and forks**, not just T-Clock-ng.

| Tool | Purpose | License / Pricing |
|---|---|---|
| [ExplorerPatcher](https://github.com/valinet/ExplorerPatcher) | Restores and customizes classic Windows taskbar behavior, Start menu, and system tray. | Free · Open Source · GPL-2.0 |
| [Open-Shell](https://github.com/Open-Shell/Open-Shell-Menu) | Provides a classic Start menu and additional File Explorer features. | Free · Open Source · MIT |
| [StartAllBack](https://www.startallback.com/) | Provides extensive Windows 11 taskbar, Start menu, system tray, and File Explorer customization. | Paid · Proprietary · Trial available |

These tools are entirely optional. Everyone has their own preferences, workflow, and idea of how their Windows desktop should look and behave. Feel free to use whichever tools suit your needs, combine them, customize your setup, or simply stick with the default Windows interface. There is no single setup that works best for everyone.

---

What's new compared to T-Clock Redux:
* works with the stock Windows 11 taskbar (22H2/23H2/24H2), which no longer has the classic clock window T-Clock used to hook
* still works with classic taskbars (Windows 7–10, or Windows 11 with StartAllBack / ExplorerPatcher)
* builds with current Visual Studio (2017–2026) and MinGW-w64 GCC; GitHub Actions CI

See [CHANGELOG.md](CHANGELOG.md) for details and [PLAN.md](PLAN.md) for what's next.

### Windows 11 taskbar ("overlay clock")
Windows 11's taskbar is drawn with XAML; there is no clock window to take over. On Windows 11, when no classic clock
is found, T-Clock places its own clock window on top of the original clock, covering it with the taskbar's color.
Clicking it opens Windows' calendar as usual (or whatever you configured).

Settings (no UI yet) in the `[Taskbar]` section of `T-Clock.ini` (portable mode) or as DWORDs under
`HKCU\Software\Stoic Joker's\T-Clock 2010\Taskbar`:

| Setting | Default | Meaning |
|---|---|---|
| `Win11Overlay` | `0` | `0` = auto (overlay on Windows 11 without a classic clock), `1` = always, `-1` = never |
| `Win11OverlayPopup` | `0` | `1` = use a top-level popup instead of a child window of the taskbar |
| `Win11OverlayOffsetX` / `Win11OverlayOffsetY` | `0` | move the overlay by N pixels |

Keep Windows' own clock enabled; T-Clock locates and covers it. Set *Clock Text → Background* to override the
automatically sampled background color.

### Building
* **Visual Studio 2017 or newer** with "Desktop development with C++": run `src\compile.bat`
  (or open `src\~ide\msvc-vs.sln`). Output goes to `Release\`.
* **MinGW-w64 / GCC**: `src/compile.bat` (bash part) with `mingw32-make`, see `src/~ide/Makefile`.
* **Character encoding:** the conversational-time formatters contain Turkish UTF-8 text. The MSVC and MinGW compiler configurations explicitly select UTF-8 input encoding.

---

---

### Original T-Clock Redux readme
<sub>(by White-Tiger, kept for history; download and support links now point to T-Clock-ng)</sub>  
<sub>(click picture below for full size)</sub>
![clockshowcase](https://cloud.githubusercontent.com/assets/1467733/4608572/71b48156-5283-11e4-960f-b0415b5b7cec.png)  
**T-Clock Redux** is an enhanced fork of [Stoic Joker's T-Clock 2010](http://www.stoicjoker.com/TClock/)  
with ISO week number support, bug fixes and the ability to use Windows' default calendar and tooltips.

T-Clock *(called TClock)*, originally written by Kazubon in the early 90's, was a popular classic that was on the edge of extinction when Windows started going 64bit. ... Stoic Joker simply chose not to let that happen. And now it's up to us to continue their efforts.

If you don't mind to read lots of text, and want to know more about T-Clock and its history: [check this page out!](http://web.archive.org/web/20160202023839/http://greggdeselms.com/tclock.html) *(thanks Gregg)*


### Downloads *(binaries)*
* [![all releases](https://img.shields.io/badge/ALL-RELEASES-brightgreen.svg?logo=github&style=flat-square) ![](https://img.shields.io/github/downloads/Balls0fSteel/T-Clock-ng/total.svg?style=flat-square)](//github.com/Balls0fSteel/T-Clock-ng/releases)
* [![stable](https://img.shields.io/github/release/Balls0fSteel/T-Clock-ng.svg?label=STABLE&logo=github&style=flat-square) ![](https://img.shields.io/github/downloads/Balls0fSteel/T-Clock-ng/latest/total.svg?style=flat-square) ![](https://img.shields.io/github/release-date/Balls0fSteel/T-Clock-ng.svg?style=flat-square)](//github.com/Balls0fSteel/T-Clock-ng/releases/latest)
* Original T-Clock Redux releases (up to 2.4.4): [White-Tiger/T-Clock](//github.com/White-Tiger/T-Clock/releases)

#### Differences to Stoic Joker's T-Clock 2010 [Build 95/98](http://www.donationcoder.com/forum/index.php?topic=21944.0)
- [x] + supports Win10 with 1st-Anniversary update *(v2.4.1)*
- [x] + Unicode support *(v2.4.1)*
- [x] * improved file structure
- [x] + ISO-8601 week number support *(Wi)*
- [x] + original Windows calendar and tooltip usable
- [x] + support for clocks on every additional taskbar on Win8+
- [x] + system/user dependent default colors
- [x] + clock text angle freely adjustable
- [x] + live update of clock text related changes *(see what happens as you change it and before you apply it)*
- [x] + clock text always automatically centered
- [x] + right mouse click can be customized
- [x] + mouse button 4 and 5 supported
- [x] * improved taskbar support such as horizontal vs vertical and size
- [x] + calendar hides on 2nd click if opened before *(autohide must be enabled, Windows default behavior)*
- [x] + custom calendar can now show X past months, additional improvements
- [x] + extended right-click menu with more Windows like behavior  
*(hold down CTRL or SHIFT to get "Run ..." and "Exit Explorer" items)*
- [x] + simplified mouse click preferences page
- [x] + default configuration with Windows like behavior and clock with line-break on Vista+ *(easier for first-time users)*
- [x] + more mouse commands / customization
- [x] + overall improved settings dialog *(so many changes.. can't name them all)*
- [x] * improved Stopwatch *(hotkeys, export, stats)*
- [x] * improved drag&drop support
- [x] ! some bugfixes
- [x] * some minor and major rewrites and changes
- [x] ! can be compiled with MinGW/GCC *(allows more people to work on it and also fixed bugs)*
- [x] ! fixed clock text transparency issues on Vista+
- [x] + portable mode using .ini files as configuration storage *(v2.4.0)*
- [x] + inbuild update checker *(v2.4.0)*
- [ ] + enhanced time format editor incl. realtime preview *tbd*
- [ ] + ability to use different timezones on modifiers *tbd*
- [ ] + LClock formating options such as different fonts and positions for time and date *tbd*
- [ ] + working timezone identifiers *tbd*
- [ ] + multilingual version? *tbd*
- [ ] + resource usage % format option (CPU,RAM maybe GPU) *tbd*
- [ ] + improved time synchronization incl. autorun at startup (requires admin rights for "install") *tbd*
- [ ] + mouseover customization, for example different time format, color, border or even current weather *tbd*
- [ ] + switching clock text, eg. every 2 seconds another one *tbd*
- [ ] + multiple clock text presets? eg. switch between them on mouse click *tbd*
- [ ] + maybe current sun state picture as clock background (plugin) *tbd*
- [ ] + improved hotkey support *tbd*

### Requirements
* Windows 2000+ *(up to Windows 10 as of 2014; Windows 11 supported by T-Clock-ng)*

### What's that `_vc2010` build?
* As of 2018, all new releases will be build with GCC instead of the Visual C++ 2010 compiler.
  So the previously known `_static` builds are used instead and for compatibility reasons,
  `_vc2010` archives will still use the old compiler and are meant for advanced users.
* Requires: [Microsoft Visual C++ 2010 Redistributable](http://microsoft.com/en-us/download/details.aspx?id=26999) (install **both** 32bit `vcredist_x86` +  64bit `vcredist_x64` **on 64bit** OS)

### Support
* [Issue Tracker](//github.com/Balls0fSteel/T-Clock-ng/issues) *(also linked from T-Clock's About page)*
* [Website](https://dukecorp1996.x35.in/) and [donations](https://dukecorp1996.x35.in/donations.html)

### License
* GPLv2 ? *(license is currently unknown, needs further research)*
~~~~


---

---

---

## AI Use and Disclaimer

### Türkçe

> **DİKKAT: BU FORKTA YAPAY ZEKA KULLANILMIŞTIR.**

Bu projedeki bazı kod değişiklikleri ve dokümantasyon, ChatGPT (OpenAI) yardımıyla hazırlanmıştır.

**Kullanım ve sorumluluk:** Bu yazılımı kendi sorumluluğunuzda kullanırsınız. Yazılımın kullanımından, çalışmamasından, veri kaybından, sistem hatalarından veya doğabilecek diğer doğrudan ya da dolaylı zararlardan fork sahibi sorumlu tutulamaz. Yazılım herhangi bir garanti verilmeksizin, olduğu gibi sunulmaktadır. Kullanmadan önce kaynak kodunu incelemeniz ve önemli verilerinizi yedeklemeniz önerilir.

**Destek ve katkı talepleri:** Fork sahibi profesyonel bir yazılım geliştiricisi değildir ve kodlama bilgisi sınırlıdır. Hata düzeltme, yeni özellik ekleme, özel istekleri yerine getirme veya teknik destek sağlama taahhüdü yoktur. Talepler karşılanamayabilir ve bu fork için sunulan değişiklikler olduğu hâliyle kalabilir.

Bu fork, orijinal T-Clock Redux projesinden ayrı olarak, kişisel kullanım ve deneme amacıyla sürdürülmektedir.

### English

> **NOTICE: THIS FORK USES ARTIFICIAL INTELLIGENCE.**

Some code changes and documentation in this project were prepared with the assistance of ChatGPT (OpenAI).

**Use at your own risk:** You use this software at your own responsibility. The fork owner accepts no responsibility for damages arising from the use of this software, its failure to work, data loss, system errors, or any other direct or indirect consequences. The software is provided "AS IS", without any warranty. You are encouraged to review the source code and back up important data before using it.

**Support and contribution requests:** The fork owner is not a professional software developer and has limited programming knowledge. There is no commitment to fix bugs, add features, fulfill custom requests, or provide technical support. Requests may not be fulfilled, and the changes provided in this fork may remain as they are.

This fork is maintained separately from the original T-Clock Redux project for personal use and experimentation.

---

---

---

## AI Use and Disclaimer

### Türkçe

> **DİKKAT: BU FORKTA YAPAY ZEKA KULLANILMIŞTIR.**

Bu projedeki bazı kod değişiklikleri ve dokümantasyon, ChatGPT (OpenAI) yardımıyla hazırlanmıştır.

**Kullanım ve sorumluluk:** Bu yazılımı kendi sorumluluğunuzda kullanırsınız. Yazılımın kullanımından, çalışmamasından, veri kaybından, sistem hatalarından veya doğabilecek diğer doğrudan ya da dolaylı zararlardan fork sahibi sorumlu tutulamaz. Yazılım herhangi bir garanti verilmeksizin, olduğu gibi sunulmaktadır. Kullanmadan önce kaynak kodunu incelemeniz ve önemli verilerinizi yedeklemeniz önerilir.

**Destek ve katkı talepleri:** Fork sahibi profesyonel bir yazılım geliştiricisi değildir ve kodlama bilgisi sınırlıdır. Hata düzeltme, yeni özellik ekleme, özel istekleri yerine getirme veya teknik destek sağlama taahhüdü yoktur. Talepler karşılanamayabilir ve bu fork için sunulan değişiklikler olduğu hâliyle kalabilir.

Bu fork, orijinal T-Clock Redux projesinden ayrı olarak, kişisel kullanım ve deneme amacıyla sürdürülmektedir.

### English

> **NOTICE: THIS FORK USES ARTIFICIAL INTELLIGENCE.**

Some code changes and documentation in this project were prepared with the assistance of ChatGPT (OpenAI).

**Use at your own risk:** You use this software at your own responsibility. The fork owner accepts no responsibility for damages arising from the use of this software, its failure to work, data loss, system errors, or any other direct or indirect consequences. The software is provided "AS IS", without any warranty. You are encouraged to review the source code and back up important data before using it.

**Support and contribution requests:** The fork owner is not a professional software developer and has limited programming knowledge. There is no commitment to fix bugs, add features, fulfill custom requests, or provide technical support. Requests may not be fulfilled, and the changes provided in this fork may remain as they are.

This fork is maintained separately from the original T-Clock Redux project for personal use and experimentation.
