# OSVcopy Spec

This file is the canonical statement of what OSVcopy is supposed to be.  
Keep it durable. Do not use it as a changelog, inbox, or weekly narrative.

- **Project:** OSVcopy
- **Canonical repo:** https://github.com/devuterian/OSVcopy
- **Project id:** `osvcopy`
- **Operator:** repository maintainers (see GitHub owners)
- **Last updated:** 2026-05-02
- **Related decisions:** (none filed yet)

## Project thesis

Give **DJI Osmo 360** and **Insta360 X series** (and similar) users a **native macOS** way to **import and file** footage and stills by **capture date** into predictable library folders, without replacing Lightroom or manufacturer desktop apps.

## Primary user context

Photographers and videographers who keep a **disk or NAS library** (often SMB) and want **YYYY-MM-DD** (or nested `YYYY/YYYY-MM-DD`) layout, with **safe dedupe** when the same file appears again.

## Core capabilities

- Recursive discovery of media under dropped paths or folders.
- Date resolution: filename patterns → optional `ffprobe` metadata → file timestamps.
- Copy or move into user-chosen **library root** with chosen folder layout.
- Skip duplicates when an existing file has the **same MD5** as the source.
- Progress in UI and Dock; optional completion notification.

## Invariants

- **User-chosen destination** is explicit; the app does not silently pick a cloud or system folder.
- **Destructive operations** (move, overwrite policy) must remain visible in the UI and documented in `README.md`.
- **No network upload** to third parties as part of core product behavior.

## Non-goals

- RAW development, timeline editing, or catalog database replacement (not Lightroom).
- Windows / Linux ports (macOS-only unless explicitly replanned).

## Main surfaces

- SwiftUI app target `OSVcopy` in SwiftPM package.
- Release distribution: signed/notarized is aspirational; current releases are unsigned `.dmg` as documented.

## Success criteria

- Reliable import for **`.OSV`** and **`.INSV`** alongside common image/video types.
- Predictable folder output and **clear operator feedback** on skips and errors.
