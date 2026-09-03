# GeoSED — GEF SGP CSO Challenge due diligence checklist

A single self-contained web page listing everything GeoSED must satisfy to pass the
GEF SGP CSO Challenge, grouped by the moment each thing is checked.

`index.html` has no build step and no dependencies. Open it locally, or publish it
with GitHub Pages and send the team the link.

## Publishing with GitHub Pages

No command line needed.

1. On github.com, create a new repository — for example `geosed-dd-checklist`.
2. Choose **uploading an existing file** and drop in `index.html` (and this README).
3. Open **Settings → Pages**.
4. Under **Source**, choose **Deploy from a branch**; pick branch `main` and folder `/ (root)`. Save.
5. Wait a minute or two. The page appears at
   `https://<your-username>.github.io/<repository-name>/`

## How progress actually travels between people

This is the part worth reading carefully, because it is not what most people assume.

GitHub Pages serves a **static file**. Everyone opening the link downloads the same
`index.html` and runs it in their own browser. When someone ticks an item, that tick is
written to their own browser's local storage — it never travels back to GitHub, because
a static host has nothing to write to. So ticking does **not** publish anything.

What everyone sees is whatever `index.html` was last committed. That gives a workflow
that does work, as long as one person owns it:

1. Anyone can open the page and tick their own items. That is theirs alone.
2. When the position should become official, one person — the checklist owner — clicks
   **Download updated page**, in the *Maintaining this page* block at the foot of the
   page. This rebuilds the whole page with the current ticks, owners and roster baked
   into it, and saves it as `index.html`.
3. That person replaces `index.html` in the repository (drag and drop on github.com,
   or commit it).
4. Within a minute everyone reloading the link sees the new baseline.

Two consequences to plan around. Anyone who has ticked items locally keeps seeing their
own ticks over the top of the new baseline until they press **Reset my ticks**. And two
people exporting at once will overwrite each other, so nominate a single owner for
step 2 — Fejay is the obvious candidate.

For quick coordination between commits, **Copy status** produces a plain-text summary of
what is still open and who holds it, ready to paste into the group chat.

The version inside Claude does share state live across everyone who opens it, with no
export step — but only for people in the same Claude organisation.

## Before you publish

A public repository means a public page. Anyone with the link can read it, and it
records our internal compliance position — items not yet evidenced, the loose ends in
Resolution No. 1, the note that we have not yet read the IUCN procurement policy. The
page carries a `noindex` tag so search engines skip it, but that is not access control.
If that matters, use a private repository (GitHub Pages on private repos needs a paid
plan) or circulate the file directly instead.

## Editing the content

The checklist items live in the `GATES` array inside the `<script id="prog">` block, and
the saved progress in the `<script id="state">` block above it. Editing either by hand
works, but the page is generated from the live Claude version, so changes made here will
be lost if it is regenerated.
