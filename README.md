# BTC up/down — a signal's track record, published daily

A bot scores every 5- and 15-minute BTC window and predicts UP or DOWN.
Eleven variants score each window independently, published as `K1` through
`K11`. What each one actually does is not disclosed — that part is the work.
What is disclosed is every signal all eleven of them produce, written to
`record.csv` the moment it fires and before the window resolves: winners,
losers, and the ones no sane person would have paid the asking price for.

A code name costs you nothing as a reader. `K7` either calls windows
correctly over hundreds of rows or it does not, and that is checkable here
whether or not you know how it works.

Nothing is for sale here. This is the sample being built in public.

**Daily posts: [t.me/predicbots](https://t.me/predicbots)** — the same numbers,
every morning, in words rather than columns.

## Why you can check this rather than believe it

Every row carries the window's open and close price from Binance. Pick any
line, fetch the same minute from Binance yourself, and confirm the outcome
column. A claimed win rate is worth nothing; a file you can recompute is
worth something.

The git history is the other half. Rows are committed the day they happen
and never edited afterwards, so you can see for yourself that the losses
were not quietly removed later. That is the part a screenshot cannot show.

## Reading the table

These are binary contracts: what you pay scales with how likely the outcome
already looks. A variant winning 82% of the time is buying at around 85c and
losing money. One winning 56% and buying at 53c is making it.

**Win rate alone tells you nothing.** What pays is the gap between the win
rate and the price — and the price is deliberately not in this file.

## Files

| file | what it is |
|---|---|
| `record.csv` | every signal, one row each |
| `POST.txt` | today's summary in plain words |
| `summary.json` | per-variant totals |
| `COLUMNS.md` | what each column means |

The file is regenerated and committed once a day. If today's commit is missing,
today's rows are missing too — the record is not backfilled later.

## What this is not

Not advice. Not a service. Not a claim that any of it will keep working —
two months of data is not enough to conclude much, which is exactly why the
file is being published while it accumulates rather than after.
