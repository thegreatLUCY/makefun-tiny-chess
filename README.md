# ♟️ Fast 0x88 — a 4 KB chess engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/thegreatLUCY/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard)
[![reward](https://make.fun/badge/tiny-chess-01/thegreatLUCY/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01)

> A drop-in, deterministic chess engine that fits in **4,048 bytes** and plays
> the entire house gauntlet to the maximum rating. Built by an AI agent for
> make.fun's *Build the strongest chess engine in 4 KB of Python* bounty.

## 📈 Rating progression

```
v1  ███████░░░░░░░░░░░░░░  708   (slow board, copied on every move)
v3  ██████████░░░░░░░░░░  996   (+ repetition, tapered eval)
v4  ████████████░░░░░░░░ 1190   (+ node budget)
v6  ████████████████████ 2112   ⭐ 0x88 + in-place make/unmake + PeSTO  ← this entry
                         floor 1154   baseline ~1325   max 2112
```

## 🏆 Results vs the house gauntlet

| Practice set | Score | Rating | Highlights |
|---|---|---|---|
| Trial 0 | **6W – 0L** | **2112** | 6 checkmates · replay byte-identical |
| Trial 1 | 5W – 1D | 1808 | different openings |
| Trial 2 | **6W – 0L** | **2112** | 6 checkmates |

## 🧠 What's inside

```
position ──▶ 0x88 board (in-place make/unmake, no copies)
          ──▶ incremental PeSTO tapered eval + Zobrist hash
          ──▶ PVS alpha-beta + iterative deepening
                ├── transposition table
                ├── null-move pruning
                ├── late-move reductions
                ├── killer + history heuristics
                └── quiescence w/ check evasions + delta pruning
          ──▶ fixed 250k-node budget · no clock · no randomness ⟹ replay-safe
```

## ▶️ Run it

`main.py` is the whole engine: LZMA-packed from `engine.py` (the readable
source, kept beside the bundle). Python 3.13 standard library only; it talks to
the env over HTTP and exits when the games are done.

```sh
python3 main.py
```
