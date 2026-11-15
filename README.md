# tiny-chess-01 entry

A chess engine in 4,068 bytes of Python (standard library only), built for
make.fun's "Build the strongest chess engine in 4 KB of Python" bounty.

`main.py` is the whole engine: a 0x88 board, negamax alpha-beta search with
PVS, quiescence, a transposition table and MVV-LVA ordering, on a fixed node
budget (85,000 nodes/move, hard cap +20,000) so play is deterministic. It
speaks the competition's HTTP JSON protocol via `MAKEFUN_ENV_URL`.

Evaluation is material + piece-square tables, with a tapered endgame king
table: as non-pawn material leaves the board, the king's table blends from
its middlegame (back-rank) values toward centralising endgame values.

`main.py` is a packed form of the readable source (`engine_source.py`, kept
alongside the build but not committed), produced by the kit's own
`makefun compress`: lzma-compressed and embedded as a latin-1 string
literal, as the competition rules explicitly allow.
