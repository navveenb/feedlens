# FeedLens for LinkedIn

**LinkedIn → FeedLens → Your signal.**

Don't let the algorithm decide what deserves your attention. FeedLens is a personal lens for your LinkedIn feed: two keyword lists, one toggle, and a set of noise filters — all processed 100% on your device.

By [Navveen Balani](https://www.linkedin.com/in/naveenbalani/).

## The model — two lists and a toggle

- **I care about** — keywords for topics that matter to you. Posts matching them are always protected.
- **I don't care about** — keywords for the noise. Posts matching them are hidden.
- **Focus mode** — off: show everything except your don't-cares. On: show **only** posts matching what you care about.
- **Starter packs** — one tap adds a curated keyword set (AI & ML, Sustainability, Cloud & DevOps, Hiring, Crypto, Sales pitches, Buzzwords). Every keyword stays an ordinary, individually removable chip.

One rule to remember: **"I care about" always wins — except ads and AI slop.**

## Features

- **Built-in noise detectors** — one-tap mutes for sponsored posts, engagement bait, polls, hiring posts, motivational spam, crypto, celebration threads, and LinkedIn's own "suggested" filler
- **AI Slop filter (experimental)** — a multi-signal, on-device classifier that scores formulaic, engagement-farmed, likely AI-generated posts (hook patterns, false-contrast openers, emoji walls, low-specificity language). Three sensitivity levels; every hidden post shows its score
- **Filtered-post counter** — a running total of everything FeedLens filtered, expandable into a per-filter breakdown, with reset
- **Collapse or Remove** — hidden posts collapse to a slim bar with the reason and a one-click **Show**, or vanish entirely; nothing is ever deleted
- **Safety net** — if filtering would ever blank your feed, FeedLens auto-pauses and tells you instead of breaking the page; a health sentinel warns if LinkedIn's page structure changes
- **Rule tester** — paste any post text in settings and see exactly what FeedLens would do with it and why
- **Optional hidden-post log** — audit what was hidden, locally
- **Live settings** — every change applies instantly, no page reload

## Privacy

FeedLens is 100% client-side. **Zero network requests** — no servers, no accounts, no analytics, no data collection of any kind. The only permission is `storage` (your settings) plus access to `linkedin.com` (to read and filter the page you're viewing). Full policy: [PRIVACY.md](PRIVACY.md).

## Install

**Chrome Web Store** — coming soon.

**Developer mode (any Chromium browser):**
1. Download or clone this repository
2. Open `chrome://extensions`, turn on **Developer mode** (top right)
3. Click **Load unpacked** and select the extension folder
4. Open linkedin.com, click the FeedLens icon, and set your signal

## Resilient by design

Most LinkedIn extensions hardcode LinkedIn's CSS class names — and break at the next redesign. FeedLens detects posts through three independent layers:

1. **Semantic layer** — accessibility markup LinkedIn can't remove without breaking screen readers
2. **Attribute layer** — LinkedIn's internal `urn:li:activity` content IDs, stable for years
3. **Structural layer** — pure heuristics (avatar + timestamp + body + action row, scored) that need zero LinkedIn-specific knowledge

If a redesign takes out the first two layers, the third keeps working — and if everything fails, the health sentinel says so in the popup rather than failing silently.

## Tested

19 Playwright regression suites run against a real Chromium build, including a 5 MB capture of an actual LinkedIn feed: real-page hiding, precedence rules, the v1→v2 settings migration, safe-mode, the AI Slop classifier, the counter pipeline, and both UIs end-to-end. Run them with `node test/<suite>.js` from the repository root (Playwright + Chromium required).

## Roadmap

- **Learn Mode** — FeedLens will learn your signal from your own corrections (every revealed post is a lesson), fully on-device and suggestion-based. Later tiers: opt-in reading-behavior signals and on-device semantic matching.
- Image provenance signals (C2PA) for the slop filter
- Broader non-English coverage for the noise detectors

## Honest limitations

- Noise-detector patterns are tuned for English; keyword rules work in any language
- LinkedIn changes its page structure regularly; FeedLens is built to survive this, but a redesign can temporarily degrade detection — the popup will tell you
- The AI Slop filter is probabilistic by nature; that's why it's off by default, conservative at "Light", and always shows its score

FeedLens is an independent project and is not affiliated with or endorsed by LinkedIn.

© 2026 Navveen Balani. All rights reserved.
