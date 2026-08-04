# Context — zistgah/kitab

## What this is
The tabdili reader architecture with all book-specific content stripped and replaced
by Lorem Ipsum config. Seeding a new book = editing config, never touching plumbing.

## Layers (decoupled)
- **Data**: config/*.json + content/*.json
- **Presentation**: js/ (engine + shell) + readers/ (three interchangeable formats) + assets/theme
- **Content**: content/*.json, where figures declare themselves (explanation, TTS, seed, 3d/hyper hooks)

## To make a new book
1. Edit config/book.config.json (metadata, chapter manifest, theme tokens)
2. Write content/*.json chapters (copy the Lorem Ipsum ones)
3. Drop figures in assets/figures/
4. Toggle features in config/features.config.json
No code changes required.

## Interfaces / contracts
- A reader module exports `mount(root, chapters, ctx) -> { destroy() }` and reads content only through core.js.
- A figure is a content object with optional `explanation`, `tts`, `seed`, and (for 3d/hyper) `declares`.
- Features are pure client-side or pre-filled GitHub links — no server we run.

Issues are routed with ai:claude / ai:chatgpt / ai:gemini / ai:fable / human-only labels.
