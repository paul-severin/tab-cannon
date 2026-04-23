# tab-cannon

Mobile-first PWA that opens a list of URLs at once on iOS, substituting a search term into each URL.

**Live:** https://paul-severin.github.io/tab-cannon/

## Usage

1. Enter a term (e.g. `claude`).
2. Paste one URL per line; use `{term}` where the term should go:
   ```
   https://www.google.com/search?q={term}
   https://de.wikipedia.org/wiki/{term}
   ```
3. Tap **Alle Öffnen** — all URLs open in new Safari tabs.

## Why a Shortcut?

iOS Safari blocks multiple `window.open()` calls from a single tap (popup blocker, no per-site override). The app delegates opening to an iOS Shortcut via the `shortcuts://` URL scheme, which bypasses the restriction.

### Shortcut setup (one-time)

Create a Shortcut named **`URLs öffnen`** with three actions:

1. Accept **Text** input (Shortcut Details → *Receive from Share Sheet and Run Shortcut*).
2. **Split Text** — input: *Shortcut Input*, separator: *New Lines*.
3. **Open URLs** — input: *Split Text*.

The name is configurable in the app's "Shortcut-Einstellungen" section.

## Install as PWA

Open in Safari → Share → **Add to Home Screen**.

## Dev

Pure static site. To run locally:

```sh
python3 -m http.server 8000 --bind 0.0.0.0
```
