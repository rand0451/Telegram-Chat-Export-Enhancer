# Telegram Chat Export Enhancer

Beautiful Telegram-like formatting for exported Telegram chats. This userscript adds a modern, responsive UI around Telegram HTML exports with dark/light themes, animations, search and filters, keyboard shortcuts, image viewer, exports (JSON/TXT/HTML), favorites, reading mode, and more.

This repository contains the userscript `telegram-chat-enhancer.user.js`, documentation, issue and PR templates, and contributing guidelines.

## Features

- Modern dark & light themes with CSS variables
- Search with filters (text, photos, videos, voice)
- Date navigation and quick jump to service messages (dates)
- Image viewer with zoom/close
- Lazy-loading images for performance
- Compact & reading modes
- Toggle media visibility
- Keyboard shortcuts (quick search, theme toggle, stats, export, etc.)
- Export messages to JSON / TXT / HTML
- Context menu (copy text, copy link, reply/forward simulation, favorites)
- Localized UI: English, Russian, Ukrainian
- Persistent settings via `localStorage` (theme, language, compact, font size, favorites)
- Simple message statistics modal
- Basic accessibility improvements and responsive layout

## Installation

Prerequisites:
- A browser [Firefox](https://www.firefox.com/en-US/?utm_campaign=SET_DEFAULT_BROWSER)
- [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/) extension

Install:
1. Save the userscript file `telegram-chat-enhancer.user.js` from this repository.
2. Open your userscript manager and create a new script, or import the file.
3. Open the Telegram export HTML file (File → Open File, or drag it to the browser).
4. The script runs automatically when the page is detected as a Telegram export.

Notes:
- The userscript uses `file:///*` @match so it will run on local files. If you host your export on `http(s)`, update the `@match` accordingly.
- If the script doesn't run, open the browser console to check for errors.

## Quick Start / Usage

- Toggle theme: click the moon/sun button (top-right) or press `T`.
- Search: press `/` or click the magnifier button. Type at least two characters to search.
- Filters: All / Text / Photos / Videos / Voice inside the Search panel.
- Compact mode: press `C`.
- Hide/show media: press `M`.
- Adjust font size: `+` / `-`.
- Date navigation: open the calendar list (📅) or press `N` / `P` to move between service-date markers.
- Export:
  - `E` — export to JSON (structured)
  - Export to TXT and HTML are available via functions in the context (or can be extended to be buttons)
- Reading mode: `R` — simplify layout for reading (hides avatars/headers).
- Favorites: right-click on a message and choose "⭐ Add to Favorites". Press `F` to show favorites temporarily.

## Keyboard Shortcuts

- `/` — Open search
- `T` — Toggle theme
- `C` — Toggle compact mode
- `M` — Hide/show media
- `+` / `-` — Increase / decrease font size
- `N` / `P` — Next / previous date marker
- `S` — Show statistics
- `E` — Export to JSON
- `H` — Show keyboard help
- `R` — Reading mode
- `F` — Show favorites
- `Home` / `End` — Scroll to top / bottom
- `Esc` — Close overlays

## Configuration & Persistence

The script stores several settings in `localStorage`:

- `telegram-theme` — "light" (default) or "dark"
- `telegram-lang` — "en", "ru", or "ua"
- `telegram-compact` — "true" / "false"
- `telegram-hide-media` — "true" / "false"
- `telegram-font-size` — integer px (default `14`)
- `telegram-reading` — "true" / "false"
- `telegram-favorites` — JSON array of message IDs

You can tweak these values using the browser console or by exposing UI to modify them.

Example (in browser console)
```js
localStorage.setItem('telegram-theme', 'dark');
localStorage.setItem('telegram-font-size', '16');
```

## Translations

Built-in translations:
- English (`en`)
- Russian (`ru`)
- Ukrainian (`ua`)

Language detection order:
1. Saved `telegram-lang` localStorage value
2. Browser language (`navigator.language`)
3. Default to English

Change language temporarily from the keyboard help dialog.

## Development

- The script is a single-file userscript (`telegram-chat-enhancer.user.js`).
- To modify styles, edit the CSS inside the `addStyles()` function or replace with an external stylesheet when packaging the script.
- To test fast edits:
  1. Save the script locally and re-import/update in Tampermonkey.
  2. Reload the Telegram export HTML.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines. Contributions are welcome: bug reports, feature requests, pull requests.

Please follow these guidelines:
- Open an issue first for significant changes or features.
- Keep PRs small and focused.
- Document changes in CHANGELOG.md for releases.

## Security

This script runs locally in your browser and reads the Telegram export HTML. It stores only lightweight settings and favorites in `localStorage`. It does not send data to external servers. Review the code before use if you have any security concerns.

If you discover a security vulnerability, please open an issue and mark it as "security".

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for release notes.

---

If you'd like, I can:
- Create a GitHub repository skeleton (with files committed).
- Add a small demo HTML export with sample messages for visual testing.
- Create packaged releases (zip) for easy installation.
