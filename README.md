# Sargam Practice

A tiny, phone-friendly web app for Hindustani sargam practice — one note at a time.

Pick a shuddha swara (Sa Re Ga Ma Pa Dha Ni Ṡa), listen to a reference tone, then sing
the note back into your microphone. The app detects your pitch in real time and shows
how far you are from the target in cents (flat ← in tune → sharp), with a plain verdict
when you hold the note steady. A hold-time streak tracker rewards holding a note in
tune: 3 seconds or more counts as a successful hold, with best-per-note and
best-overall times for the session.

**Live app:** https://jailad.github.io/sargam-practice/

## Using it

- Works in any modern mobile or desktop browser. Microphone access requires a secure
  (HTTPS) page and your permission — on Android, Chrome is recommended, as in-app
  browsers inside other apps often cannot hand a microphone to a web page at all.
- On Android Chrome you can add it to your home screen (⋮ → Add to Home screen /
  Install app) and it will open full-screen like a native app.
- Sa defaults to **G** and can be changed in Settings (all 12 choices). Every other
  swara is derived from Sa using just-intonation (Hindustani) ratios, labelled in the
  app; equal temperament is the alternative tuning and is not used here.
- Streaks and bests are **session-only**: nothing is recorded, stored, or sent
  anywhere. Reloading the page resets them.

## Honest note about the reference "voice"

The reference tone is **not** a recording of a person. It is a synthesized voice-like
tone (harmonic source + formant filtering shaped like the vowel "aa" + slight
vibrato) generated with the Web Audio API. The male/female toggle changes the base
pitch and formant placement. Real recorded reference voices are a possible future
enhancement.

## Scope (v1)

One octave, shuddha (natural) notes only. No komal/tivra notes, no alankars, no
accounts, no saved history, no analytics, no network calls. Everything runs locally
in your browser; the microphone stream is analysed on-device and never leaves it.

## Run it locally

It is a single static page — no build step:

```sh
# any static server works, e.g.
python3 -m http.server 8000
# then open http://localhost:8000/  (mic works on localhost; on a phone use the Pages URL)
```

Or simply open the hosted version above.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (UI, synthesis, pitch detection) |
| `manifest.webmanifest` | Installable web-app manifest |
| `sw.js` | Service worker (offline cache for the app shell) |
| `icon.svg` | App icon |

## License

MIT — see [LICENSE](LICENSE).
