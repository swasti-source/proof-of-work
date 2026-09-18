# Swasti Shukla — Proof of Work

Portfolio site. Single `index.html`, no build step, no dependencies.
Live at: https://swasti-source.github.io/proof-of-work/

## Adding your work

Everything you fill in lives in **one place**: the lists near the bottom of
`index.html`, under the comment `FILL YOUR WORK IN HERE`. Nothing else needs
touching. Any field left as `""` renders as a labelled empty slot, so the page
always looks finished while you fill it in over time.

### Long-form episodes — `LONGFORM`

```js
{
  show: "SparX · Meraki Labs",
  title: "Building India's First Private Space Company",
  youtubeId: "J9bzeHdNpDI",     // just the bit after "v=" in the URL
  metric: "480K views",
  role: "What you owned on this one.",
  breakdown: {
    "The hook": "Why the first 60 seconds worked.",
    "Who it was for": "The audience you were aiming at.",
    "What it did": "The outcome — views, retention, comments."
  }
}
```

Set `youtubeId` and the thumbnail and watch-link appear automatically — no
image file needed.

### Shorts — `SHORTS`

```js
{ show:"SparX", image:"assets/shorts/01.jpg", link:"https://instagram.com/reel/...", hook:"Counterintuitive stat in frame one.", tag:"Instagram · Reel" }
```

Instagram has no public thumbnail URL, so save a **9:16 screenshot** of the reel
into `assets/shorts/` and point `image` at it.

### Campaigns — `CAMPAIGNS`

```js
{ show:"Headout · 2024–26", title:"Headout for Creators", image:"assets/campaigns/headout.jpg", link:"https://...", metric:"1L+ creators", role:"...", breakdown:{...} }
```

Save a **16:9 image** into `assets/campaigns/`.

### Numbers and the scrolling strip

`STATS` is the six-tile grid; `MARQUEE` is the scrolling list of brands and
skills. Both are plain lists — add or remove freely.

## Publishing changes

```bash
git add -A && git commit -m "Add SparX episodes" && git push
```

GitHub Pages redeploys in about a minute.

## Notes

- The clapperboard intro plays once per browser session, and is skipped
  entirely for anyone with reduced-motion turned on. Click, Esc, Enter or
  Space skips it.
- Light and dark mode both follow the visitor's system setting.
