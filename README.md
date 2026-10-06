# QuestWordHunter — German Voiceover: Words

**121,904 German word recordings**, including 17,609 clips added from the expanded quest, item, spell and NPC corpus.

This repository keeps the master word audio. The normal download is [German Dictionary](https://github.com/Ironship/WordHunterWoW-Dictionary-DE), which includes these recordings and the reader in one addon. No separate word pack or engine is needed with that dictionary.

The new clips use native German Voxtral voices, primarily `de_female` with `de_male` for some difficult replacements. Each Ogg is decoded and checked by the same German large-v3 recognizer used for the original pack. Defects such as repeated words, filler, long invented sentences and clipped output are queued for another take. Recognition can remain uncertain for unusual names and compounds; automatic checks are not human listening to every clip.

The clip inventory and automatic check results are in `verification/words-20261006.jsonl`, with a summary in `verification/words-20261006.json`. All 17,754 planned new paths were generated and checked. The 145 still unconfirmed clips are withheld and listed in `verification/words-20261006-withheld.json`. They are not included in the download. One new path for the source typo `Díe` reuses the original `die` recording, with its source path and checksum in the inventory. These audit files are excluded from addon packages.

Nine damaged text fragments or opaque rune names added to the dictionary are ignored and excluded from this audio batch. Abbreviations such as `NSC`, `SGS` and `Std.` are read in full German. The original 104,295 recordings are preserved.

## Compatibility pack

The standalone pack still depends on [QuestWordHunter](https://github.com/Ironship/WordHunterWoW) and the [German Voiceover engine](https://github.com/Ironship/WordHunterWoW-Voice-DE). Install either this older arrangement or the bundled German Dictionary: two packs claiming the same word audio have no defined priority.

`sounds/` is committed. `Tools/build_pack.py` in the engine repository builds this compatibility pack; `Tools/build_dictionary_bundle.py` in addon-tools assembles the single-addon dictionary download.

## Clip paths

`sounds/w/<first two hex digits>/<16 hex digits>.ogg`. The filename joins two 32-bit FNV-1a hashes of the UTF-8 key, using the prefix byte `01` for the second hash. `Tools/naming.py` and the engine's `Naming.lua` compute the same path. Keys retain German umlauts and eszett; hashed filenames avoid those characters in client file paths.

GPL v3, see `LICENSE`. Audio is CC BY-NC 4.0, see `NOTICE`; it may not be sold.
