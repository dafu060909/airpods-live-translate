# Live Translate for AirPods (no Apple Intelligence needed)

**[中文](README.md)** · **Live demo:** https://zhai66666-max.github.io/airpods-live-translate/

Apple's Live Translation on AirPods needs Apple Intelligence, which isn't available on China-region iPhones. This single web page rebuilds the pipeline without it:

**iOS speech recognition → DeepSeek streaming translation → system text-to-speech in your ear.**

No jailbreak, no sideloading, no extra hardware: open the page in Safari, paste a DeepSeek API key once, tap **Start**.

## What you need

| | |
|---|---|
| iPhone | iOS 14.5+, Safari (needs `webkitSpeechRecognition`) |
| Earbuds | Any Bluetooth earbuds; AirPods are simply the smoothest |
| DeepSeek API key | https://platform.deepseek.com/ — pay as you go, a conversation costs a few cents |
| Server | Not required. Use the hosted page, or self-host for a server-side key |

## How it works in a conversation

| Mode | Audio output | Result |
|---|---|---|
| **I listen** | AirPods | They speak a foreign language → you hear your language |
| **They listen** | iPhone speaker (switch via Control Center → AirPlay icon) | You speak → the translation is read aloud, with large flipped subtitles facing them |

**No earbuds?** Turn on **Phone-only mode** in settings: the iPhone mic listens and the speaker plays, with half duplex and echo guard switched on automatically. Disconnect Bluetooth earbuds first — while they are connected, iOS only uses their mic.

Typical latency is **1–1.5 s** after a pause. "Early translate" starts on comma-level pauses so long sentences don't wait to finish.

## Built for real conversations

- **Double-tap anywhere** on the subtitles to switch who is speaking — handy when the phone lies upside-down between you.
- **Push-to-talk** (Settings): hold the big button to speak, release to translate. Steadier in noisy places and for turn-taking.
- **Phrase cards** (💬, top right): pre-translate key lines (restroom, allergies, hotel address) and show them full-screen even **offline**.
- Requests time out (9 s first byte, 7 s idle) and retry once; a half-finished translation is kept if the network drops.

## Must-knows

- Open it **in Safari**, not as a Home Screen app — iOS disables speech recognition in standalone web apps.
- **Siri must be on** (Settings → Siri & Search), or recognition fails.
- If it goes silent after reading one sentence, switch **Full duplex → Half duplex** in settings.
- In static mode the key lives in this browser only. Turn off **Remember key** to keep it for the current tab only, or self-host with `server.js` so the phone never sees the key.

## Run it

1. **Hosted (10 s):** open the demo link above.
2. **Mac local:** double-click `start.command`.
3. **Temporary HTTPS:** `./tunnel.command` (needs `cloudflared`).
4. **Your own server:** `bash deploy.sh --domain your.domain` — see `DEPLOY.md`.

## Limits

Not a native app, can't give each side their own language simultaneously, needs a network connection. AirPods mics are beamed at your mouth, so stand close to the other person.

MIT License.
