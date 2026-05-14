# Little Fingers — Letters & Numbers

For curious toddlers who wonder what their remote-working parents are doing on the keyboard all day — now they can find out, one letter at a time.

**[Live demo](https://nesicvladimir.github.io/littlefingers/)**

## Features

- **2 alphabet modes** — English ABC (A–Z) and Serbian Cyrillic (А–Ш, 30 letters)
- **Animals or Objects** — toggle between animals and everyday objects (vehicles, toys, food) per mode
- **Keyboard & tap support** — press any key or tap the screen
- **Synthesized sounds** — each letter plays a matching animal or object sound
- **Speech synthesis** — names spoken aloud in the correct language (English or Serbian)
- **Numbers (0–9)** — digit keys show numbers with counting dots and Serbian/English names
- **Progress strip** — bottom dots track which letters have been visited
- **Achievements** — badge system rewards interaction milestones
- **Mouse trail** — colored trail follows the cursor
- **Particle burst** — emoji explosion on every letter change
- **Fullscreen** — auto-requests on first interaction

## Modes

| Mode | How to switch |
|------|---------------|
| English Alphabet (A–Z) | Default |
| Serbian Cyrillic (А–Ш, 30 letters) | Select "Ћирилица" in dropdown |
| Numbers (0–9) with counting dots | Press digit keys in either alphabet mode |

### Animals / Objects toggle

The **🐾 Animals / 🎁 Objects** button (top right, purple) switches between two content sets for every letter:

| | Animals | Objects |
|-|---------|---------|
| **Alphabet** | ALLIGATOR, BEAR… | AIRPLANE, BALLOON… |
| **Ћирилица** | АНТИЛОПА, БИК… | АВИОН, БАЛОН… |

Object names follow the active alphabet language (English in ABC mode, Serbian in Cyrillic mode).

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

- Web Audio API — synthesized sounds (`AC.resume().then(...)` for mobile compatibility)
- SpeechSynthesis API — names spoken aloud (`lang='sr'` in Cyrillic mode)
- localStorage — persists alphabet mode, animals/objects toggle, item rotation state, and interaction count

## Credits

Created by Vladimir Nešić @ [Navira Tech](https://navira.rs)
