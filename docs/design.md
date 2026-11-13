# Design notes

How the report is designed and why. Every visual answers one question, and colour carries meaning, not decoration.

## 1. Design concept

Two directions were considered:

| | A. Dark glass executive | B. Light editorial (chosen) |
|---|---|---|
| Mood | Trading-desk, dramatic, high contrast | Investment-committee memo: calm, precise, print-like |
| Background | `#0B1220` with frosted panels `rgba(255,255,255,0.06)` | `#F1F5F9` canvas, white panels |
| Accent | Electric teal `#2DD4BF` | Aegean teal `#0E7C86` |
| Supporting | Amber `#FBBF24` | Burnt orange `#C2410C` (negative / cooling only) |
| Neutrals | `#E2E8F0` text, `#334155` lines | Ink `#0F1B2D`, slate `#475569`, muted `#94A3B8`, lines `#E2E8F0` |
| Fonts | Segoe UI Light numbers, Segoe UI Semibold titles | DIN for KPI numbers, Segoe UI Semibold titles, Segoe UI body |
| Corners and shadow | 16 px, glow | 12 px, soft shadow (blur 9 px, 15% ink, 3 px down) |

**Why B:** the report is read by fund partners on GitHub screenshots and laptops, often printed or pasted into a memo. A light page keeps tables readable, survives printing, and lets one accent colour do the talking. The dark direction only appears in the hover tooltip, where contrast with the page helps.

**Colour rules**

- Teal `#0E7C86` is the one accent: the leading sector, venture stages, target funds, rising momentum, the current page.
- Burnt orange `#C2410C` only means "worse": cooling momentum and negative change.
- Everything else is neutral grey `#B8C4CF`, so the accent stands out.
- Light teal `#B7DDE0` is for fills: heatmaps, sparkline areas and data bars.

## 2. Theme file

[`GreekDeepTech.Report/StaticResources/RegisteredResources/GreekDeepTech.json`](../GreekDeepTech.Report/StaticResources/RegisteredResources/GreekDeepTech.json) sets data colours, text classes (callout in DIN, titles in Segoe UI Semibold) and visual styles for every visual type used. Visual containers are transparent with no border, because the panels come from the page background. Charts have no gridlines or axis titles. Tables have a white header with a thin rule and zebra rows. The theme also covers slicers, buttons and dark tooltips. In Power BI Desktop: View > Themes > Browse for themes.

## 3. Page layouts

Canvas 1280 x 720. Grid: 24 px outer margin, 16 px gutter, 72 px header band, content starting at y = 88. Each page reads top to bottom: KPI strip, main insight, supporting detail. The tables below are generated from the report files, so they match the report exactly.

#### Overview (1280 x 720)

