# FeedLens for LinkedIn — Privacy Policy

_Last updated: September 24, 2026_

**Summary: FeedLens runs entirely on your device. It collects nothing and transmits nothing.**

## What FeedLens does

FeedLens reads the LinkedIn pages you visit (feed pages by default) inside your own browser in order to hide or collapse posts according to rules you configure. All processing happens locally, in-memory, in your browser. There is no FeedLens server.

## Data stored — all of it on your device or in your own Chrome profile

- **Your settings** — keyword lists ("I care about" / "I don't care about"), noise-detector toggles, Focus mode, AI Slop level, and other preferences — are stored using Chrome's extension storage (`chrome.storage.sync`), which Chrome may sync across your own signed-in profiles. FeedLens never sees, reads back remotely, or transmits this data.
- **Filtered-post counter** — an anonymous tally of how many posts FeedLens hid, broken down by filter type (e.g. "Sponsored: 61"). Stored locally (`chrome.storage.local`); contains counts only, never post content. Resettable from the popup, and cleared by Factory reset.
- **Optional hidden-post log** — off by default. If you enable "Log hidden posts", FeedLens stores short text snippets and LinkedIn post URLs of hidden posts locally so you can audit what was hidden and why. This log never leaves your device and can be cleared at any time from the settings page or by Factory reset.
- **Operational flags** — small local values such as the safety-pause flag (set if filtering would blank your feed) and a page-structure health marker. Local only, cleared by Factory reset.

## What FeedLens does NOT do

- No data is sent to any server. FeedLens makes **zero network requests** — no analytics, telemetry, crash reporting, or tracking of any kind.
- No personal data is collected, sold, or shared.
- No remote code is loaded or executed; every line of code ships inside the extension package.
- No access to your LinkedIn account, messages, or credentials — FeedLens only reads the rendered page you are already viewing.

## Permissions, explained

- `storage` — saves your settings and the local values described above.
- Host access to `linkedin.com` — required to read post text on the LinkedIn pages you view and hide the ones matching your rules. No other websites are accessed.

## Changes

If this policy ever changes, the update will appear in this file with a new date, and any change that touched data handling would be called out in the extension's release notes.

## Contact

Navveen Balani — https://www.linkedin.com/in/naveenbalani/
Questions or concerns: open an issue on this repository.
