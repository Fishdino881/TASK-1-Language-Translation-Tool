## Task 1: Language Translation Tool

**File:** `translator.html`

A single-file, browser-based translation tool called **Polyglot**. Open the file directly in any browser — no install, no build step, no server.

### Features
- Text box for entering source text (up to 4000 characters)
- Source and target language dropdowns (25+ languages, plus **auto-detect** for the source)
- Swap button to flip source ↔ target languages
- Auto-translates as you pause typing, or click **Translate**
- Displays the translated text clearly, with a live character count
- Shows the detected language when using auto-detect
- **Copy button** — copies the translation to your clipboard
- **Text-to-speech** — listen to either the source or translated text, using the browser's built-in Web Speech API (no API key needed)

### How translation works
By default it calls Google Translate's free public web endpoint directly from the browser:

```
https://translate.googleapis.com/translate_a/single?client=gtx&sl=<source>&tl=<target>&dt=t&q=<text>
```

This requires no API key, which makes the demo runnable out of the box. It's fine for testing and light personal use, but it isn't an official, rate-limited, or SLA-backed API — for production use, swap in a real API.

### Switching to an official API
The `fetchTranslation()` function in the `<script>` block is the only place that needs to change. Commented-out examples are included at the bottom of the script for:

- **Google Cloud Translation API** — requires an API key from Google Cloud Console (Cloud Translation API enabled, billing set up).
- **Microsoft Translator (Azure Cognitive Services)** — requires a subscription key and region from the Azure portal.

Both are simple `fetch()` calls with a JSON body; paste your key into the relevant snippet and point `fetchTranslation()` at it.

### Notes
- If the free endpoint is blocked by your network (CORS/firewall), the UI shows a clear in-app error rather than failing silently — you'll then need to switch to an official API key.
- Text-to-speech voice availability depends on what voices your OS/browser has installed for a given language.

---
