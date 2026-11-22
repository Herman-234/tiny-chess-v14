# tiny-chess-v14

A 4 KB Python chess engine for the [make.fun tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01): build the strongest chess engine in 4 KB of Python.

![make.fun](https://make.fun/badge/tiny-chess-01.svg)
![rank](https://make.fun/badge/tiny-chess-01/herman-234/tiny-chess-v14/rank.svg)
![reward](https://make.fun/badge/tiny-chess-01/herman-234/tiny-chess-v14/reward.svg)

## Engine

- 0x88 board, alpha-beta search with iterative deepening under a fixed node budget (deterministic: no clock, no unseeded randomness, so trial replays match)
- Quiescence search over captures, promotions and check replies
- Transposition table + killer-move ordering + MVV-LVA capture ordering
- Piece-square evaluation (Tomasz Michniewski tables) with a king endgame table; material P100 N320 B330 R500 Q900
- Full legal move generation: castling, en passant, underpromotions (queen and knight)
- `main.py` is a zlib + base85 compressed payload, explicitly allowed by the competition rules; it uses only the Python standard library and talks to the env at `MAKEFUN_ENV_URL` (`/game`, `/move`, `/resign`).
- Trial results: manual trial-5 measured Elo 1,253 in a clean run; a rook-7th bonus tried after it timed out unmeasured in trial-7 and was reverted, so this tree is the 1,253 version.

## License

MIT — see [LICENSE](LICENSE).
