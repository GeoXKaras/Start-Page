# Starting Page

A personal browser start page. One file: `index.html` (HTML + CSS + JavaScript together).
No build step, no frameworks, no installs. Open the file in a browser to run it.

## What's on the page
- Greeting, clock and date, plus a quote of the day
- Quick links (grouped; edit the `LINK_GROUPS` list near the top of the script)
- Weather for Thessaloniki (Open-Meteo API)
- Cinema card: now-playing films at Village Cinemas (hand-edited `CINEMA` data)
- Greek news and World news, with tabs per source (RSS feeds)
- Reloads itself after 30 minutes away (on `visibilitychange`)

## How it's built
- Plain "old-style" JavaScript (`var`, `function`), no modules, no libraries. Match this style.
- Settings and data live in lists at the top of the `<script>`: links, feeds, cinema, location.
  Change those lists rather than the rendering code when possible.
- Network calls use `fetchJson` (6 second timeout). News tries rss2json first, then falls
  back to the allorigins relay.
- `localStorage` caches weather and news and remembers the chosen tab. Always wrap it in
  try/catch, and the page must still work if it is blocked.
- Failures must degrade quietly: show a short status message or the cached copy marked as stale.

## Rules for changes
- Keep it a single file unless I agree to split it.
- Don't add libraries, trackers, or new external services without asking.
- No API keys or tokens anywhere. All current services are keyless.
- Keep it accessible: real headings, labelled sections, links open with `rel="noopener noreferrer"`.
- Keep the layout working on a phone-width screen.

## How to test a change
1. In the project folder run: `open index.html` (opens it in the browser).
2. Refresh and check: clock, links, weather, cinema card, both news tabs.
3. Check the browser console for errors (Chrome: Cmd+Option+J).
4. Test offline: turn off Wi-Fi and refresh. Cached data should appear marked as stale.

## Git
- This repo is public: no personal data in any file, including this one.
- Work on a branch, never directly on `main`. Open a pull request to merge.
- Small commits with plain-English messages.
- Before pushing: check nothing private is in the file (personal links, tokens).