| Visual | x | y | w | h | Shows |
|---|---|---|---|---|---|
| Text box | 16 | 2 | 560 | 44 | Greek deep tech venture analytics |
| Page navigator | 592 | 18 | 584 | 36 | one button per visible page; teal = current page |
| Button | 1184 | 18 | 72 | 36 | Filters |
| KPI value / text card | 16 | 40 | 576 | 32 | Selection Summary |
| Text box (hidden until toggled) | 992 | 80 | 264 | 300 | Filters |
| SVG image (measure) | 778 | 110 | 50 | 50 | Backed Share Ring SVG |
| KPI value / text card | 34 | 114 | 172 | 46 | Companies |
| KPI value / text card | 242 | 114 | 108 | 46 | KPI Capital Value |
| KPI value / text card | 450 | 114 | 172 | 46 | Disclosed Rounds |
| KPI value / text card | 658 | 114 | 108 | 46 | Greek Fund Backed Companies |
| KPI value / text card | 866 | 114 | 108 | 46 | Momentum Score |
| KPI value / text card | 1074 | 114 | 172 | 46 | KPI Grants Value |
| SVG image (measure) | 346 | 118 | 66 | 38 | Capital Sparkline SVG |
| SVG image (measure) | 970 | 118 | 66 | 38 | Signals Sparkline SVG |
| Slicer (hidden until toggled) | 1004 | 120 | 240 | 56 | Map Status |
| KPI value / text card | 34 | 158 | 178 | 32 | KPI Companies Context |
| KPI value / text card | 242 | 158 | 178 | 32 | KPI Capital Context |
| KPI value / text card | 450 | 158 | 178 | 32 | KPI Rounds Context |
| KPI value / text card | 658 | 158 | 178 | 32 | KPI Backed Context |
| KPI value / text card | 866 | 158 | 178 | 32 | KPI Momentum Context |
| KPI value / text card | 1074 | 158 | 178 | 32 | KPI Grants Context |
| Slicer (hidden until toggled) | 1004 | 184 | 240 | 56 | Sector |
| Column chart | 32 | 216 | 584 | 252 | dynamic: [Title Capital by Year] |
| Bar chart | 648 | 216 | 600 | 252 | dynamic: [Title Capital by Sector] |
| Table (hidden until toggled) | 648 | 216 | 600 | 252 | dynamic: [Title Capital by Sector] |
| Button | 1112 | 220 | 64 | 24 | Chart |
| Button | 1180 | 220 | 64 | 24 | Table |
| Slicer (hidden until toggled) | 1004 | 248 | 240 | 56 | Fund |
| Button (hidden until toggled) | 1004 | 324 | 116 | 32 | Clear all |
| Button (hidden until toggled) | 1128 | 324 | 116 | 32 | Close |
| Table | 32 | 500 | 792 | 196 | Largest disclosed rounds |
| Bar chart | 856 | 500 | 392 | 196 | dynamic: [Title Stage] |

#### Sectors (1280 x 720)

| Visual | x | y | w | h | Shows |
|---|---|---|---|---|---|
| Text box | 16 | 2 | 560 | 44 | Sectors and stages |
| Page navigator | 592 | 18 | 664 | 36 | one button per visible page; teal = current page |
| KPI value / text card | 16 | 40 | 576 | 32 | Selection Summary |
| Slicer | 36 | 96 | 272 | 56 | Metric |
| Slicer | 348 | 96 | 272 | 56 | Breakdown |
| Slicer | 660 | 96 | 272 | 56 | Min Round Size (EUR M) |
| KPI value / text card | 970 | 116 | 90 | 38 | Rounds Above Threshold |
| KPI value / text card | 1060 | 126 | 190 | 26 | KPI Threshold Context |
| Bar chart | 32 | 184 | 584 | 256 | Any metric, any breakdown |
| Table | 648 | 184 | 600 | 256 | Which sectors punch above their weight? |
| Matrix | 32 | 472 | 584 | 224 | Time intelligence on any measure |
| Matrix | 648 | 472 | 600 | 224 | Where the companies sit |

#### Funds (1280 x 720)

| Visual | x | y | w | h | Shows |
|---|---|---|---|---|---|
| Text box | 16 | 2 | 560 | 44 | Fund lens |
| Page navigator | 592 | 18 | 664 | 36 | one button per visible page; teal = current page |
| KPI value / text card | 16 | 40 | 576 | 32 | Fund Lens Title |
| Slicer | 32 | 96 | 1216 | 48 | Fund Short |
| SVG image (measure) | 570 | 190 | 50 | 50 | Lead Share Ring SVG |
| KPI value / text card | 34 | 194 | 276 | 46 | Greek Fund Backed Companies |
| KPI value / text card | 346 | 194 | 212 | 46 | Lead Positions |
| KPI value / text card | 658 | 194 | 212 | 46 | KPI Capital Value |
| KPI value / text card | 970 | 194 | 276 | 46 | Co-invested Companies |
| SVG image (measure) | 866 | 198 | 66 | 38 | Capital Sparkline SVG |
| KPI value / text card | 34 | 238 | 282 | 32 | KPI Portfolio Context |
| KPI value / text card | 346 | 238 | 282 | 32 | KPI Lead Context |
| KPI value / text card | 658 | 238 | 282 | 32 | KPI Capital Context |
| KPI value / text card | 970 | 238 | 282 | 32 | KPI Co-invested Context |
| Bar chart | 32 | 296 | 464 | 216 | dynamic: [Title Fund Positions] |
| Matrix | 528 | 296 | 720 | 216 | dynamic: [Title Overlap] |
| Table | 32 | 544 | 1216 | 152 | Portfolio companies |

