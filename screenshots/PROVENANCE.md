# Gameplay capture provenance

Captured on 24 September 2026 with SargamAutoStore **0.2.8**, Valheim **1.0.15**,
Unity **6000.0.75f1** and BepInEx **5.4.23.5**, on macOS.

These are authentic game-rendered images from a staged local singleplayer set.
A private QA helper created native wooden chests, signs and dropped items, set
clear daylight and fixed the camera. Bloom, depth of field, motion blur and
chromatic aberration were temporarily disabled for legibility. The normal
production mod scheduler performed the transfers; the helper did not move items
into destinations. Normal routing ranges, drop delay and highlight duration
were used. The final chest was designated during fixture setup; this sequence
is not a demonstration of pressing Alt+N.

| Item | Added from the ground | Destination | Before → after |
| --- | ---: | --- | --- |
| Wood | 7 | Existing type | 40 → 47 |
| FineWood | 8 | Existing type | 20 → 28 |
| TinOre | 6 | Matching ORE sign | 0 → 6 |
| BombOoze | 5 | Designated new-item chest | 0 → 5 |

The helper checked each resulting chest total both in native inventory and in
an independently loaded native saved-inventory payload (ZDO).

- PNG files are unretouched 1920×1080 screenshots.
- `automatic-routing.gif` is an **edited image sequence**, resized and palette
  encoded for the page. Selected drop frames are held for 0.25 seconds and
  feedback frames for 2.75 seconds. It is not real-time footage or a speed/FPS
  benchmark. Glow and transfer messages are the real mod's effects.
- This demonstrates these four items in local singleplayer, not every item,
  the inventory shortcut, a full regression suite, or multiplayer compatibility.

The header banner and logo are original AI-assisted promotional illustrations,
not gameplay images. Valheim imagery belongs to its respective rights holders.
No game binaries, private source, player saves or raw diagnostic logs are hosted
here. See `assets.json` for exported file hashes.
