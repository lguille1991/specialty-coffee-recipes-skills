# Portability & Storage-Agnostic Pattern

Use this reference when adapting the specialty-coffee workflow for users outside a specific agent runtime, outside Obsidian, or in mixed tool environments.

## Core Principle

The coffee logic must work **without any persistent store**. Storage is an enhancement, not a prerequisite.

## Preferred Source Order for Bean Data

When generating a recipe, look for bean details in this order:

1. Current conversation inputs
   - user-written bean description
   - pasted profile text
   - uploaded coffee bag image
2. Attached file or note supplied in-session
3. Configured external profile store (if any)
   - Obsidian
   - local folder
   - Notion / Drive / database
4. Ask the user for missing required inputs

Never fail recipe generation just because a profile store is unavailable.

## Storage Model

Treat storage as one of four modes:

- `none` — no save/load behavior; return results inline
- `local_files` — read/write generic markdown files in a user-specified folder
- `obsidian` — use vault paths and note conventions
- `other` — use the host system's configured store

If no storage mode is configured, default to `none`.

## Capability-Based Tool Mapping

For portable instructions, describe capabilities rather than runtime-specific tool names.

Prefer:
- "extract text from the coffee bag image"
- "consult the grinder settings reference"
- "read the primary source page"
- "save to the configured destination if available"

Avoid requiring runtime-specific tool names or APIs directly in the portable version.
Instead, describe the capability needed, such as image OCR, reference lookup, page-text extraction, or file writing.

Runtime-specific wrappers can still map those capabilities to concrete tools.

## Save/Load Rules

- Bag analysis must be able to return a finished profile inline.
- Recipe generation must work from inline inputs alone.
- Recipe adaptation must not assume a saved base recipe exists.
- Research synthesis may be returned inline unless the user explicitly wants persistence.

## Output Design

All templates should remain plain markdown so they work in:
- chat
- text files
- Obsidian
- Notion paste
- GitHub markdown

## Recommended Skill Split

For sharing across systems, separate:

1. **core workflow skill**
   - domain logic only
   - no storage assumptions
   - no harness-specific tool names
2. **storage integration skill**
   - Obsidian or other persistence layer
3. **harness wrapper skill**
   - maps workflow steps onto the active agent's tools

## Pitfall

Do not make "check the Obsidian vault first" a required first step. That breaks recipe generation for users who only provide bean details in chat.