#### Momentum (1280 x 720)

| Visual | x | y | w | h | Shows |
|---|---|---|---|---|---|
| Text box | 16 | 2 | 560 | 44 | Momentum and signals |
| Page navigator | 592 | 18 | 664 | 36 | one button per visible page; teal = current page |
| KPI value / text card | 16 | 40 | 576 | 32 | As-Of Label |
| KPI value / text card | 242 | 114 | 156 | 46 | Momentum Score |
| KPI value / text card | 498 | 114 | 220 | 46 | Momentum Change |
| KPI value / text card | 754 | 114 | 220 | 46 | Active Companies |
| KPI value / text card | 1010 | 114 | 220 | 46 | Rising Companies |
| SVG image (measure) | 394 | 118 | 66 | 38 | Signals Sparkline SVG |
| Slicer | 32 | 120 | 176 | 56 | Momentum Window (days) |
| KPI value / text card | 242 | 158 | 226 | 32 | KPI Momentum Context |
| KPI value / text card | 498 | 158 | 226 | 32 | KPI Change Context |
| KPI value / text card | 754 | 158 | 226 | 32 | KPI Active Context |
| KPI value / text card | 1010 | 158 | 226 | 32 | KPI Rising Context |
| Table | 32 | 216 | 744 | 480 | dynamic: [Title Momentum] |
| Line chart | 808 | 216 | 440 | 224 | Signal events per month |
| Table | 808 | 472 | 440 | 224 | Backtest: GitHub before funding |

#### Company (1280 x 720)

| Visual | x | y | w | h | Shows |
|---|---|---|---|---|---|
| Text box | 16 | 2 | 560 | 44 | Company detail |
| Page navigator | 592 | 18 | 664 | 36 | one button per visible page; teal = current page |
| KPI value / text card | 16 | 40 | 576 | 32 | Company Header |
| KPI value / text card | 970 | 114 | 160 | 42 | Trend Label |
| SVG image (measure) | 1150 | 116 | 96 | 56 | Signals Sparkline SVG |
| KPI value / text card | 34 | 118 | 276 | 70 | Last Round Text |
| KPI value / text card | 346 | 118 | 276 | 70 | Last Round Date Text |
| KPI value / text card | 658 | 118 | 276 | 70 | Company Funds Text |
| KPI value / text card | 970 | 158 | 170 | 30 | KPI Momentum Context |
| Table | 32 | 216 | 288 | 88 | What they do |
| Table | 324 | 216 | 292 | 144 | Verification |
| Table | 648 | 216 | 600 | 62 | Deal |
| Table | 648 | 278 | 600 | 84 | Investors, as written in the market map |
| Table | 32 | 304 | 288 | 58 | HQ / Greek link |
| Table | 32 | 392 | 584 | 304 | Signals in the tracker snapshot |
| Table | 648 | 392 | 600 | 136 | EU-funded projects naming the company |
| Table | 648 | 560 | 600 | 136 | Greek fund positions and the text behind them |

#### Company tooltip (320 x 240)

| Visual | x | y | w | h | Shows |
|---|---|---|---|---|---|
| KPI value / text card | 10 | 4 | 300 | 40 | Selected Company |
| KPI value / text card | 10 | 60 | 300 | 34 | Last Round Text |
| KPI value / text card | 10 | 110 | 300 | 34 | Company Funds Text |
| SVG image (measure) | 12 | 166 | 170 | 60 | Signals Sparkline SVG |
| KPI value / text card | 196 | 176 | 118 | 40 | Trend Label |

#### About (1280 x 720)

| Visual | x | y | w | h | Shows |
|---|---|---|---|---|---|
| Text box | 16 | 2 | 560 | 44 | About the data |
| Page navigator | 592 | 18 | 664 | 36 | one button per visible page; teal = current page |
| Matrix | 848 | 96 | 400 | 176 | Companies by verification tier |
| Text box | 40 | 100 | 768 | 592 | Sources |
| Matrix | 848 | 304 | 400 | 176 | Round amounts: how they were reported |
| Matrix | 848 | 512 | 400 | 176 | Round dates: precision |

