# Gate Log

A daily check-in tracker for a 24-week airport English study plan. Runs
entirely on your own Mac — no account, no cloud, no server you have to pay
for.

## Open it

Double-click **`Open Gate Log.app`**. It starts a small local backend and
opens the page in your browser. First launch may ask you to confirm it's
okay to run (macOS Gatekeeper) — that's normal for an unsigned app; right‑click
it and choose **Open** once if double‑clicking refuses.

Want it on your Desktop? Drag `Open Gate Log.app` there, or hold ⌘⌥ while
dragging to make an alias — either way it still finds the project folder on
its own.

If double-clicking ever doesn't work, you can start it by hand:

```
cd gate-log
python3 server.py
```

then open http://127.0.0.1:8420 in your browser. (Needs Python 3 — most
Macs have it; if not, run `xcode-select --install` in Terminal.)

## Where your data lives

Every check-in and journal note is written to `gate-log/data.json`, a plain
JSON file right next to `server.py`. That's the real, inspectable file —
not something hidden inside the browser. If the backend isn't running for
some reason, the page still works and falls back to the browser's local
storage until it reconnects.

## Backing up

The page has three buttons at the bottom:

- **导出进度报告** — downloads a Markdown summary of your progress (day/week/
  phase, streak, last 14 days, journal notes). This is the one to send to
  Claude when you want feedback on your real practice — just attach the
  downloaded `.md` file to a message.
- **导出备份** — downloads the full `data.json` as a dated `.json` file, for
  restoring your record if it's ever lost.
- **导入备份** — restores from a previously exported `.json` file.

## Stopping the backend

The launcher starts the server in the background so closing the browser
tab doesn't stop it. To shut it down:

```
pkill -f gate-log/server.py
```
