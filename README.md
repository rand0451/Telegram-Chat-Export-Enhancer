# Telegram Chat Export Viewer

Modern, polished viewing layer for exported Telegram HTML chats. This userscript transforms the raw export into a responsive interface with themes, powerful search, favorites, navigation aids, statistics, and ergonomic keyboard shortcuts.

## Highlights

- Dark & light theme switch (T) with smooth transitions
- Search panel with filters: All / Text / Photos / Videos / Voice (`/` to open)
- Inline favorites: hover shows ☆, click to add ⭐, click ⭐ to remove (F to temporarily show only favorites)
- Date navigation: calendar list + N / P to jump between date markers
- Reading mode (R) and Compact mode (C)
- Hide / show all media (M)
- Adjustable font size (+ / -) and instant reset (0)
- Language auto-detect + dropdown inside Help (English / Russian / Ukrainian)
- Statistics modal (S) with message/media counts & period
- Persistent settings via `localStorage`
- Direct open for images and videos (no intermediate preview layer)
- Smooth scrolling, custom scrollbar, subtle animations & hover feedback
- Context menu (right‑click): Copy Text, Select, Copy Link (favorites handled inline)
- Inline selection (multiselect) with counter + clear control
- Help overlay (H) with live language switch
- Accessible focus & visual contrast refinements

## Current Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `/` | Open / focus search |
| `T` | Toggle theme |
| `C` | Toggle compact mode |
| `M` | Hide/show media |
| `R` | Reading mode |
| `+` / `-` | Increase / decrease font size |
| `0` | Reset font size to default (14px) |
| `N` / `P` | Next / previous date marker |
| `S` | Show statistics |
| `H` | Help / shortcuts & language dropdown |
| `F` | Temporarily show only favorites |
| `Home` / `End` | Scroll to top / bottom |
| `Esc` | Close overlays (search, help, date list, etc.) |

## Installation

This script is designed and tested for **Firefox + Greasemonkey** only.

Why not other managers?
- Firefox Greasemonkey provides reliable `file://` execution for local Telegram exports.
- Some Chromium extensions (Tampermonkey / Violentmonkey) may restrict or require extra permission steps for local files; behavior is less consistent for offline usage.

Steps:
1. Install [Firefox](https://www.firefox.com/en-US/?utm_campaign=SET_DEFAULT_BROWSER).
2. Install the [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/) extension.
3. Open Greasemonkey dashboard → New Script → Paste contents of `telegram-chat-enhancer.user.js` (or drag the file to the editor).
4. Save the script.
5. Export a chat from Telegram Desktop in **HTML** format.
6. Open the exported `messages.html` file directly in Firefox (`File → Open File` or drag & drop). The URL will start with `file://`.
7. The enhancer automatically activates when it detects Telegram export markup.

If you later host the export over `http(s)`, update the `@match` line in the userscript header accordingly.

## Favorites

- Hover a message to reveal ☆ (add).
- ⭐ indicates saved favorite (click to remove).
- Press `F` to filter view to favorites for a short period.
- Stored persistently in `localStorage` (`telegram-favorites`).

## Persistent Settings (localStorage)

| Key | Description | Example |
|-----|-------------|---------|
| `telegram-theme` | `light` or `dark` | `dark` |
| `telegram-lang` | `en`, `ru`, `ua` | `en` |
| `telegram-compact` | Compact mode flag | `true` |
| `telegram-hide-media` | Media hidden flag | `false` |
| `telegram-font-size` | Base message font size (px) | `16` |
| `telegram-reading` | Reading mode flag | `false` |
| `telegram-favorites` | JSON array of message IDs | `['message1','message42']` |

Example tweak from console:
```js
localStorage.setItem('telegram-theme', 'dark');
localStorage.setItem('telegram-font-size', '16');
```

## Language

Auto‑detect order:
1. Saved `telegram-lang`
2. Browser `navigator.language`
3. Fallback English

Switch language via the Help (H) modal dropdown without reloading favorites or layout state (page reload performs text substitution).

## Statistics

Press `S` or open via planned UI extension to view:
- Total messages
- Photos / Videos / Voice messages
- Link count
- First & last date

## Context Menu

Right‑click a message to access:
- Copy Text
- Select (multi‑selection)
- Copy Link (deep link with fragment id)

Favorites are now managed inline, not through the context menu.

## Development Notes

- Firefox + Greasemonkey targeted environment.
- Single-file userscript for straightforward installation.
- Styles embedded via `addStyles()` (can be externalized if packaging later).
- Pure vanilla JS / DOM APIs; no dependencies.
- All processing happens locally; no network calls.

### Modifying / Extending
- Add UI buttons for export helpers.
- Introduce tag/label system for messages.
- Integrate quick filter chips near toolbar.
- Persist scroll position across reloads.
- Add optional “jump to first unread” logic.

## Security & Privacy

Runs entirely client-side; no data exfiltration. Review source if required. Data persisted is minimal preference and favorites metadata only.

## Contributing

Issues & PRs welcome. Please:
1. Open an issue for large feature proposals.
2. Keep PRs focused & small.
3. Include before/after screenshots for UI changes.
4. Update documentation sections relevant to your change.

## Roadmap Ideas

- Optional timeline density heatmap
- Inline media carousel
- Per-user message counts & breakdown
- Export subset (date range / favorites only)
- Advanced regex search mode

## License

MIT License. See `LICENSE`.

---
Enjoy a clean reading experience for your Telegram chat history. Feedback & feature suggestions are appreciated!
