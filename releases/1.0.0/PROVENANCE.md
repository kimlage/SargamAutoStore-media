# Gameplay capture provenance — 1.0.0

Recorded September 25, 2026 in Valheim 1.0.15 on macOS with the actual SargamAutoStore 1.0.0 production DLLs. Local singleplayer QA world and character; no other gameplay mods. A private helper prepared native floor pieces, 32 native player-built chests and native item fixtures. It supplied the fixed camera and English chapter overlay. The helper is excluded from the distributed mod.

Ground collection used the production automatic scheduler. Inventory collection invoked the same production `StoreInventory(false)` entry point behind F9 and `/sas inventory`, with the native inventory UI visible. This does not prove a synthetic F9 keypress. No transfer animation, receipt glow or disappearing item was painted in. The green highlights are the mod's real native material effect.

## Quantities

- Ground: 32 types × 3 units = **96 units**. Each seeded chest rose from 1 to 4 units of its assigned exact type. At least 28 concurrent receipt effects were recorded during the transfer verification.
- Inventory: 24 types × 5 units = **120 units**. Those 24 chests rose from 1 to 6; the other eight remained at 1. A hammer and two cooked-meat units remained in the protected hotbar.
- Every destination was read independently from native in-memory inventory and its serialized ZDO payload. Counts and item types agreed. This checks the saved payload in-session, not a save/reload or multiplayer cycle.

The 32 types were Wood, FineWood, RoundLog, ElderBark, Stone, Flint, Coal, Resin, Amber, AmberPearl, Ruby, Coins, Feathers, LeatherScraps, DeerHide, BoneFragments, TrollHide, WolfPelt, LoxPelt, ScaleHide, Chitin, Obsidian, Crystal, CopperOre, TinOre, IronScrap, SilverOre, BlackMetalScrap, Copper, Tin, Iron and Bronze. Inventory uses the first 24. These selected fixtures are not all-prefab validation.

## Presentation

Ground footage preserves the full game frame. Inventory footage places two crops from each same frame side by side: native inventory at left, visible receiving chests at right. The crafting panel, chapter text and central fixture-notification area are outside those crops. Fixture-generated items can cause native dev-item achievement notices; the private setup is not ordinary player loot.

The camera used a temporary cloned postprocessing profile with bloom, depth of field, motion blur and chromatic aberration disabled for readability. Cleanup restored the original profile without writing player graphics preferences. The staged ranges were 32 m for chests and 64 m for ground activity, with signs disabled. Normal 24 entries/frame, 1.5 ms cooperative budget and 1.5-second highlight duration remained in place.

Source screenshots were requested at up to 10 Hz; actual recorded timestamps determine playback. The ground sequence spans about 6.30 seconds and the inventory sequence 9.40 seconds, plus a final 0.15-second frame hold. GIFs are reduced to 800 pixels wide and 6 fps; MP4s use 1280-pixel width and repeated frames at 30 fps. They are not 30-fps game-performance measurements. Encoding preserves elapsed time, apart from normal frame quantization and the final hold; no acceleration or hidden time cuts occur within a chapter. The preparation gap between chapters is omitted because they are separate clips.

[Ground timestamps](ground-capture-times.csv) · [Inventory timestamps](inventory-capture-times.csv) · [Separate benchmark](BENCHMARK.md)

Fixtures were removed; the QA world/character backups and original active mod profile were restored. Raw logs, save files, inventory backups and game binaries are private. Valheim imagery belongs to its respective rights holders.
