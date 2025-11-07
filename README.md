# The Obsidian Protocol — Frontend-Only Site

A single-file, cyberpunk recruitment terminal inspired by John Wick and The Matrix. The page blends neon UI, glitch effects, ambient audio, and game-like interactions (interrogation, role reveal, ID badge, armory, missions, and an in-page terminal).

> File: final.html

---

## Quick Start

1. **Open final.html in any modern desktop browser.**
2. Click *INITIATE* to start the recruitment flow.
3. Use the *navigation dots* on the right to jump between sections.
4. Toggle *sound* with the circular ♪ button (bottom-right).
5. Press **~ (tilde)** to open the *in-page terminal. Press **Esc* to close.

> No build step is required. Everything is inline (HTML, CSS, JS).

---

## Features

### Cinematic background
- *Matrix rain* and *particle field* rendered on <canvas> with color/behavior that adapts to the active section.
- *Global glitch* pulses, scanlines, and a gold gangster overlay for the noir vibe.

### Interactive flow
- *AI Interrogation*: multiple-choice prompts, “trap” answers, escalating warnings, and a fail-reset sequence.
- *Role reveal: animated stats for **STEALTH, **TECH, **FORCE, followed by a **Generate Digital ID* button.
- *Digital ID: draws a badge to canvas with role name, serial number, QR placeholder, and **Download* as PNG.
- *Blood Contract: “SIGN CONTRACT” triggers SFX + glitch, then routes to **Armory*.
- *Armory*: 3D-flip weapon cards with front/back details.
- *Missions*: dynamic grid of flip cards generated from a JS array.
- *Lore*: staged text reveals and leader cards.
- *Terminal*: press ~ to open; supports commands: help, profile, missions, reset, clear, lore, exit, and the easter egg neo.

### Audio
- Lightweight Web Audio *synth SFX* (glitch/click/gun/ambient) guarded by a *sound toggle*. No external audio files.

### Typography & Icons
- Google Fonts: *Orbitron, **Share Tech Mono, **Rajdhani*.
- *Font Awesome* (CDN) for icons.

---

## Sections (IDs)

- #landing — title + start button  
- #interrogation — chat container + dynamic options  
- #role — role card + animated stats + “Generate Digital ID”  
- #badge — canvas badge + download button  
- #contract — blood contract + sign button  
- #weapons — armory showcase (flip cards)  
- #missions — dynamic mission board  
- #roles — (preview grid prepared; can be filled programmatically)  
- #lore — story + division leaders  
- #terminal — overlaid in-page terminal (opens with ~)  

---

## Controls & Commands

- *Navigation dots*: Right side of the screen. Click to jump between sections.
- *Sound toggle* (♪): Bottom-right. Starts/stops ambient audio and enables other SFX.
- *Keyboard*:
  - ~: Open terminal
  - Esc: Close terminal

*Terminal commands*:
- help — list commands
- profile — show current role and stats (after completing interrogation)
- missions — prints a message (mission grid is already visible in the Missions section)
- reset — full page reload confirmation
- clear — clears terminal output
- lore — shows a short lore line
- exit — closes the terminal
- neo — easter egg; forces a special role assignment and jumps to Role

---

## File Structure

This project is intentionally *single-file*. All styles and logic are embedded in final.html so it’s easy to drop into any static host. You can split it later if you prefer:


final.html
└─ (inline) CSS variables, animations, and component styles
└─ (inline) JavaScript: background renderers, flow controller, terminal, SFX, and generators


---

## Customization Guide

### Colors
Edit the CSS variables in :root:

css
:root {
  --bg-dark: #050507;
  --neon-cyan: #00E5FF;
  --blood-red: #FF2E3B;
  --neon-purple: #B026FF;
  /* ... */
}


### Fonts & icons
- Replace or add Google Fonts in the <head> link.
- Swap Font Awesome with your preferred icon set, or replace <i class="fas fa-..."> with inline SVGs.

### Interrogation & roles
- Update the interrogation logic, warnings, trap answers, and role mapping in the JS section. You can add more questions, modify scoring, or change role names/descriptions.

### Missions
- Edit the missions array in JS to change targets, rewards, statuses, and details. Add more cards or attach a click handler to “ACCEPT MISSION”.

### Badge design
- Tweak the canvas drawing routine (title, role, serial, QR placeholder, security text). You can add an actual QR generator or embed logos.

### Section order & navigation
- Reorder the <section> blocks and ensure the *nav dots* data-section attributes match the section IDs.
- The background color of *matrix code* and *particle field* are keyed off the current sectionId. Update the switch statements in the JS if you rename or add sections.

---

## External Dependencies

- *Google Fonts* (CDN)
- *Font Awesome* (CDN)

If you need an *offline* build, self-host the fonts and icons, or remove them and rely on system fonts and inline SVGs.

---

## Browser Support

- Modern Chromium, Firefox, and Safari on desktop.
- Mobile renders are supported with responsive rules, though the *terminal* and some hover/flip effects are best on desktop.

---

## Roadmap Ideas (Optional)

- Persist interrogation state and role in localStorage.
- Expand terminal: list/accept missions; export logs; command history.
- Replace QR placeholder with a real code that encodes the role + serial.
- Add accessibility tweaks (reduced motion toggle, improved contrast for scanlines/glitch).

---

## License

Personal/portfolio use allowed. If you intend to publish commercially, ensure you have the right to use any names or references and replace them as needed.