## 4. Background design

Each page background is a PNG at 2x (2560 x 1440), drawn from the same panel coordinates as the visuals. They live in `StaticResources/RegisteredResources/bg_*.png` and are set as the page's canvas background (Format page > Canvas background > Image, Image fit: Fit, Transparency 0%).

| Element | Spec |
|---|---|
| Canvas | `#F1F5F9` |
| Header band | 0-72 px, horizontal gradient `#0F1B2D` to `#173B52`, 3 px teal rule `#0E7C86` along the bottom |
| Panels | White, 12 px corner radius, 1 px `#E6EBF1` outline |
| Panel shadow | `#0F1B2D` at 15%, Gaussian blur 9 px, offset 3 px down |
| KPI tile accent | 3 x 16 px teal bar at x+0, y+14, 2 px radius |
| Section labels | Segoe UI Semibold 10 px, upper case, `#64748B`, at x+14, y+13 inside the tile |
| Tooltip page | 320 x 240, ink `#0F1B2D` background, labels `#8FA3B8` |

To rebuild one in Figma or PowerPoint, make a 1280 x 720 frame, draw the panels at the x, y, w, h values in section 3, apply the shadow above, and export it at 2x.

## 5. Advanced visual elements

**KPI tiles.** Each tile is a painted panel plus:
- a multi-row card for the value (DIN 20 pt)
- a second card for a context line that compares against something real: the prior window, the share of total, or the target funds. Nothing in the data is a target, so no target is invented.
- an SVG sparkline or progress ring, rendered from a DAX measure in an Image visual (Format > Image > Image URL > fx > field value).

**Conditional formatting.**
- *Bar colours:* Format > Bars > Colors > fx > Format style: Field value. They use [Sector Bar Color], [Stage Color] and [Fund Bar Color].
- *Momentum table:* data bars on Score (Cell elements > Data bars), font colour by [Momentum Change Color] and [Trend Color], and arrow icons from [Trend Label].
- *Heatmaps:* background-colour gradients (Cell elements > Background color > Gradient).

**Dynamic titles and subtitles.** Chart titles are insight headlines bound to measures (Format > General > Title > Text > fx), for example "Space & Defense takes 42% of disclosed capital". The header subtitle [Selection Summary] lists the companies in view, the selected sectors and the selected funds.

**Report-page tooltip.** The *Company tooltip* page is a 320 x 240 dark page (Page information > Allow use as tooltip). It shows the last round, the Greek funds, a 12-month signals sparkline and the trend. It is attached to the company tables (Format > General > Tooltips > Type: Report page).

**SVG measures.** These have data category *Image URL* (Measure tools > Data category):
- capital and signals sparklines (area plus line plus end dot)
- progress rings for Greek-fund-backed share and lead share
- a bullet chart in the sector scorecard: the bar is the share of capital, the tick is the share of companies. The bar turns teal when a sector punches above its weight.

The key DAX, in full:

**Capital Sparkline SVG** (data category: ImageUrl): Area sparkline of capital raised by round year, 2019-2026

```dax
VAR yrs = GENERATESERIES ( 2019, 2026, 1 )
VAR t =
    ADDCOLUMNS (
        yrs,
        "@v", VAR y = [Value] RETURN CALCULATE ( [Capital Raised (EUR)], 'Date'[Year] = y ) + 0
    )
VAR mx = MAXX ( t, [@v] )
VAR pts =
    CONCATENATEX (
        t,
        FORMAT ( ( [Value] - 2019 ) * 100 / 7, "0.0", "en-US" ) & ","
            & FORMAT ( 36 - DIVIDE ( [@v], mx ) * 32, "0.0", "en-US" ),
        " ", [Value], ASC
    )
VAR lastY = 36 - DIVIDE ( MAXX ( FILTER ( t, [Value] = 2026 ), [@v] ), mx ) * 32
RETURN
    IF (
        mx > 0,
        "data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='-4 -4 108 46'>"
            & "<polygon points='0,38 " & pts & " 100,38' fill='%23B7DDE0' fill-opacity='0.7'/>"
            & "<polyline points='" & pts & "' fill='none' stroke='%230E7C86' stroke-width='2.5' stroke-linejoin='round' stroke-linecap='round'/>"
            & "<circle cx='100' cy='" & FORMAT ( lastY, "0.0", "en-US" ) & "' r='3.5' fill='%230E7C86'/></svg>"
    )
```

