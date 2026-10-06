# LockPress

A night lock for Clash Royale, Brawl Stars, Instagram, Brave, Snapchat and Reddit. During your set hours, opening one of them jumps to a lock screen. Holding the circle unlocks that app for a while.

**Settings page:** https://ender500500.github.io/LockPress/ (add it to your Home Screen)

## How it works

- **Settings page** (no URL parameters): lock hours, hold duration, how long an unlock lasts, and which apps are locked. "Save to Shortcuts" runs **LockPress Save**, which writes them to `LockPress/settings.json` in the Shortcuts iCloud folder.
- **LockPress Gate** (run by one automation per app): reads `settings.json`, checks the app is enabled, the time is inside the lock hours and there's no active unlock. If it should lock, it opens
  `https://ender500500.github.io/LockPress/?app=<app>&cfg=<url-encoded settings.json>`
- **Lock page**: hold the circle; then it runs **LockPress Unlock** with `{"app": "...", "until": "yyyyMMddHHmm"}`.
- **LockPress Unlock**: saves `until` to `LockPress/unlocked.txt` and opens the app again.

### settings.json

```json
{"from":"22:00","to":"07:30","start":1320,"length":570,"hold":10,"unlockMinutes":0,"clashroyale":1,"brawlstars":1,"instagram":1,"brave":1,"snapchat":1,"reddit":1}
```

`start` = lock start in minutes after midnight, `length` = lock length in minutes. The Gate locks when `(minutes since midnight + 1440 − start) mod 1440 < length`. `unlockMinutes` 0 means "rest of the night".

App keys: `clashroyale`, `brawlstars`, `instagram`, `brave`, `snapchat`, `reddit`. To add an app: add it to `APPS` in `index.html`, add a branch to LockPress Unlock, and create its automation. Usage limits are handled by Screen Time → App Limits.

## Limits

- It's a speed bump, not a hard lock: deleting the automations turns it off.
- iOS may ask "Open in Shortcuts?" after the hold and when saving settings.
