# OblivianOS

A browser desktop shell. Pure HTML/CSS/JS — no build step, no dependencies.

## Run locally

`fetch()` is blocked on `file://`, so serve the folder:

    python3 -m http.server 8000

Then open http://localhost:8000

(Double-clicking `index.html` still works — it just falls back to the
built-in game/wallpaper defaults instead of reading `data/*.json`.)

## Deploy on GitHub Pages

1. Push all files to `main`.
2. Repo → Settings → Pages → Source: `Deploy from a branch` → `main` / `/ (root)`.
3. Live at `https://<user>.github.io/OBLIVIAN-OS/`

## Add a game

Edit `data/games.json` and add an entry:

    { "name": "My Game", "ico": "🎯", "type": "embed", "url": "https://example.com/game/" }

The host must allow framing. GitHub Pages sites, archive.org embeds and
hextris.io all work. YouTube, Roblox, TikTok, Discord and most big sites
send `X-Frame-Options` and will show a blank frame — use the
"Open externally" button for those.

`"type": "inline"` entries call a function baked into `index.html`
(currently only `snake`).

## Add a wallpaper

Edit `data/wallpapers.json`:

    { "id": "mywall", "name": "My Wall", "css": "linear-gradient(...)" }

Or paste a GIF/image URL into Settings → Wallpaper.

## What this cannot do

- 800k / 2.9k real games — no legal source, and most hosts block iframing.
- PS4 emulation — not viable in a browser tab.
- Roblox / `.rbxl` inside the page — needs the Roblox engine.
- Real VPN / unblocking proxy — needs a server (Cloudflare Worker is easiest).
- Cross-device chat and calls — needs a backend (Supabase/Firebase + WebRTC).
- "Every song" — copyright.
