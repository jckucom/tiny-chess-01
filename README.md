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
