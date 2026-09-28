# Extracting a style observation

CapCut schemas vary by platform and version. Inspect actual field names and retain their JSON paths. Do not treat this guide as a fixed schema. Store a focused record of editing materials, not an entire account or project metadata dump.

## Provenance

Each observation records project name/ID, absolute source draft path, active timeline ID, SHA-256 of draft bytes, source modification time, capture time, canvas width/height and FPS when present. Include track/segment/material IDs and source JSON paths for each captured item. If files change during extraction, re-read before saving a coherent snapshot. Preserve old snapshots; do not overwrite prior observations with an unrelated project.

Resolve a segment's `material_id` and `extra_material_refs` against materials collections. Keep unresolved references explicitly marked. Record observed timing units; native drafts commonly use microseconds, but verify the actual format before conversion.

## BGM and sound effects

Capture the native name, material/library/resource/music/effect IDs that actually exist, source path, local availability, source and target ranges, volume/gain with its native units, fades, loops, speed, and volume keyframes when present. Keep full asset duration distinct from the used excerpt duration.

Classify as BGM, SFX, dialogue, or unknown using actual metadata, track context, and user labels. An audio track or filename alone may be ambiguous; do not misremember dialogue as music. Record uncertain roles without promoting them to defaults. Exact loudness and audible balance cannot be established solely from a volume scalar.

## Transitions

Inspect transition materials and their links to segment boundaries, including extra references and separate tracks where the schema uses them. Capture the native name/resource ID, duration and unit, parameters, referenced segment pair or boundary, and local resource path if present. Do not confuse text entrance animations, video effects, or fades with clip transitions. Preserve those as separately typed observations when useful. Unlinked transition materials may be unused: do not describe them as applied.

## Text position

For each active text segment capture:

- Role such as Chinese subtitle, English subtitle, hook, title, or label; keep unknown if ambiguous.
- Exact native transform X/Y (often `clip.transform.x` and `.y`), with JSON paths and native coordinate space if established.
- Canvas dimensions/aspect ratio, rotation, scale, anchor/alignment, text box dimensions, font name/ID/size, outline/shadow and timing when available.
- Position-related keyframes, offsets and entrance/exit animations. Animated text has a base position plus motion, not one fixed X/Y.

Do not interpret normalized coordinates as pixels or assume origin, axis direction, or scale. Store raw coordinates even if conventions are unknown; only add converted coordinates when the conversion is verified. Distinguish a missing transform from an explicit zero. If multiple text roles use different positions, remember each separately. Avoid storing full dialogue unnecessarily; a short role label or excerpt is sufficient.

## Persistent record

Use a JSON object with `source`, `audio`, `transitions`, `texts`, and `unresolved` collections. Include the source field paths and raw native values alongside interpreted labels. Each interpreted role or preference carries a status (`observed`, `inferred`, or `user-confirmed`) and supporting evidence. Write atomically and preserve unrelated existing preferences.

In `preferences.md`, record confirmed values or qualified patterns under BGM, SFX, transitions, and text roles. Each entry includes scope (global/style/project), evidence snapshot, and date. User corrections supersede older defaults with a short record of the change. Never promote an agent-generated edit to the user's taste unless the user accepts it.