**Backed Share Ring SVG** (data category: ImageUrl): Progress ring: share of companies backed by a Greek fund

```dax
VAR p = [Greek Fund Backed Share %]
RETURN
    IF (
        NOT ISBLANK ( p ),
        "data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 42 42'>"
            & "<circle cx='21' cy='21' r='15.9155' fill='none' stroke='%23E2E8F0' stroke-width='5'/>"
            & "<circle cx='21' cy='21' r='15.9155' fill='none' stroke='%230E7C86' stroke-width='5' stroke-linecap='round' stroke-dashoffset='25' stroke-dasharray='"
            & FORMAT ( p * 100, "0.0", "en-US" ) & " " & FORMAT ( 100 - p * 100, "0.0", "en-US" ) & "'/>"
            & "<text x='21' y='24.6' text-anchor='middle' font-family='Segoe UI' font-weight='600' font-size='10' fill='%230F1B2D'>"
            & SUBSTITUTE ( FORMAT ( p, "0%" ), "%", "%25" ) & "</text></svg>"
    )
```

**Sector Bullet SVG** (data category: ImageUrl): Bullet chart: bar = share of capital, tick = share of companies (scale 0-50%); teal when capital share is the larger

```dax
VAR cs = [Capital Share %] + 0
VAR ks = DIVIDE ( [Companies], CALCULATE ( [Companies], ALLSELECTED ( 'Sector' ) ) )
VAR scale = 0.5
VAR wBar = MIN ( cs / scale, 1 ) * 100
VAR xK = MIN ( ks / scale, 1 ) * 100
VAR barColor = IF ( cs > ks, "%230E7C86", "%2394A3B8" )
RETURN
    IF (
        NOT ISBLANK ( ks ),
        "data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 20' preserveAspectRatio='none'>"
            & "<rect x='0' y='6' width='100' height='8' rx='4' fill='%23E2E8F0'/>"
            & "<rect x='0' y='6' width='" & FORMAT ( wBar, "0.0", "en-US" ) & "' height='8' rx='4' fill='" & barColor & "'/>"
            & "<rect x='" & FORMAT ( MAX ( xK - 1, 0 ), "0.0", "en-US" ) & "' y='1' width='2' height='18' fill='%230F1B2D'/></svg>"
    )
```

**Sector Bar Color**: Accent for the tp sector, neutral for the rest

```dax
VAR tp = MAXX ( ALLSELECTED ( 'Sector'[Sector Short] ), [Capital Raised (EUR)] )
RETURN IF ( [Capital Raised (EUR)] = tp, "#0E7C86", "#B8C4CF" )
```

**Trend Label**: Trend with an arrow icon

```dax
SWITCH ( [Momentum Trend], "Rising", "▲ Rising", "Cooling", "▼ Cooling", "Steady", "► Steady", "Quiet", "• Quiet" )
```

**KPI Momentum Context**

```dax
VAR c = [Momentum Change]
RETURN IF ( c >= 0, "▲ +", "▼ -" ) & FORMAT ( ABS ( c ), "#,0" ) & " vs prior " & [Momentum Window Value] & "d" 
```

**Selection Summary**: Header subtitle that reacts to the sector and fund slicers

```dax
VAR s =
    IF (
        ISFILTERED ( 'Sector'[Sector] ) || ISFILTERED ( 'Sector'[Sector Short] ),
        CONCATENATEX ( VALUES ( 'Sector'[Sector Short] ), 'Sector'[Sector Short], ", " ),
        "all sectors"
    )
VAR f =
    IF (
        ISFILTERED ( 'Fund'[Fund] ) || ISFILTERED ( 'Fund'[Fund Short] ),
        CONCATENATEX ( VALUES ( 'Fund'[Fund Short] ), 'Fund'[Fund Short], ", " ),
        "all Greek funds"
    )
RETURN
    FORMAT ( [Companies] + 0, "0" ) & " companies  ·  " & s & "  ·  " & f & "  ·  snapshot 26 Oct 2026" 
```

