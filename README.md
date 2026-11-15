# tiny-chess-01 entry

A chess engine in 4,086 bytes of Python (standard library only), built for
make.fun's "Build the strongest chess engine in 4 KB of Python" bounty.

`main.py` is the whole engine: a 0x88 board, negamax alpha-beta search with
PVS, quiescence, a transposition table and MVV-LVA ordering, on a fixed node
budget so play is deterministic. It speaks the competition's HTTP JSON
protocol via `MAKEFUN_ENV_URL`.

Local practice measurement (official rig, 3 trials x 8 games): aggregate
performance rating about 1,200.
