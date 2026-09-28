---
name: capcut-editing-memory
description: Learn and recall the user's CapCut editing preferences from native project files, including BGM, sound effects, transitions, and text X/Y positions. Use when asked to remember an edit, learn a CapCut style, or reuse saved editing preferences. Read backend files only; never control the desktop.
---

# CapCut editing memory

Read native files and maintain persistent, source-backed editing memory. Never control the mouse, keyboard, screen, or CapCut UI. Learning is read-only with respect to source projects. Do not claim background monitoring or automatic observation between requests.

## Memory location and precedence

Use `~/.codex/memories/capcut-editing-memory/` for persistent records: `preferences.md` for confirmed reusable choices and `observations/<project-id>/<snapshot-hash>.json` for source-backed observations. Resolve the user's actual home directory. Create these only when recording real evidence; do not invent sample observations. If writing there is blocked, retain a workspace copy and clearly state the actual location.

Read existing preferences before learning or applying a style. Also read the current workspace's `CAPCUT_MEMORY.md` if present. Latest explicit user instructions override saved defaults; explicit preferences override inferred patterns. Use [references/learning.md](references/learning.md) for extraction and recording. Read [references/seed-preferences.md](references/seed-preferences.md) only for the previously saved style baseline; it contains no verified BGM names, transition names, or text coordinates.

## Learn from the user's work

Identify the intended user-edited project, then inspect its root draft, metadata, and active timeline mapping. Never assume the newest project is the intended one or that an agent-created candidate is user-approved. If no project is identified, discover candidate project names from local files and ask which to learn from. Do not scan unrelated media or choose a candidate arbitrarily.

Read the actual saved draft and capture its hash and timestamp. Resolve active timeline references from metadata instead of assuming the root draft is current. If root and active timeline disagree and the authoritative version cannot be established, keep them distinct and ask. Encrypted, unreadable, or unknown structures must be reported, not overwritten or silently interpreted as an empty edit.

The request to remember editing authorizes recording observations. It does not make every observed asset or coordinate a universal default. Separate user-confirmed reusable preferences, clip-specific observations, and inferred patterns. Prefer the user's corrections to agent output. When learning across several projects, retain project-specific variants instead of averaging incompatible styles.

Save real BGM/SFX identities, transition details, and exact text X/Y with provenance. Missing values remain unknown, not zero. Report what was actually learned and what remains unresolved.

## Reuse

Select the relevant role and style variant before applying memory. Verify resource availability and inspect the destination project's native schema, canvas, and coordinate conventions. Reuse exact X/Y only in a compatible layout; otherwise adapt explicitly while retaining the source values. Never fabricate effect IDs or substitute unavailable assets silently.

This skill stores and retrieves preferences. For native project mutations, use the installed `ipnimma-capcut` skill if available; otherwise inspect native structure and make a verified, recoverable copy. A memory request alone does not authorize project edits. Preserve approved footage, speech, timing, and user corrections unless the user requests a change. Backend validation does not establish that playback was watched or heard.