**Title Capital by Sector**

```dax
VAR t = ADDCOLUMNS ( VALUES ( 'Sector'[Sector Short] ), "@c", [Capital Raised (EUR)] )
VAR tp = TOPN ( 1, t, [@c], DESC, 'Sector'[Sector Short], ASC )
VAR sh = DIVIDE ( MAXX ( tp, [@c] ), SUMX ( t, [@c] ) )
RETURN IF ( NOT ISBLANK ( sh ), MAXX ( tp, 'Sector'[Sector Short] ) & " takes " & FORMAT ( sh, "0%" ) & " of disclosed capital", "No disclosed capital in this view" )
```

**Title Overlap**

```dax
VAR t =
    ADDCOLUMNS (
        CROSSJOIN ( VALUES ( 'Fund'[Fund Short] ), VALUES ( 'Co-Fund'[Co-Fund Short] ) ),
        "@s", [Co-Investments]
    )
VAR tp = TOPN ( 1, t, [@s], DESC, 'Fund'[Fund Short], ASC, 'Co-Fund'[Co-Fund Short], ASC )
VAR n = MAXX ( tp, [@s] )
RETURN
    IF (
        n > 0,
        MAXX ( tp, 'Fund'[Fund Short] ) & " and " & MAXX ( tp, 'Co-Fund'[Co-Fund Short] ) & " share the most companies (" & n & ")",
        "No two Greek funds share a company in this view"
    )
```

All 88 measures are in [`Key Measures.tmdl`](../GreekDeepTech.SemanticModel/definition/tables/Key%20Measures.tmdl); the design ones sit in the *Design* display folders.

## 6. Navigation and interactivity

- **Page navigator** in the header (Insert > Buttons > Navigator > Page navigator). Three states: default (transparent, light text), hover (white at 12%) and selected (teal fill). The tooltip page is hidden, so it is not listed.
- **Bookmarks** (View > Bookmarks), each limited to selected visuals with Data unticked, so slicer choices survive:
  - *Filters open / Filters closed:* the Filters button in the Overview header slides in a panel with three slicers, a *Clear all* button (button action: Clear all slicers) and *Close*.
  - *Sector view: chart / table:* the Chart and Table pills switch the sector visual between a bar chart and a table with data bars.
- **Drill-through:** right-click any company > Drill through > *Company*. The page opens on Perceptual Robotics by default.
- **Field parameters:** the *Metric* and *Breakdown* selectors on the Sectors page.
- **What-if parameters:** minimum round size (Sectors page) and momentum window (Momentum page). The FX-rate parameters are in the model.
- **Hover states:** every button has a default and a hover fill.

## 7. Polish checklist

| Item | Status |
|---|---|
| Alignment to the 24/16 px grid, every visual inside its panel with 8 px inset | Done (positions generated from one layout) |
| Consistent number formats: €#,0 in tables, €xM text in KPI tiles, one decimal for percentages in tables | Done |
| Chart clutter removed: no gridlines, no axis titles, no default titles, legends only where there is more than one series | Done |
| Colour carries meaning only; one accent plus one warning colour | Done |
| Contrast (WCAG AA needs 4.5:1 for small text): ink `#0F1B2D` on white 17.3:1, slate `#475569` 7.6:1, label grey `#64748B` 4.8:1, teal `#0E7C86` 4.9:1 (and white on teal 4.9:1), orange `#C2410C` 5.2:1, header text `#C9D6E2` on ink 11.7:1 | Done |
| Alt text on every visual | Done |
| Tab order follows reading order (top-left to bottom-right) | Done |
| Mobile layout | Not built. In Desktop: View > Mobile layout, then drag the KPI tiles and the main chart onto the phone canvas. |
| Performance | Import mode over small tables (under 5,000 rows each). SVG measures iterate at most 12 points, and the momentum measures use column filters, not FILTER over whole tables. Not yet timed in Performance analyzer (Optimize > Performance analyzer). |

