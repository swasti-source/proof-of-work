# Swasti Shukla — Proof of Work

Portfolio site. Single `index.html`, no build step, no dependencies.
Live at: https://swasti-source.github.io/proof-of-work/

## Adding your work

Everything you fill in lives in **one place**: the lists near the bottom of
`index.html`, under the comment `FILL YOUR WORK IN HERE`. Nothing else needs
touching. Any field left as `""` either renders as a labelled slot or is
quietly skipped, so the page always looks finished while you fill it in.

| List | Section on the page | What's in it now |
|---|---|---|
| `LONGFORM`   | 01 — Long Form  | 5 SparX episodes, live |
| `SOCIAL`     | 02 — Instagram  | 4 reels + 2 carousels, live |
| `PROGRAMMES` | 03 — Campaigns  | Headout, DhyanHQ, DiveIn |
| `CAMPAIGNS`  | 03 — Campaigns  | 3 campaign reels, live |
| `ONCAMERA`   | 04 — On Camera  | 1 YouTube + 2 reels, live |
| `STATS`      | The Reel        | the six-tile numbers grid |
| `MARQUEE`    | scrolling strip | brands and skills |

### YouTube items

```js
{ show:"SparX · Meraki Labs", title:"...", youtubeId:"FPya76YLbKA", metric:"480K views", role:"...", breakdown:{...} }
```

`youtubeId` is the bit after `v=` (or after `youtu.be/`). Set it and the
thumbnail *and* the watch link both appear — no image file needed. If a video
has no `maxresdefault` thumbnail the page falls back to `hqdefault`
automatically.

### Instagram items

Reels and carousels live together in one `SOCIAL` list. `type` is `"reel"` or
`"carousel"` and only changes the label on the tile — every card renders at the
same 4:5 ratio so the grid stays even.

```js
{ type:"reel", show:"SparX", hook:"Counterintuitive stat in frame one.", image:"", link:"https://www.instagram.com/reel/XXXX/" }
```

Instagram does not expose thumbnails or captions to anyone who isn't logged in,
so these cards render as a **designed tile** — clapperboard stripes, a big index
number, and a "View on Instagram" cue — instead of a preview image.

Three optional fields:

- `show` — which show or brand it came from (SparX, DhyanHQ...). Shown before
  the type: "SparX · Instagram · Reel". Leave `""` and it just reads
  "Instagram · Reel".
- `hook` — one line on what made someone stop scrolling. Appears on the tile
  and under the card, and fills out the middle of the tile nicely.
- `image` — a real screenshot. Save it into `assets/shorts/` and set
  `image: "assets/shorts/01.jpg"`. The screenshot replaces the tile.

### Strategy breakdowns

Every card can carry a `breakdown` drawer:

```js
breakdown: { "The hook": "Why the first 60 seconds worked.", "Who it was for": "", "What it did": "" }
```

The drawer **only appears once at least one line is filled in** — empty ones
stay hidden, so unfinished cards never look broken.

## Publishing changes

```bash
git add -A && git commit -m "Add hooks to the reels" && git push
```

GitHub Pages redeploys in about a minute.

## Notes

- The clapperboard intro plays once per browser session, and is skipped
  entirely for anyone with reduced motion turned on. Click, Esc, Enter or
  Space skips it.
- Light and dark mode both follow the visitor's system setting.
- Instagram share links were saved without their `stkn` / `utm` tracking
  parameters — those are tied to your own logged-in session and don't belong
  in a public page.
