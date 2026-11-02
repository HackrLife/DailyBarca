# BarcaFutbol chart styles — codified from Dev's reference images (2 Nov 2026)

These supersede `design_system.md` in the match-review plugin wherever the two differ
(that file's `#0d1b2a` / `#1a1a2e` backgrounds and Palette A are NOT used for these charts).
Build only these formats. Do not invent a new look, palette, font or layout. A chart that is not
in this file needs Dev's approval of a spec first.

Colour values marked (S) were sampled from the pixels of the reference files; (E) are
estimated by eye from the image and must be confirmed with Dev before being treated as final.

## 0. Two families, one rule

| Family | Where | Canvas bg | Used by |
|---|---|---|---|
| **A — StatsDex dark** (default) | Everything built from Sofascore data | `#0f1117` (S) | match statistics, goal timeline, goal cards, team radar |
| **B — Score card dark** | Lead image and the Racing-style timeline | `#0e0d12` (S) | score card, big-scale goal timeline |

Default to family A. Use family B only for the score card (lead image) and when Dev asks for
the large timeline. One family per chart, never mixed inside a chart.
Open question for Dev: should the Racing-style timeline (family B) be retired in favour of the
Feyenoord-style (family A) timeline? Until answered, use A.

## 1. Global tokens

| Token | Hex | Use |
|---|---|---|
| `BG_A` | `#0f1117` (S) | family A canvas |
| `BG_B` | `#0e0d12` (S) | family B canvas |
| `BARCA` | `#a50044` (S) | Barcelona bars, lines, markers, fills |
| `OPP` | `#4a7fb5` (S) | the opponent, always, in every chart |
| `GOLD` | `#e4b719` (S, score card) / `#e8b000` (E, goal cards) | highlight numbers, scorer minute, xGOT and strike |
| `TEXT` | `#ffffff` | titles, subtitles (A) |
| `TEXT_B` | `#f1f1f3` (S) | titles (B) |
| `TEXT_DIM` | `#8a97a6` (E) | axis labels, row labels, subtitles (B), captions |
| `TEXT_FAINT` | `#5e6b7a` (E) | footers, tick labels, left footer |
| `GRID` | `#ffffff` at α 0.08–0.12 (E) | grid lines, family A |
| `BARCA_FILL` | `#220e1c` (S, family A) / `#1d0e18` (S, family B) | area under Barça timeline line |
| `OPP_FILL` | `#221927` (S, family B) | area under opponent line |
| `CARD_BG` | `#141b29` (S) | goal-card panels |
| `CARD_BG_ALT` | `#1b2536` (S) | inner pitch panel / reading card |
| `CARD_BORDER` | `#2a3546` (E) | 1px border on cards and legends |
| `ASSIST_BLUE` | `#5aa0e0` (E) | assist pass line and passer label on goal cards |

The opponent is always `OPP`. The subject team is always `BARCA`. Never recolour per match.
A match against Real Madrid still uses `OPP`.

## 2. Typography

DejaVu Sans only (ships with matplotlib). Titles bold. Sentence case for subtitles, UPPER CASE
for chart titles on the stats and score charts, Title Case on the radar title.

| Role | Size (at the reference canvas) | Weight | Colour |
|---|---|---|---|
| Chart title | 22 pt | bold | `TEXT` |
| Subtitle | 13.5 pt | bold (A) / regular (B) | `TEXT` (A) / `TEXT_DIM` (B) |
| Row / axis label | 11 pt | regular | `TEXT_DIM` |
| Bar value | 11.5 pt | bold | the bar's own colour |
| Footer | 8.5 pt | italic (left), regular (right) | `TEXT_FAINT` |

Render at 300 dpi, solid facecolor, never transparent, never `bbox_inches='tight'` on multi-panel
figures (the existing chart-system rules also apply).

## 3. Footers (exact strings)

Family A, bottom left, italic: `Sofascore published public data`
Family A, bottom right: `Data analysis and design — Dev Das @HackrLife  ·  for BarcaFutbol @BarcaFutbolLive`
(variants by chart in the reference images: match statistics and goal timeline use
`Design and data analysis — Dev Das @HackrLife  ·  for BarcaFutbol @BarcaFutbolLive` and
`Data analysis and design — Dev Das @HackrLife  ·  for BarcaFutbol @BarcaFutbolLive`; the radar
uses `Chart design and analysis — Dev Das @HackrLife  ·  for BarcaFutbol @BarcaFutbolLive`; the goal cards use
`Designed and analysed by Dev Das @HackrLife  ·  for BarcaFutbol @BarcaFutbolLive`.
Open question for Dev: standardise to ONE string. Until answered use the string for that chart type exactly as shown in this file.)
Family B, bottom left: a one-line source note (e.g. `Score: FC Barcelona match report. Statistics: supplied screenshots.`), bottom right: `BarcaFutbol • Dev Das`.
The source note must say where the numbers came from; for Sofascore-pulled data it is `Data: Sofascore`.

## 4. Chart formats

### 4.1 Match statistics comparison (family A, 1600 × 1440 px at the reference, portrait-ish)
- Title `MATCH STATISTICS COMPARISON`, subtitle `<Home> <h>–<a> <Away> | <competition and matchday> | <d Month yyyy>` (en dash in the score).
- Horizontal paired bars, one row per stat, in this order: Possession %, xG, Big Chances, Total Shots, Shots on Target, GK Saves, Corners, Fouls.
- Each row: Barcelona bar (`BARCA`) on top, opponent bar (`OPP`) below, equal thickness, small gap between the two, larger gap between rows.
- Bars are normalised so the higher value of each row is 100 and the other is proportional. The raw value is printed just right of each bar end, bold, in that bar's colour (xG to 2 decimals as given, others as integers; possession as whole numbers without a % sign).
- Row labels right-aligned left of the axis in `TEXT_DIM`. Bottom axis 0–100, ticks every 20, caption centred below: `Normalised to the higher value in each row`.
- Legend top right in a rounded box (`CARD_BG`, `CARD_BORDER`): Barcelona, <Opponent>.
- No gridlines, no top/right spines, bottom spine in `CARD_BORDER`.

### 4.2 Score card — lead image (family B, 2000 × 857 px)
- Title `BARCELONA 7–2 RACING SANTANDER` upper case, bold, `TEXT_B`, centred at the top. Subtitle centred under it, `TEXT_DIM`, regular: `<Venue>  |  <d Month yyyy>  |  Half-time <h>–<a>`.
- Score `7 – 2` very large (about 110 pt), bold, `TEXT_B`, centred in the upper half.
- A row of exactly four stats evenly spaced across the lower third: value in `GOLD`, bold, ~38 pt; label under it in `TEXT_DIM`, ~15 pt. The four stats are: Barcelona xG, Shots, Big chances, Corners (always these four, in this order).
- Footer: source note left, `BarcaFutbol • Dev Das` right.
- No other decoration.

### 4.3 Goal timeline — standard (family A, 1600 × 685 px)
- Title `GOAL TIMELINE`, subtitle `<Home> <h>–<a> <Away> | <competition and matchday> | <d Month yyyy>` (bold white).
- X: match minutes 0–90 (ticks every 15; stoppage time may extend past 90 only when goals fall there). Y: goals, integer ticks, top set to max goals + 1.
- Two stepped lines, Barça `BARCA` and opponent `OPP`, 2.2 px, step goes up at the goal minute, filled beneath with `BARCA_FILL` / `OPP_FILL` at low alpha; round marker at each goal.
- Dashed vertical line at 45 with label `HT` in `TEXT_FAINT` to its upper right.
- Each goal carries a rounded label box with a 1 px border in the team colour, text in the team colour, two lines: `Scorer` bold / `minute'`; own goals `(OG)`, penalties `(pen)` appended to the name. Boxes sit above the marker (Barça) or above/below as needed so none overlap; the validator must catch overlaps.
- Legend top left in a rounded box. Axis labels `Match Minutes` / `Goals`.
- Footer family A.

### 4.4 Goal timeline — large (family B, 2000 × 1143 px)
Same data and logic as 4.3 but: bg `BG_B`, title `GOAL TIMELINE` centred bold ~34 pt, subtitle `<Home> <h>–<a> <Opponent>  |  Each step marks a goal` in `TEXT_DIM`, line weight 4 px, label boxes filled with the canvas colour, text white, border in team colour, minute marker `′` (U+2032), x-axis label `Match minute`, footer is a source note left and `BarcaFutbol • Dev Das` right. Use only when Dev asks.

### 4.5 Goal cards (family A, 1355 × 2000 px, portrait)
A grid of cards, two per row, one card per Barcelona goal in match order, plus a final `READING EACH CARD` card in the last free slot.
- Title `BARCELONA'S <N> GOALS` (upper case, N spelled as a word), subtitle `<Home> <h>–<a> <Away>  ·  <competition and matchday>  ·  <venue>  ·  <d Month yyyy>`.
- Card: rounded rectangle `CARD_BG`, 1 px `CARD_BORDER`.
  - Top row: minute in `GOLD` bold (e.g. `3'`) then scorer name white bold; running score in a small rounded pill at top right (`1-0`).
  - Line 2: `<Left footed|Right footed|Head> · Assisted by <Name>` (or `Direct free kick, unassisted`) in `TEXT_DIM`.
  - Line 3 (white-grey): one factual sentence on how the move was built. Line 4 and 5 (italic, `TEXT_FAINT`): one editorial line (max 2 lines).
  - Goal mouth at the top: white frame, dark mesh, the shot's finishing zone lit in gold with a ringed ball, `LEFT` / `RIGHT` small labels either side.
  - Pitch below: attacking half only, goal at the top, markings in `#2f3d52` (E) on `CARD_BG_ALT`; shot origin as a gold ringed ball with a solid gold line to the goal-mouth point; dashed grey-blue line for the scorer's carry with label `carried N m`; assist pass as a dotted `ASSIST_BLUE` curve from the passer (blue dot and name label); `shot from N m` bottom right in `TEXT_FAINT`.
  - Bottom rail: grey dot at xG (label `xG 0.00`, `TEXT_FAINT`), gold dot at xGOT (label `xGOT 0.00`, gold bold), gold bar between them, delta pill at the right in gold on a dark-gold fill (`+0.00`).
- Final card `READING EACH CARD`: bold white title, then the key in the three line colours (blue for the assist, grey for the carry, gold for the shot), and a summary box at the bottom: `<sum xG> xG  ·  <sum xGOT> xGOT` in gold, one grey line under it. Add a line naming any opponent goal not shown.
- Footer family A (goal-card string).
- Data: shot coordinates and goal-mouth position from the spatial pull; carry and passer position are drawn only when the data supports it. Never estimate a missing coordinate: draw the card without that element and log it.

### 4.6 Team performance radar (family A, 1600 × 1600 px, square)
- Title `Team Performance Radar` (Title Case, bold white), subtitle `<Home> <h>–<a> <Away> — MD<n>` bold white.
- Eight axes, clockwise from the right: Possession %, Shots on Target, xG, Final Third Entries, Tackles, Duel Win %, Pass Accuracy %, and back. Axis labels bold white, two-line where long.
- Each axis normalised 0–100 (higher value of the two teams = 100, same rule as 4.1); radial ticks 20/40/60/80/100 in `TEXT_FAINT`, dotted rings, thin outer circle in `CARD_BORDER`.
- Barça: dashed 2.5 px `BARCA` line, round markers, fill `BARCA` at α≈0.3. Opponent: dashed 2.5 px `OPP` line, markers, fill `OPP` at α≈0.25. Barça drawn first, opponent on top.
- Legend top left in a rounded box.
- Footer family A (radar string).

## 5. Rules for every chart
1. Opponent is always `OPP`, subject is always `BARCA`.
2. Titles and subtitles follow the patterns above; the subtitle always names the match, competition, matchday and date exactly (taken from the match data, never retyped).
3. Every printed number traces to the raw Sofascore file; the chart-data JSON for each chart is saved beside the PNG.
4. Normalised charts say they are normalised (the caption in 4.1; a note in the footer for 4.6).
5. Validate before save: no text overlap, no clipping, glyphs renderable, title/subtitle not overprinting, contrast ≥ 4.5:1 for body text (decorative `TEXT_FAINT` footers are exempt).
6. Checker B opens every PNG and checks it against this file: colours, order of rows/axes, footer string, subtitle exactness.
7. Ask Dev before adding any chart type not listed here.

## 6. What is not yet specified (needs Dev)
- The other standard visualisations Dev said are coming (the format list). They are added here as new sections, with a reference image each.
- Confirmation of the (E) values, and whether to standardise the footer string and retire family B.
- Any chart with player colours (the old table in `design_system.md`) — keep only if Dev confirms it still applies.
