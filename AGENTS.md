# Repository Guidelines

## Project Structure & Module Organization

This repository is a small, documentation-first skill package. The root contains [README.md](/Users/guillermoabrego/Downloads/specialty-coffee-recipes-skills/README.md) and this guide. The main deliverable lives in `coffee-recipe-generator/`:

- `SKILL.md`: the primary skill definition and workflow rules
- `references/`: source material and operating guidance for recipe generation and research
- `templates/`: output scaffolds such as `coffee-profile.md` and `recipe-output.md`

Keep new content close to the skill it supports. For example, add brewing research under `coffee-recipe-generator/references/` and reusable output formats under `coffee-recipe-generator/templates/`.

## Build, Test, and Development Commands

No build pipeline or package manager is configured in this repository. The useful local commands are basic inspection commands:

- `git status`: review pending changes before editing docs or skill files
- `find coffee-recipe-generator -maxdepth 2 -type f | sort`: inspect the current file set
- `cat coffee-recipe-generator/SKILL.md`: review the primary workflow before making changes

If you add tooling later, document the exact commands here and in `README.md`.

## Coding Style & Naming Conventions

Prefer concise Markdown with clear headings and short paragraphs. Match the existing style in `SKILL.md`: imperative instructions, explicit constraints, and ordered workflows. Use lowercase kebab-case for new reference filenames such as `water-quality.md`. Keep templates descriptive and task-oriented, for example `espresso-output.md`.

## Testing Guidelines

There is no automated test suite today. Validate changes by reading the edited Markdown end to end and checking that:

- internal paths are real
- section ordering is still logical
- templates and references named in `SKILL.md` actually exist

When changing workflow rules, verify examples and required output sections remain consistent with the referenced files.

## Commit & Pull Request Guidelines

Recent history mixes short descriptive commits with Conventional Commit prefixes such as `fix:`. Prefer concise, imperative subjects under 72 characters, for example `fix: tighten grinder guidance` or `docs: add origin reference`.

Pull requests should include a clear summary, the reason for the change, and note any affected files or workflows. Include rendered Markdown screenshots only when formatting changes are substantial.
