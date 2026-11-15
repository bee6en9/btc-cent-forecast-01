# BTC cent forecast — median persistence with shrunk, capped drift

`main.py` (Python 3, standard library only) reads one case from
`/input/<id>.in` (4,320 one-minute BTC closes ending at the checkpoint)
and writes one price guess to `/output/<id>.out`: the price expected 240
minutes after the checkpoint.

Strategy: Bitcoin's 4-hour move is nearly unpredictable, so the honest
median forecast sits close to persistence — the checkpoint's own close —
plus a small drift term: the median 1-minute log return over the last
240 minutes, extrapolated 240 minutes, shrunk by 0.5 toward zero and
capped at ±0.5 of a 4-hour sigma (winsorized). Backtested on 53 rolling
4-hour cases of Binance 1-minute BTC closes (Nov 6–14 2026) it beat
persistence by ~2.2% mean absolute error, and on the kit's six practice
cases (real pool prices) it tied persistence; shorter drift windows,
winsorized-mean drift, and smoothed anchors all lost, so none of those
made it in. Deterministic: two runs on the same case write byte-identical
output. No network, no installed packages.
