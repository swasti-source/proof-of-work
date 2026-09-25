# Swasti Shukla — Proof of Work

Portfolio site. Single `index.html`, no build step, no dependencies.
Live at: https://swasti-source.github.io/proof-of-work/

## Design

Warm parchment and deep plum, Playfair Display for headings (italic for
accents), Manrope for body, JetBrains Mono for labels. Cards use a cusped
"cartouche" silhouette — the concave corners are pure CSS radial-gradient
masks, so they scale to any card size. Light and dark both follow the
visitor's system setting.

## Adding your work

Everything you fill in lives in **one place**: the lists near the bottom of
`index.html`, under the comment `FILL YOUR WORK IN HERE`. Nothing else needs
touching. Any field left as `""` either renders as a labelled slot or is
quietly skipped, so the page always looks finished.

All five lists feed **one Work section** with filter pills. The pills and
their counts build themselves from the data — add an item and the count
updates, empty a whole list and its pill disappears.

| List | Filter pill | What's in it now |
|---|---|---|
| `LONGFORM`   | Long form  | 5 SparX episodes, live |
| `SOCIAL`     | Instagram  | 4 reels + 2 carousels, live |
| `PROGRAMMES` | Campaigns  | Headout, DhyanHQ, DiveIn |
| `CAMPAIGNS`  | Campaigns  | 3 campaign reels, live |
| `ONCAMERA`   | On camera  | 1 YouTube + 2 reels, live |
| `STATS`      | —          | the six-tile numbers grid |
| `MARQUEE`    | —          | the scrolling strip |

### The hero portrait

Save a cut-out photo as **`assets/portrait.png`** and it drops straight into
the frame — no code change. Until then the frame shows a labelled slot.
A transparent PNG works best; roughly 3:4, at least 600px wide.

### YouTube items

```js
{ show:"SparX · Meraki Labs", title:"...", youtubeId:"FPya76YLbKA", metric:"480K views", role:"...", breakdown:{...} }
```

`youtubeId` is the bit after `v=` (or after `youtu.be/`). Set it and the
thumbnail *and* the watch link both appear. If a video has no
`maxresdefault` thumbnail the page falls back to `hqdefault` automatically.

### Instagram items

Reels and carousels share the `SOCIAL` list. `type` is `"reel"` or
`"carousel"` and sets the label. These render as a compact 3-up grid rather
than full-width cards, since there are many of them.

```js
{ type:"reel", show:"SparX", hook:"Counterintuitive stat in frame one.", image:"", link:"https://www.instagram.com/reel/XXXX/" }
```

Instagram serves no thumbnail or caption to logged-out visitors, so these
render as a designed tile — stripes, a big index numeral, a view cue.

- `show` — which show or brand it came from. Optional.
- `hook` — one line on what made someone stop scrolling. This becomes the
  card's title, so it's the highest-value thing to fill in.
- `image` — a real screenshot in `assets/shorts/`. Replaces the tile.

### Strategy breakdowns

```js
breakdown: { "The hook": "Why the first 60 seconds worked.", "Who it was for": "", "What it did": "" }
```

The drawer **only appears once at least one line is filled in**, so
unfinished cards never look broken.

## Publishing changes

```bash
git add -A && git commit -m "Add hooks" && git push
```

GitHub Pages redeploys in about a minute.

## Notes

- The clapperboard intro plays once per browser session, and is skipped
  entirely under reduced-motion. Click, Esc, Enter or Space skips it.
- Instagram links are stored without their `stkn` / `utm` tracking
  parameters — those are tied to your logged-in session.
- The previous dark purple-gold design is in git history
  (`git log -- index.html`) if you ever want it back.
