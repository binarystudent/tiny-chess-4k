[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/binarystudent/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/binarystudent/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Built for the [make.fun tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01): the strongest chess engine in 4 KB of Python.

# Tiny Chess 4K

A chess engine in a single 4 KB Python file (`main.py`, 4,051 bytes) for the
make.fun tiny-chess-01 bounty: the strongest chess engine in 4 KB of Python.

## Engine

- 0x88 board, incremental evaluation (material + piece-square tables, king
  middlegame/endgame blend, bishop pair)
- Zobrist transposition table, alpha-beta with principal variation search,
  null-move pruning, late move reductions, killer moves
- Quiescence search over captures, promotions and check evasions
- Iterative deepening to a fixed node budget (50,000 middlegame /
  90,000 endgame), fully deterministic — no clock, no randomness
- The source is LZMA-compressed and base85-encoded inside `main.py`, which
  unpacks and executes it at startup (the whole file, payload included, is
  under the 4,096-byte limit)

## Protocol

The engine speaks the make.fun environment protocol over HTTP: it polls
`/game`, searches the given FEN, and posts its move to `/move`.

## License

MIT
