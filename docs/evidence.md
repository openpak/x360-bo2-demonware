# Evidence: x360-bo2-demonware

## Supported title

- **Call of Duty: Black Ops 2** (TU17) — Title ID `0x47DB` / `41560817`

## Code and asset check

- The title ID in code is `TITLE_ID = 0x415608c3` (`src/core/bb-constants.ts`). This does not match the `0x47DB` / `41560817` values in the section above. The repository's Facts table uses the code value.
- `files/` holds TU18 assets (`online_tu18_mp_english.wad`, `online_tu18_zm_english.wad`, `en_ffotd_tu18_*`), while the section above says TU17. No file in `src/` references `files/`.

## Captures and test results

Nothing recorded yet.
