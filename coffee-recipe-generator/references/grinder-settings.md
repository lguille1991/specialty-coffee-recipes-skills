# Grinder Settings Reference

Use these tables for every generated or adapted recipe. Recipe outputs must include exact settings for all five grinders in this file, even if the user specifies only one grinder or no grinder at all. Generic descriptions such as medium-fine or medium may be included only as secondary context after the exact grinder table.

Required recipe grinder rows:
- 1Zpresso K-Ultra
- 1Zpresso Q Air
- Baratza Encore ESP
- Fellow Opus
- Timemore C2

If a brew method is unsupported by a grinder, keep that grinder row and write `Not supported`, then add the closest practical alternative only when the reference below supports one.

> **Sources:** 1Zpresso data from [1zpresso.coffee/grind-setting](https://1zpresso.coffee/grind-setting/) (official). Baratza Encore ESP data from [Baratza official brew guides](https://www.baratza.com/en-us/blog/brew-guides/) (AeroPress and Chemex guides verified). Fellow Opus data from [Honest Coffee Guide's Coffee Grind Size Chart](https://honestcoffeeguide.com/coffee-grind-size-chart/) with brand `Fellow` and model `Opus` selected.

## 1ZPresso K-Ultra (Rotation.Number.Tick — external adjustment)

**Format:** `Rotation.Number.Tick` (e.g., `0.5.3` = 0 rotations, 5th number, 3rd tick = 53 ticks total). The K-Ultra has 10 numbered positions per rotation (`0` through `9`) with 10 ticks per number, so `1.0.0` means one full rotation / 100 ticks. Never confuse `0.0.0` with a usable grind setting; it is the fully tightened zero point.

> **Source:** [honestcoffeeguide.com 1Zpresso K-Ultra grind settings](https://honestcoffeeguide.com/1zpresso-k-ultra-grind-settings/)

| Brew Method | K-Ultra Setting | Notes |
|-------------|-----------------|-------|
| Turkish | 0.0.6 – 0.2.8 | |
| Espresso | 0.2.4 – 0.5.0 | |
| V60 | 0.5.3 – 0.9.2 | |
| AeroPress | 0.4.3 – 1.0.0 | Wide range; finer end for short/standard brews, coarser for long immersion |
| Moka Pot | 0.4.8 – 0.8.6 | |
| Pour Over | 0.5.4 – 1.0.0 | |
| Siphon | 0.5.0 – 1.0.0 | |
| Filter Coffee Machine | 0.4.0 – 1.0.0 | |
| French Press | 0.9.1 – 1.0.0 | Near grinder limit |
| Cupping | 0.6.1 – 1.0.0 | |
| Cold Brew | 1.0.0 | Grinder max |
| Cold Drip | 1.0.0 | Grinder max |
| Steep-and-release | 0.6.0 – 1.0.0 | Inverted AeroPress, Switch, full-immersion dripper |

**Important:** Never grind at `0.0.0` (fully tightened). HCG ranges above. For **V60**, start near `0.7.0` (70 ticks) and adjust ±0.1.0. For **standard AeroPress** (1–2 min, 15–18 g), start near `0.6.0` (60 ticks). For **inverted/long-immersion AeroPress** (2+ min, 20 g+), use `0.7.0 – 0.8.0` (70–80 ticks) to avoid over-extraction. For **Chemex**, start at `0.8.5` (85 ticks). For **cold brew**, `1.0.0` is the grinder maximum and should be treated as marginal/practical-max rather than freely adjustable extra-coarse range. The K-Ultra has exceptional particle uniformity — very minimal fines. The external adjustment ring makes it easy to note and repeat exact settings.

## 1ZPresso Q Air (HCG Rotation format — internal adjustment)

**Format:** Uses `Rotation.Number.Tick` format directly (same notation as K-Series but different internal mechanism and scale). The Q Air has ~8 numbers per rotation with ~4 ticks per number.

> **Source:** [honestcoffeeguide.com 1Zpresso Q Air grind settings](https://honestcoffeeguide.com/1zpresso-q-air-grind-settings/)

| Brew Method | Q Air Setting | Notes |
|-------------|---------------|-------|
| Turkish | 0.1.1 – 0.6.1 | |
| Espresso | 0.5.1 – 1.1.0 | |
| V60 | 1.2.0 – 2.0.1 | |
| AeroPress | 0.9.2 – 2.8.0 | Wide range; finer end for short brews, coarser for long immersion |
| Moka Pot | 1.0.2 – 1.9.1 | |
| Pour Over | 1.2.1 – 2.7.1 | |
| Siphon | 1.1.1 – 2.3.1 | |
| Filter Coffee Machine | 0.9.0 – 2.6.1 | |
| French Press | 2.0.1 – 3.8.0 | |
| Cupping | 1.3.2 – 2.5.0 | |
| Cold Brew | 2.3.2 – 4.0.0 | |
| Cold Drip | 2.4.1 – 3.7.1 | |
| Steep-and-release | 1.3.1 – 2.4.0 | Inverted AeroPress, Switch, full-immersion dripper |

**Important:** The Q Air uses a different internal mechanism than K-Series grinders — the HCG rotation format is **not directly comparable** to K-Ultra settings. A setting of `1.0.0` on Q Air is much coarser than `1.0.0` on K-Ultra. The Q Air is optimized for coarser grinds (pour-over through French Press) and is lighter (365g) — excellent for travel. Start at `1.5.0` for pour-overs and adjust ±0.2.0–0.3.0 based on taste. For **inverted/long-immersion AeroPress** (2+ min, 20 g+), use `1.8.0 – 2.0.0`. For **cold brew**, the Q Air can reach HCG cold brew ranges, but use the coarse end and expect limited room to adjust if you need very coarse immersion grinds.

## Baratza Encore ESP (Settings 1-40, stepped)

**Specifications:** 40 stepped settings (no micro-adjustments between steps), M40 steel-coated burrs.

| Brew Method | Encore ESP Setting | Notes |
|-------------|-------------------|-------|
| Turkish | — | Not supported |
| Espresso | 0 – 13 | |
| V60 | 7 – 18 | |
| AeroPress | 3 – 29 | Wide range; finer end for short brews, coarser for long immersion |
| Moka Pot | 5 – 17 | |
| Pour Over | 7 – 28 | |
| Siphon | 6 – 23 | |
| Filter Coffee Machine | 3 – 27 | |
| French Press | 19 – 40 | |
| Cupping | 9 – 25 | |
| Cold Brew | 24 – 40 | |
| Cold Drip | 24 – 40 | |
| Steep-and-release | 9 – 24 | Inverted AeroPress, Switch, full-immersion dripper |

**Verified Baratza official settings:**
- **AeroPress:** Setting 22 (from [Baratza AeroPress Brew Guide](https://www.baratza.com/en-us/blog/brew-guides/aeropress-brew-guide))
- **Chemex:** Setting 30 (from [Baratza Chemex Brew Guide](https://www.baratza.com/en-us/blog/brew-guides/chemex-brew-guide))
- **General Encore ESP reference:** Setting 25 (same Chemex guide page)

**Notes:** The Encore ESP is a stepped grinder (1=finest, 40=coarsest). HCG does not list a dedicated ESP table; ranges above are adapted from the standard Encore and align closely with ESP behavior. For **standard AeroPress** (1–2 min, 15–18 g), start at 22. For **inverted/long-immersion AeroPress** (2+ min, 20 g+), use **24–26** to avoid over-extraction. Unlike the 1Zpresso hand grinders, you cannot make micro-adjustments between steps — each step is a discrete jump. Start at 18 for unknown pour-overs and adjust ±2–3 steps. The M40 burrs are ceramic-coated steel and produce more fines than pure ceramic burrs — this can affect flow rate in paper-filter brewers. Clean the burrs and grind chamber regularly; the Encore ESP retains fines more than hand grinders.

## Fellow Opus (Dial settings 1–11 with decimal intermediates)

**Specifications:** HCG exposes the Opus on a numeric dial from **1 to 11**, with intermediate decimal positions such as **2.5**, **7.25**, and **8.75**.

> **Source:** [honestcoffeeguide.com Coffee Grind Size Chart — Fellow Opus](https://honestcoffeeguide.com/coffee-grind-size-chart/)

| Brew Method | Fellow Opus Setting | Notes |
|-------------|---------------------|-------|
| Turkish | N/A | Not listed by HCG for Opus |
| Espresso | 1 – 2.5 | |
| V60 | 3 – 6 | |
| AeroPress | 2 – 8.75 | Wide range; finer end for short/standard brews, coarser for long immersion |
| Moka Pot | 2.5 – 5.5 | |
| Pour Over | 3 – 8.5 | |
| Siphon | 2.75 – 7 | |
| Filter Coffee Machine | 2 – 8 | |
| French Press | 6 – 11 | Near grinder limit |
| Cupping | 3.5 – 7.5 | |
| Cold Brew | 7.25 – 11 | Near grinder limit |
| Cold Drip | 7.5 – 11 | Near grinder limit |
| Steep-and-release | 3.5 – 7.25 | Inverted AeroPress, Switch, full-immersion dripper |

**Notes:** Use the HCG range as the base map for the Opus. For unknown pour-overs, start near **5.0** and adjust up or down based on taste and drawdown. For **standard AeroPress** (1–2 min, 15–18 g), start near **4.5–5.0**. For **inverted/long-immersion AeroPress** (2+ min, 20 g+), start near **6.0–6.5** to avoid over-extraction. For **French Press**, start near **8.5–9.0**. Because HCG shows decimal positions rather than simple whole-number steps, preserve decimals exactly when recording recipes and dial-ins.

## Timemore C2 (Clicks from zero, stepped)

**Specifications:** Can grind coffee between a range of **0 – 950 microns**. 30 stepped click settings (no micro-adjustments between clicks). Uses stainless steel burrs.

> **Warning:** Avoid using settings below **6 clicks**, as these settings may dull the burrs.
>
> **Source:** [honestcoffeeguide.com Timemore C2 grind settings](https://honestcoffeeguide.com/timemore-c2-grind-settings/)

| Brew Method | C2 Setting (clicks) | Notes |
|-------------|---------------------|-------|
| Turkish | 2 – 6 | At burr-dulling limit; use with caution |
| Espresso | 6 – 12 | |
| V60 | 13 – 22 | |
| AeroPress | 11 – 30 | Wide range; finer end for short/standard brews, coarser for long immersion |
| Moka Pot | 12 – 20 | |
| Pour Over | 13 – 29 | |
| Siphon | 12 – 25 | |
| Filter Coffee Machine | 10 – 28 | |
| French Press | 22 – 30 | Near grinder limit |
| Cupping | 15 – 26 | |
| Cold Brew | 26 – 30 | Near grinder limit |
| Cold Drip | 26 – 30 | Near grinder limit |
| Steep-and-release | 15 – 26 | Inverted AeroPress, Switch, full-immersion dripper |

**Notes:** The C2 is a compact, budget-friendly hand grinder with stepped clicks (no micro-adjustment between steps). For **V60**, start near **18 clicks** and adjust ±2–3 clicks. For **standard AeroPress** (1–2 min, 15–18 g), start near **16 clicks**. For **inverted/long-immersion AeroPress** (2+ min, 20 g+), use **20–22 clicks** to avoid over-extraction. For **Chemex** (which needs a coarser grind than V60), start at **20–22 clicks**. The C2 produces slightly more fines than premium hand grinders like the K-Ultra, so flow rates may run a bit slower — adjust accordingly. The click mechanism is internal (adjust by turning the adjustment dial under the burr); always count clicks from zero (fully tightened, burrs touching). Because settings below 6 clicks risk burr damage, espresso and Turkish grinds are near the lower practical limit. Clean the burrs regularly to maintain consistent output.
