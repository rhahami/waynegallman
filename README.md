# Wayne Gallman II — brand site

Single file. No build step, no framework. Open `index.html` in a browser and it runs.

---

## 1. Drop in the media

**Video clips** → `assets/video/` — **already done.**

Six clips are cut and in place, pulled from the 2020 Giants season reel you sent.
They run across the full width of the page and cross-cut like an edit: long holds,
then rapid-fire bursts. All in colour.

| File | What's in it | Source timecode |
|---|---|---|
| `clip-01.mp4` | Downhill run, tracking shot with the pulling guard | 44.3s |
| `clip-02.mp4` | Long open-field sprint | 96.8s |
| `clip-03.mp4` | Breaking through the gap into space | 5.7s |
| `clip-04.mp4` | Power run through contact near the goal line | 127.5s |
| `clip-05.mp4` | Walking straight at camera in the end zone | 78.2s |
| `clip-06.mp4` | Goal-line push into the pile | 149.1s |

To swap or add clips: drop new `.mp4` files in `assets/video/` and edit the
`clips` array in the CONFIG block. Landscape 16:9, 3–10 seconds, no audio needed,
under ~2 MB each so phones don't choke.

**Photos** → `assets/img/`

| File | Where it shows | Shape |
|---|---|---|
| `brands-01.jpg` | Brands, top of the stack | wide, 16:10 |
| `brands-02.jpg` | Brands, bottom left | vertical, 4:5 |
| `brands-03.jpg` | Brands, bottom right | vertical, 4:5 |
| `portrait.jpg` | About | vertical, 3:4 |
| `contact.jpg` | Contact | wide, 16:9 |
| `og.jpg` | link preview when the site is shared | 1200×630 |

Any slot without a file shows a labelled placeholder instead of a broken image,
so the page never looks broken mid-build.

---

## 2. Fill in the follower counts

Open `index.html`, scroll to the `CONFIG` block near the bottom (it's clearly
marked and it's the only thing you ever need to edit). Set the numbers:

```js
social: {
  instagram: { count: 48200, handle: '@waynegallman9', url: '...' },
  x:         { count: 12400, handle: '@waynegallman',  url: '...' },
  linkedin:  { count: 3100,  handle: 'Wayne Gallman II', url: '...' }
}
```

Plain integers, no commas. The site formats them (48.2K, 1.2M) and animates the
count-up, and the "Combined Reach" tile adds itself up. Leave a count at `0` and
that tile reads ADD COUNT so you can see what's still missing.

**Double-check the handles and profile URLs before this goes live** — the ones in
there now are a best guess from a web search, not confirmed by Wayne.

---

## 3. Wire up the contact form

1. Go to **web3forms.com**, enter `rhahami@gmail.com`, and they email you an
   access key. Free, no account, no server.
2. Paste it into `CONFIG.web3formsKey`.

Done. Submissions land in that inbox with the inquiry type in the subject line.

Until a key is in there, the form falls back to opening the visitor's email app
with everything pre-filled — so nothing is lost if the site goes up early.

---

## 4. Put it online

The whole folder is static, so anything works. Easiest options:

- **Netlify Drop** (app.netlify.com/drop) — drag the folder onto the page. Live in
  about 20 seconds, free, and you can point a custom domain at it later.
- **Vercel** or **Cloudflare Pages** — same idea, drag or connect a repo.

Whichever you pick, upload the **entire folder**, not just `index.html`. The
fonts live in `assets/fonts/` and are bundled so the site loads fast and doesn't
depend on Google.

---

## Notes

- Everything editable is in the `CONFIG` block. Clips, counts, form key, and the
  scrolling credential ticker. Nothing below it needs touching.
- The montage pauses itself when you scroll past the hero, so it isn't burning
  a phone battery while someone reads the About section.
- Career stats in the copy were sourced from Wikipedia and Pro-Football-Reference
  in Aug 2026. Worth a second pass with Wayne before it's public.
