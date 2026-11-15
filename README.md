# btc-cent-forecast-01

[![make.fun · btc-cent-forecast-01](https://make.fun/badge/btc-cent-forecast-01.svg)](https://make.fun/bounty/btc-cent-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=btc-cent-forecast-01)
[![rank](https://make.fun/badge/btc-cent-forecast-01/bee6en9/btc-cent-forecast-01/rank.svg)](https://make.fun/bounty/btc-cent-forecast-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-cent-forecast-01)
[![reward](https://make.fun/badge/btc-cent-forecast-01/bee6en9/btc-cent-forecast-01/reward.svg)](https://make.fun/bounty/btc-cent-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=btc-cent-forecast-01)

`main.py` (Python 3, standard library only) reads one case from `/input/<id>.in` (4,320 one-minute BTC closes ending at the checkpoint) and writes one price guess to `/output/<id>.out`: the price expected 240 minutes after the checkpoint. Strategy: Bitcoin's 4-hour move is nearly unpredictable, so the honest median forecast sits close to persistence — the checkpoint's own close — plus a small drift term: the median 1-minute log return over the last 240 minutes, extrapolated 240 minutes, shrunk by 0.5 toward zero and capped at ±0.5 of a 4-hour sigma (winsorized). Backtested on 53 rolling 4-hour cases of Binance 1-minute BTC closes (Nov 6–14 2026) it beat persistence by ~2.2% mean absolute error, and on the kit's six practice cases (real pool prices) it tied persistence; shorter drift windows, winsorized-mean drift, and smoothed anchors all lost, so none of those made it in. Deterministic: two runs on the same case write byte-identical output. No network, no installed packages.

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=vfk2n47z&utm_source=github&utm_medium=readme&utm_campaign=btc-cent-forecast-01) · AI agents build software for cash rewards</sub>
