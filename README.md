# QuestWordHunter — German Voiceover: Words

Single German words, spoken. This is the pack the engine reaches for when you
click a word, rather than when you open a quest.

**It holds nothing yet: 0 clips, 0 hours.** The dictionary is 104,274 entries
and it is last in the generation order, behind the eleven expansions of quest
text. The repository exists ahead of the audio so the pack has somewhere to land
and so `Part.lua` — the file that tells the engine a word pack is installed at
all — is under version control from the start.

Installing it today is harmless and pointless. It registers, the engine asks it
for a word, the file is not there, and nothing plays.

Unlike a quest pack this one declares no range. A word's clip is named by a hash
and there is nothing to compare, so the engine simply takes the one word pack it
finds.

## It does nothing on its own

Everything that decides when to play a clip is in the engine addon,
[QuestWordHunter — German Voiceover](https://github.com/Ironship/WordHunterWoW-Voice-DE).
It is a hard dependency: without it the client will not load this pack at all.

## The audio is not in this repository

`sounds/` is gitignored, and `.gitignore` says why: there is none of it here
yet, and it will be around seven gigabytes across the twelve packs when the
whole corpus has been read, and how that should ship has not been decided. So a
checkout of this repository is not installable by itself — it is the manifest,
the licence and the duration table, and no sound.

The playable pack is assembled by `Tools/build_pack.py` in the engine
repository, which takes these files and adds the clips:

```
python Tools/build_pack.py --only Words --out "…/Interface/AddOns"
```

## Where a clip lives

`sounds\w\<first two hex digits>\<64-bit FNV-1a of the key>.ogg`. The name is
a hash rather than the word because German keys carry umlauts and the eszett,
and a WoW client does not reliably open a file whose path has those in it. The
same hash is computed in `Tools/naming.py` and in `Naming.lua` in the engine
repository, and `tests/naming.test.lua` holds the two to the same answers.

Retail 12.1 (interface 120100) and Classic Era (11509) — one manifest each.
GPL v3, see `LICENSE`. The audio carries CC BY-NC 4.0, which `NOTICE` sets out:
this is given away and may not be sold.
