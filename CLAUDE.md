# Little Fingers — Letters & Numbers

Single-file children's educational app. Everything lives in `index.html` — no build step, no dependencies except Google Fonts.

## What it does
Teaches letters and numbers to toddlers via keyboard/tap. Each letter shows an animal or object with emoji, color, synthesized sound, and speech synthesis. Two alphabet modes: Latin ABC and Serbian Cyrillic АБВ. Digit keys show numbers in either mode.

## Key data structures

- `LETTERS` — A–Z, each with `animals:[{n,e,c,s}]` and `objects:[{n,e,c,s}]` (name, emoji HTML entity, color hex, sound type)
- `CYRILLIC_LETTERS` — А–Ш (30 Serbian Cyrillic letters), same format as LETTERS; object names are in Serbian
- `NUMBERS` — 0–9 with `n` (English), `nc` (Serbian), and counting dot `items`
- `EN_MAP` — keyboard `e.code` → Latin letter/digit
- `SR_MAP` — keyboard `e.code` → Serbian Cyrillic letter (standard Windows Serbian layout)

## Mode system
`currentType`: `'abc'` | `'cyr'` | `'num'`

Dropdown `#mode-select` switches between `'abc'` (Alphabet) and `'cyr'` (Ћирилица). Digit keys trigger number display from either mode.

Keyboard handler reads `mode-select.value` (not `currentType`) to determine language context — this ensures digit presses stay in the right language even after `showNumber` sets `currentType = 'num'`.

## Content toggle
`contentMode`: `'animals'` | `'objects'`

Button `#content-btn` (purple, top right) toggles between animals and objects. Label says "Animals/Objects" in ABC mode, "Životinje/Predmeti" in Cyrillic mode. `updateContentBtn()` syncs the label; called on toggle click and on mode dropdown change.

## Core functions
- `renderLetter(idx, animal, x, y)` — renders a Latin letter with given item (animal or object)
- `renderCyrillic(idx, animal, x, y)` — renders a Cyrillic letter with given item
- `showLetter(letter, x, y)` / `showCyrLetter(letter, x, y)` — lookup + rotate through `contentMode` list
- `showIdx(idx, x, y)` / `showCyrIdx(idx, x, y)` — show by array index, respects `contentMode`
- `showNumber(idx, x, y, lang)` — show a number; `lang='sr'` uses `nc` name and Serbian speech
- `switchMode(mode)` — switches to `'abc'` or `'cyr'`, shows first letter, calls `buildStrip()`
- `updateContentBtn()` — syncs icon and label of `#content-btn` to current `contentMode` and `mode-select`
- `randomShow(x, y)` — random letter from current alphabet mode
- `playSound(type)` — Web Audio API synth sounds via `AC.resume().then(...)` for mobile compatibility
- `speak(name, lang)` — SpeechSynthesis; uses `lang='sr'` when `lang='sr'` or `currentType==='cyr'`
- `buildStrip()` / `updateStrip()` — bottom progress dots; mode-aware (26 Latin / 30 Cyrillic)

## State
- `currentIdx` — index into current letter array
- `currentType` — `'abc'` | `'cyr'` | `'num'`; set by render functions
- `contentMode` — `'animals'` | `'objects'`; persisted to localStorage as `lf_content`
- `animalIdxMap` — per-letter item rotation state, persisted to localStorage as `lf_animals`
- `actionCount` — total interaction count, persisted; drives badge/achievement system

## UX details
- First interaction auto-requests fullscreen
- Hold `#hold-indicator` (gear, top-left) 2s OR hold Escape 1s → opens settings panel
- Settings panel: toggle sound, toggle speech, fullscreen, new session
- Mouse trail effect uses current letter color
- Particle burst on each letter change

## Owner
Created by Vladimir Nešić @ Navira Tech
