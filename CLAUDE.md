# yt_spoilerless

A minimal Express app that embeds YouTube videos without revealing their duration or progress bar.

## Stack

- Node.js + Express (server)
- Vanilla HTML/CSS/JS (frontend, no build step)
- YouTube IFrame API (video embedding)

## Conventions

- Keep dependencies minimal — no bundlers, no UI frameworks
- Server entry point: `server.js`
- Static assets served from `public/`
- `public/index.html` is the single page; inline CSS and JS are fine given the small scope
- No TypeScript, no transpilation

## Running

```bash
npm install
npm start        # starts on PORT env var or 3000
```

## Key Design Decisions

- YouTube IFrame API `controls: 0` hides the native player chrome (progress bar, duration, play button)
- A custom overlay captures clicks and forwards play/pause to the player, so users can still interact
- `rel: 0` suppresses related-video suggestions; `modestbranding: 1` reduces YouTube branding
- Duration is never exposed in the DOM — no JS reads `getDuration()` and renders it
