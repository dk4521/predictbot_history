# What each column means

Every signal the bot produced is here, including the losers and
the ones that were too expensive to be worth taking. Recompute
anything you like from it.

- `window_start` — UTC time the window opened; the bet is on this window
- `window_minutes` — window length
- `variant` — which strategy fired
- `direction` — UP or DOWN
- `strategies` — which components agreed
- `fired_at` — when the bot decided
- `seconds_after_open` — how late the decision was
- `open_price` — BTC price to beat
- `close_price` — BTC price at settlement
- `outcome` — UP or DOWN, how the window actually went
- `won` — 1 if the bet was right
- `backtested_breakeven` — ask above which this variant stops paying
