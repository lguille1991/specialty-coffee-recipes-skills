---
name: coffee-recipe-generator
description: Storage-optional, harness-agnostic specialty coffee workflow for bag analysis, recipe generation, recipe adaptation, and primary-source brewing research.
metadata:
  version: "1.0.0"
  author: Portable Skill Template
  tags: Coffee, Brewing, Barista, Research, Portable
  recipe_generation_parameters:
    - name: brew_method
      label: Brewing method
      required: true
      prompt: "What brewing method do you want to use?"
    - name: coffee_dose_grams
      label: Coffee dose in grams
      required: true
      prompt: "How many grams of coffee will you be using for this recipe?"
    - name: flavor_intent
      label: Flavor intent
      required: true
      prompt: "What flavor direction do you want: clarity, balanced, sweetness, body, or forgiveness?"
---

# Specialty Coffee Core

## Compatibility

This skill is designed to work across different agent harnesses and note systems.
- It does not require Obsidian.
- It does not require any specific agent tool API.
- It must remain functional when no persistent storage is configured.
- Storage, if available, is an optional enhancement for loading and saving profiles, recipes, and research.

When adapting this skill to a specific system, map workflow steps by capability:
- image extraction / OCR
- web extraction / browser access
- file read / write
- optional profile-store lookup

For portability rules, load `references/portability-and-storage.md`.

## When to Use

Load this skill when the user:
- shares a photo of a coffee bag or label
- asks to create, generate, or adjust a brewing recipe
- asks to adapt an existing recipe to a different bean, brewer, or equipment version
- wants to research brewing science, equipment, or competition techniques
- may want to save coffee profiles or recipes to an optional storage destination

## Required Inputs

| Workflow | Required Inputs |
|----------|----------------|
| Bag Analysis | Image of the coffee bag/label |
| Recipe Generation | Brew method, coffee dose (g), origin, processing method, flavor intent: clarity, balanced, sweetness, body, or forgiveness |
| Recipe Adaptation | Base recipe, target bean profile OR target brewer/equipment version, flavor intent: clarity, balanced, sweetness, body, or forgiveness |
| Research | Topic or question |

Optional adjustments: roast level, strength preference, equipment available.

---

## Workflow A: Bag Analysis

1. Extract text from the coffee bag image using the available image/OCR capability. Request: Brand, Variety, Processing method, Farm/Producer, Origin, Elevation, Roast level, Tasting notes (both languages), Roast date.
2. Normalize the result: standardize processing terms, convert elevation to `msnm`, preserve bilingual tasting notes, classify acidity/sweetness balance.
3. Build the profile with `templates/coffee-profile.md`. Generate a safe filename: `{Brand} - {Variety} {Process} - {Farm or Origin}.md`.
4. If a destination is configured or explicitly requested, save the profile to the user's profile store. Otherwise, return the completed profile inline as markdown.
5. Confirm what was extracted, what was missing, and whether the result was saved or returned inline.

Pitfalls:
- Ask for a clearer photo if critical fields are unreadable.
- Do not guess a missing processing method.
- If no image is available yet, explain that you will fill `templates/coffee-profile.md` and either save it or return it inline once the image is received.

---

## Workflow B: Recipe Generation

1. Check for an existing bean profile using this source order: current conversation inputs → attached file/note → configured profile store (if any). If none exist, ask for missing bean details.
2. Gather required recipe inputs before generating: brew method, coffee dose in grams, origin, processing method, and flavor intent. Flavor intent must be one of: clarity, balanced, sweetness, body, or forgiveness. If brew method is missing, ask: “What brewing method do you want to use?” If coffee dose is missing, ask: “How many grams of coffee will you be using for this recipe?” If flavor intent is missing, ask: “What flavor direction do you want: clarity, balanced, sweetness, body, or forgiveness?” If multiple required inputs are missing, ask for them in the same message. Do not assume or default the brew method, coffee dose, or flavor intent. Origin and processing method are non-negotiable. Do not require a grinder model before generating a recipe, because grinder settings are always produced for the full grinder set below.
3. Load `references/brew-method-defaults.md` for the method base.
4. Load `references/grind-determinants.md` and `references/grinder-settings.md`. Apply the five-determinant stack: method base → processing → origin/altitude → roast → variety.
5. Always include exact settings for every grinder in `references/grinder-settings.md` in one markdown table: 1Zpresso K-Ultra, 1Zpresso Q Air, Baratza Encore ESP, Fellow Opus, and Timemore C2. This is required even when the user mentions only one grinder, does not specify a grinder, or asks for a quick recipe.
6. Load `references/origin-processing-guide.md` and adjust temperature for origin, process, and roast.
7. Fill `templates/recipe-output.md`.
8. Mandatory output sections, in this order:
   - Coffee Details
   - Overview
   - Flavor Profile
   - Brew Timeline
   - Brewing Steps
   - Troubleshooting Guide
   - Adjusting for Your Taste
