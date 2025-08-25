# Thunderbird Crew Credits (Movie-Style Scroll)

This repo stores a single source of truth for Thunderbird’s community credits and auto-generates a human-friendly `CONTRIBUTORS.md`. Your add-on (“role credits”) can fetch the JSON to render a scrolling, movie-style credit roll.

---

## Files

- `data/credits.json` — **source of truth** for credits (machine-readable).
- `data/credits.backup.json` — **fallback** copy you can bundle in your add-on.
- `data/credits.schema.json` — JSON Schema used to validate `credits.json`.
- `CONTRIBUTORS.md` — auto-generated from `data/credits.json` (human-readable).
- `.github/workflows/credits-validate-and-build.yml` — CI that validates/builds monthly and on PR.

> Update cadence: **once per month** (or as needed). CI runs monthly + on PR.

---

## Edit flow

1. Open `data/credits.json` and add/remove names under each role.
2. Open a PR. CI will:
   - Validate your JSON against `data/credits.schema.json`.
   - Generate `CONTRIBUTORS.md`.
   - Commit it back if it changed.

If validation fails, the PR will show an error so you can fix the structure before merging.

---

## JSON format

```json
{
  "title": "Thunderbird: The Motion Picture — Credits",
  "sections": [
    { "role": "Directed by", "names": ["Michael Ellis", "John Doe", "Jane Doe"] }
    // ...
  ],
  "end_line": "Thunderbird opening soon on a desktop near you."
}
