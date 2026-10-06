# LockPress

A night lock for Clash Royale, Brawl Stars and YouTube. During set hours, opening one of them jumps to a lock screen. Holding the circle for 10 seconds unlocks that app until the morning.

**Live page:** https://ender500500.github.io/LockPress/

## How it works

1. A Shortcuts automation fires when one of the apps is opened.
2. The shortcut **LockPress Gate** checks whether it's night (22:00–07:30) and whether you've already unlocked tonight. If not, it opens the lock page:
   `https://ender500500.github.io/LockPress/?app=clashroyale&until=07:30`
3. After the 10-second hold, the page runs the shortcut **LockPress Unlock**, which saves the unlock time and opens the app again.

Supported `app` values: `clashroyale`, `brawlstars`, `youtube`. Without `app` (e.g. opened from the Home Screen), the page unlocks everything for the night.

Usage limits are handled by Screen Time → App Limits, not by LockPress.

## Limits

- It's a speed bump, not a hard lock: deleting the Shortcuts automation turns it off.
- iOS may ask "Open in Shortcuts?" after the hold.