9. Before returning the recipe, verify the Overview contains a grinder table with exactly these five rows: 1Zpresso K-Ultra, 1Zpresso Q Air, Baratza Encore ESP, Fellow Opus, Timemore C2.
10. Verify the selected flavor intent appears in the Overview and is reflected in the Flavor Profile and Adjusting for Your Taste guidance.
11. Offer pairing context when useful by consulting `references/brew-method-pairings.md` or `references/equipment-profiles.md`.
12. If the user explicitly wants 4:6, load `references/four-six-method.md`.
13. Remind the user this is a starting recipe and offer to refine after brewing.

Pitfalls:
- Never omit any of the five grinder rows from generated or adapted recipes.
- Never rely on generic grind descriptions alone; generic descriptors may appear only as a secondary label after the exact grinder table.
- Never assume a default brew method, coffee dose, or flavor intent; ask the user when any are missing from the initial prompt.
- Never fail recipe generation just because no profile store exists.

---

## Workflow C: Primary-Source Research

1. Skip general search engines when they are unreliable in the current harness.
2. Navigate directly to relevant domains from `references/coffee-research-sources.md`.
3. Extract the source text using whatever web/browser capability the harness provides.
4. Synthesize the result into structured markdown with these sections:
   - Summary
   - Key Mechanisms
   - Practical Effects / Comparison Table
   - Expert Techniques
   - Sources (exact URLs)
   - Action Items
5. Validate that all six sections are present.
6. Save the research only if a destination is configured or requested; otherwise return it inline.

Pitfalls:
- When primary blogs are blocked, look for open-source calculators or recipe implementations that preserve the original parameters.
- Include exact URLs in the Sources section.

---

## Workflow D: Recipe Adaptation

1. Read the base recipe and any available bean profile.
2. Gather the required flavor intent before adapting. Flavor intent must be one of: clarity, balanced, sweetness, body, or forgiveness. If missing, ask: “What flavor direction should the adapted recipe target: clarity, balanced, sweetness, body, or forgiveness?”
3. Identify what changed:
   - bean swap
   - brewer swap
   - attachment/filter swap
4. Apply adaptation rules from `references/brewer-version-adaptation.md`.
5. Rebuild the recipe using `templates/recipe-output.md` and include a clear “Changes from Base” section.
6. Include the full five-grinder table required by Workflow B, recalculated for the adapted recipe rather than copied blindly from the base recipe.
7. Verify the selected flavor intent appears in the Overview and is reflected in the Flavor Profile and Adjusting for Your Taste guidance.
8. Set expectations honestly when a bean cannot reproduce the same style as another.
9. Save only if a destination is configured or requested; otherwise return the adapted recipe inline.

Pitfalls:
- Do not blindly copy numbers from one bean to another.
- Do not ignore process, variety, or brewer geometry differences.

---

## References Index

| File | Workflow Step | Purpose |
|------|---------------|---------|
| `references/portability-and-storage.md` | Cross-cutting | Portability pattern for non-Obsidian and runtime-agnostic environments |
| `references/brew-method-defaults.md` | B-3, D-3 | Base parameters per brew method |
| `references/grind-determinants.md` | B-4 | Five-determinant grind calculation |
| `references/grinder-settings.md` | B-4 | Exact grinder settings for K-Ultra, Q Air, Encore ESP, Fellow Opus, Timemore C2 |
| `references/origin-processing-guide.md` | B-6 | Origin, variety, and roast temp guidance |
| `references/brew-method-pairings.md` | B-9 | Matching coffee profile to brew method |
| `references/equipment-profiles.md` | B-9 | Personal brewer design notes and pairings |
| `references/troubleshooting.md` | B-8 / standalone | Taste diagnosis and fixes |
| `references/pour-patterns.md` | B-7 | Pour pattern descriptions and speed reference |
| `references/four-six-method.md` | B-10 | Tetsu Kasuya 4:6 Method; filename spells out leading numeral by convention |
| `references/coffee-research-sources.md` | C-2 | Primary-source domains and HCG workflow |
| `references/grind-size-extraction-yield.md` | C / standalone | Condensed research: grind size vs extraction yield |
| `references/orea-v4-research.md` | C / standalone | Canonical Orea V4 bottoms, filters, and competition recipes |
| `references/brewer-version-adaptation.md` | D-3 | Adapting recipes between brewer versions |
| `templates/coffee-profile.md` | A-3 | Structured bean profile scaffold |
| `templates/recipe-output.md` | B-7, D-4 | Recipe output scaffold |
