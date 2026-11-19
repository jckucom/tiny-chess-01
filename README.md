[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/jckucom/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/jckucom/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01 entry

A chess engine in at most 4 KB of Python (`main.py`, Python 3.13, standard
library only), built for the make.fun tiny-chess-01 bounty.

## Design

- 64-square board with incremental Zobrist hashing
- Iterative deepening under a fixed node budget, never a clock
- Negamax alpha-beta search with a transposition table and quiescence
  (captures and promotions, evasions when in check)
- Material plus piece-square evaluation, with a bishop-pair bonus and a
  separate endgame king table

## Play

The engine talks to the game env at `MAKEFUN_ENV_URL` — `POST /game`,
`POST /move` and `POST /resign` — playing one game after another, and it
exits when every game is over.

## Determinism

Every move is derived only from the position, the game history and the
fixed node budget: no clock and no randomness, so a replay of the same
game makes the same moves.
