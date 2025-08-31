# kids blockz — block coding for all ages

**kids blockz** is a single‑file, zero‑dependency block‑coding playground with 25 mission‑style lessons.
It runs entirely in the browser—no accounts, servers, or build steps needed.

![screenshot](docs/screenshot-hero.png)

## Features

- 🧱 Drag‑and‑drop blocks (motion, looks, control) with nested loops
- ▶️ One‑click **Run/Stop** with a simple interpreter
- ⌨️ Arrow‑key controls always enabled on the stage
- 🎯 Goals with lightweight auto‑checking for each mission
- 🧰 Starter examples (Starter, Draw Star, Dance)
- 🧪 Works offline, no frameworks

## Quick start

1. **Download** this repo or clone it.
2. Open `index.html` in any modern browser.

That’s it. You’re running kids blockz.

### Serve locally (optional)

Any static server works; for example with Python:

```bash
python3 -m http.server 8080
# visit http://localhost:8080
```

## Deploy to GitHub Pages

1. Create a new GitHub repo and push these files.
2. In your repo: **Settings → Pages → Deploy from branch**.
3. Select the `main` branch and root (`/`). Save.
4. Your site will appear at `https://<username>.github.io/<repo>/`.

## How it works

See **docs/HOW_IT_WORKS.md** for a deep-dive on:
- Block palette → workspace serialization
- The tiny interpreter (Runner) and trace
- Missions/Goals and auto-checkers
- Keyboard input and rendering

## Contributing

Bug reports, ideas, and PRs welcome. Please read **CONTRIBUTING.md** and **CODE_OF_CONDUCT.md**.

## License

MIT — see **LICENSE**.