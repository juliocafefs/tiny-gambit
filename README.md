# tiny-chess-01 — a chess engine in 4,067 bytes of Python

`main.py` is the whole engine: an lzma-packed Python program (standard
library only) that plays through the make.fun env (POST /game, POST
/move). Unpacked, it is a negamax alpha-beta search with:

- a transposition table with mate-distance scores
- null-move pruning and late-move reductions
- quiescence search over captures, promotions and check evasions
- check extensions and MVV-LVA move ordering
- repetition and fifty-move detection (game history plus search path)
- material and piece-square evaluation (tables stored as byte strings)
- a fixed 60,000-node budget per move

No clock is ever read: the same position and history always produce the
same move, so trials replay exactly.

Local practice results (the kit's three practice gauntlets, 6 games
each, anchors depth-2 855 … nodes-500k 1596): 5.0, 4.0 and 4.0 points,
a mean Elo of about 1,519.

License: MIT (see LICENSE).
