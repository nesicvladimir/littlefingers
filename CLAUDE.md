# Little Fingers — Letters & Numbers

Single-file children's educational app. Everything lives in `index.html` — no build step, no dependencies except Google Fonts.

## What it does
Teaches letters and numbers to toddlers via keyboard/tap. Each letter shows an animal with emoji, color, synthesized sound, and speech synthesis. Three modes: Latin ABC, Serbian Cyrillic АБВ, and Numbers 123.

## Key data structures

- `LETTERS` — A–Z, each with multiple `{n, e, c, s}` animals (name, emoji HTML entity, color hex, sound type)
- `CYRILLIC_LETTERS` — А–Ш (30 Serbian Cyrillic letters), same format as LETTERS
- `NUMBERS` — 0–9 with counting dot items
- `EN_MAP` — keyboard `e.code` → Latin letter/digit
- `SR_MAP` — keyboard `e.code` → Serbian Cyrillic letter (standard Windows Serbian layout)

## Mode system
`currentType`: `'abc'` | `'cyr'` | `'num'`

Toggle button `#mode-btn` cycles: ABC → АБВ → 123 → ABC (label always shows *next* mode).

## Core functions
- `renderLetter(idx, animal, x, y)` — renders a Latin letter
- `renderCyrillic(idx, animal, x, y)` — renders a Cyrillic letter
- `showLetter(letter, x, y)` / `showCyrLetter(letter, x, y)` — lookup + rotate animals
- `showIdx(idx, x, y)` / `showCyrIdx(idx, x, y)` — show by array index
- `showNumber(idx, x, y)` — show a number with counting dots
- `switchMode()` — cycles mode, updates button label, calls `buildStrip()`
- `randomShow(x, y)` — random from current mode's letter pool
- `playSound(type)` — Web Audio API synth sounds (meow, bark, roar, hiss, croak, etc.)
- `speak(name)` — SpeechSynthesis; uses `lang='sr'` in Cyrillic mode
- `buildStrip()` / `updateStrip()` — bottom progress dots; mode-aware (26 Latin / 30 Cyrillic)

## State
- `currentIdx` — index into current letter array
- `animalIdxMap` — per-letter animal rotation state, persisted to localStorage
- `actionCount` — total interaction count, persisted; drives badge/achievement system

## UX details
- First interaction auto-requests fullscreen
- Hold `#hold-indicator` (gear, top-left) 2s OR hold Escape 1s → opens settings panel
- Settings panel: toggle sound, toggle speech, fullscreen, new session
- Mouse trail effect uses current letter color
- Particle burst on each letter change

## Owner
Created by Vladimir Nešić @ Navira Tech
