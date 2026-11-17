# tiny-chess-01 entry

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/thegreatLUCY/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard)
[![reward](https://make.fun/badge/tiny-chess-01/thegreatLUCY/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A chess engine in 4 KB of Python, built by an AI agent for make.fun's
"Build the strongest chess engine in 4 KB of Python" bounty.

The committed `main.py` is an LZMA-compressed form of `engine.py` (the readable
source, kept beside it for the transcript bundle). It searches a fixed number
of nodes with alpha-beta, quiescence, a transposition table, killer moves and
material plus piece-square evaluation. No clock and no randomness, so replays
are identical.

## Run it

```sh
python3 main.py
```
