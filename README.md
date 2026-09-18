# Sacred Rainbow Nation Songs of Light, Peace and Love

Melody reconstruction for the most-sung songs of the Rainbow Gathering song
circles — part of [A World Made of Rainbows](https://sites.google.com/view/aworldmadeofrainbows).

**Live site:** https://mendicott.github.io/songsite/

The songbooks passed hand to hand at Gatherings preserve the words and chords;
the melodies are the endangered part. Each page here carries a song's staff
notation, rendered live in the browser from a MusicXML file, with playback,
lyrics, chords, and provenance notes.

## Layout

- `data/<slug>/` — the source of truth for each song: `song.json` (metadata,
  provenance), `lyrics.txt`, and either `melody.spec.json` (a hand-encoded
  melody spec) or `melody.musicxml` directly.
- `<slug>/` folders at the root — the generated site pages. **Build output;
  never edit by hand.** Each contains `index.html`, `melody.musicxml`,
  `melody.mid`.
- `index.html` — the generated song index (Core 50 + extended 51–100).
- `assets/opensheetmusicdisplay.min.js` — the notation renderer
  ([OpenSheetMusicDisplay](https://opensheetmusicdisplay.org/) 1.8.4, BSD-3),
  vendored so the site has no external code dependencies.

## Rebuilding

The generator lives in the companion repo
[song2xml](https://github.com/mendicott/song2xml) (`sitegen/`). From this
repo's root:

```
python ../song2xml/sitegen/encode.py            # melody.spec.json -> MusicXML/MIDI
python ../song2xml/sitegen/build.py --out .     # data/ -> site pages
```

The site is served by GitHub Pages straight from the root of `main` — there is
no build service, workflow, or domain to maintain. Correcting a melody means
editing its file under `data/`, rebuilding, and pushing.

## Status

Pages marked *draft* await verification against the source songbooks and
recordings. Song-level provenance is on each page.
