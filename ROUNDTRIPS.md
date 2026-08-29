# The round-trip record

Three bots, R1, R2 and R3, that differ from the ones in `record.csv` in one
way: each of these opens a position **and closes it again inside the same
window**, rather than buying once and waiting for the window to settle.

So a row here is not a prediction that came true or did not. It is a purchase
and a sale, and `won` means it sold for more than it cost -- which is a
different question from whether the window went our way.

What a trade earned is not in this file, for the same reason the asks are not
in `record.csv`: both venues reserve their own market data, and what a signal
returns at a given price is what a buyer is paying to find out. Outcomes and a
win rate are here, and they are enough to check every row.

`would_have_won` says whether holding that same position to settlement would
have won instead. If it consistently would have, these bots are worse than
doing nothing clever, and the file will show it.

Every closed position is here, including the losses.

This file has been published since the family's first day of trading,
2026-08-29 -- including that first day, which was a loss, and including the
rows a deploy crash left behind. Publishing was not started once the numbers
looked worth showing, and the git history of this repository is what proves it:
one commit a day, never rewritten.

## Rows marked `not-closed`

Some rows show `not-closed` under `exit`, with `won` and `hold_seconds` blank.
Those are positions the process never managed to sell -- it was restarted, or
it crashed, while holding one. Nothing was sold, so there is no round trip to
call won or lost; `would_have_won` still says what the window did, because that
is what the position was left exposed to.

They are kept in the file, not removed, and counted on their own line in
`roundtrips_summary.json` as `never_sold`. A record that drops rows is not a
record, and a family reporting forty trades while seven more were abandoned
mid-position would be hiding exactly the ones that went wrong.

## What each column means

- `window_start` — UTC time the window opened; the position lived inside it
- `window_minutes` — window length
- `bot` — which round-trip bot: R1, R2 or R3
- `side` — UP or DOWN -- which token was bought
- `opened_at` — when the position was opened
- `hold_seconds` — how long it was held before being sold
- `exit` — what closed it: target, stop, clock, timer, signal-gone, or not-closed
- `won` — 1 if it sold for more than it cost
- `outcome` — UP or DOWN, how the window went in the end -- the position was already sold by then
- `would_have_won` — 1 if holding to settlement would have won instead
