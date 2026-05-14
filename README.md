# Little Fingers — Letters & Numbers

An interactive educational app for toddlers to learn the alphabet and numbers through colorful animals, sounds, and speech.

**[Live demo](https://nesicvladimir.github.io/littlefingers/)**

## Features

- **3 learning modes** — English ABC, Serbian Cyrillic (АБВ), and Numbers (0–9)
- **Keyboard & tap support** — press any key or tap the screen
- **Synthesized animal sounds** — each letter/number plays a matching sound
- **Speech synthesis** — names are spoken aloud in the correct language
- **Counting dots** — numbers show the matching count of emoji items
- **Progress strip** — bottom dots track which letters have been visited
- **Achievements** — badge system rewards interaction milestones
- **Mouse trail** — colored trail follows the cursor
- **Particle burst** — emoji explosion on every letter change
- **Fullscreen** — auto-requests on first interaction

## Modes

| Mode | Switch to |
|------|-----------|
| English Alphabet (A–Z) | Default |
| Serbian Cyrillic (А–Ш, 30 letters) | Select "Ћирилица" in dropdown |
| Numbers (0–9) with counting dots | Press digit keys in either mode |

## Usage

Open `index.html` in any modern browser — no build step, no dependencies (except Google Fonts loaded from CDN).

### Keyboard
- **Letter/digit keys** — show the matching letter or number
- **Any other key** — advance to the next item
- **Hold Escape (1s)** — open settings panel

### Touch / Mouse
- **Tap / click** anywhere — advance to the next item
- **Hold gear icon (top-left, 2s)** — open settings panel

## Settings panel

- Toggle animal sounds on/off
- Toggle voice speech on/off
- Enter fullscreen
- Start a new session (resets counter)

## Tech

Single HTML file. No framework, no build tool.

- Web Audio API — synthesized animal sounds
- SpeechSynthesis API — letter/number names spoken aloud (`lang='sr'` in Cyrillic mode)
- localStorage — persists mode selection, animal rotation state, and interaction count

## Credits

Created by Vladimir Nešić @ [Navira Tech](https://navira.rs)
