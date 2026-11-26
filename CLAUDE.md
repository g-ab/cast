# Cast: notes for Claude

## Restyling with Stylist
Cast's look comes from Stylist (https://github.com/g-ab/stylist). Its style files sit at the repo root:
`stylist-theme.css` (generated: never edit by hand), `app-tokens.css` (Cast's own tokens), `stylist-icons.css`,
`stylist.json` (the recipe), `components.json` and `brand/`. Load order: theme → app tokens → icons → brand.
`--clay` and the `.clay` classes are the clay material colour (the pottery clay). Keep them.

When gab pastes a **"Stylist setup for Cast"** block:
1. Get Stylist: clone https://github.com/g-ab/stylist (public) and run `python3 build.py` in it.
   It needs `pip install playwright` and a Chromium (`python3 -m playwright install chromium`, or `STYLIST_CHROME=/path/to/chrome`).
2. Save the pasted text to a file and run `python3 <stylist>/export.py <this repo> <that file>`.
3. If it stops (exit code 2), the theme file was edited by hand since the last export. Show gab the list and stop:
   he resolves them in Stylist (Share → Open from GitHub… → g-ab/cast) and pastes a new setup. Never overwrite them.
4. Otherwise show gab the "Changed tokens" list, check Cast still looks right in light and dark mode,
   and commit with that list in the message ("Restyle: …"). One restyle per commit, so it can be undone in one step.
5. Publish Cast as usual, so gab can check it live.

When gab says **"upgrade Stylist"**: do steps 1 and 3–5 above, but run `export.py` with no setup:
`python3 <stylist>/export.py <this repo>`. The files are rewritten in Stylist's latest format and Cast's look
must not change: if "Changed tokens" lists anything, show gab before committing. Commit as "Upgrade Stylist: …"
with what's new.

A new logo, mark or favicon isn't in a pasted setup: for those gab exports the full package from Stylist;
replace the files in `brand/` from it.
