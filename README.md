# tiny-chess-01 entry

A chess engine in at most 4,096 bytes of Python (`main.py`, Python 3.13,
standard library only). It plays the make.fun gauntlet through the env at
`MAKEFUN_ENV_URL`: iterative-deepening alpha-beta search with a fixed node
budget (never a clock), a transposition table, quiescence, null-move
pruning and piece-square evaluation, so every replay makes the same moves.
