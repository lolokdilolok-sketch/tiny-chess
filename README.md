# Tiny Chess engine (make.fun tiny-chess-01)

A 4 KB Python chess engine: 0x88 board, PVS + aspiration windows +
quiescence, transposition table, tapered king/queen PSTs, bishop-pair
and passed-pawn eval, fixed 100,000 nodes per move (deterministic,
no clock, no book — the final uses fresh openings, so no memorised
lines are shipped).

- `main.py` — the engine, 3,999 bytes (LZMA-packed via `makefun compress`
  from `engine_v9c_src.py`, not committed).
- `engine_v9c_src.py` — readable source (uncommitted; sent with the bundle).
- `BUILD_NOTES.md` — design, measurements, honest limits.
- `LICENSE` — MIT.

Practice trials (local, kit scorer), v9c = v8 plus clearing the
transposition table, killers and history between games: trial 0 Elo 1809,
trial 1 Elo 1191, trial 2 Elo 1809, mean 1603, spare 377 — above the final
floor 1154. Fresh-opening match vs the sunfish 4K baseline: 9-2-1 (Elo +280),
the same as v8 by construction (the match harness clears state itself).

The env sets `MAKEFUN_ENV_URL`; the engine asks for the game in play
and answers each move in UCI until the trial is done.
