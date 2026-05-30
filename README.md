cat > /tmp/README.md << 'ENDOFFILE'
# DD2 Clone — Dangerous Dave in the Haunted Mansion (1991)

A faithful + creative reverse-engineered clone of the 1991 MS-DOS game *Dangerous Dave in the Haunted Mansion*.

## Current Status (as of latest build cycle)

**Python Prototype** (`./run_prototype.sh`)
- Fully playable with original level data (RLEW + 2-plane levels + real EGA tiles)
- Physics and mechanics closely matched to DD2ME reference
- Excellent practice tools:
  - Savestates (F5/F9)
  - Pause + frame advance (P + Space)
  - Ghost replays + live racing (F4–F12)
  - X-Ray mode with hitboxes and tag inspector (F1)
  - Slow motion and speed control
- **Real 1991 sprites** (F3 toggle):
  - "REAL" mode loads authentic EGA data from original `S_DAVE.DD2` and monster archives using frame hints + 4-plane planar unpacking
  - Currently supports multiple real walk frames + real jump/shoot surfaces
  - Real monsters from S_FRANK + S_CHUNK1 + S_CHUNK2
- Linux/X11 robustness: auto-forces X11 driver + clear diagnostics on startup failure

**Zig Engine** (`cd zig_game && zig build run`)
- Basic playable movement, shooting, monsters, pickups
- Pure Zig RLEW decoder
- Still mostly colored rects (real sprite port in progress)

## How to Run (Python Prototype)

```bash
./run_prototype.sh 1     # Start on Level 1
```

On Linux, the launcher automatically sets `SDL_VIDEODRIVER=x11`.

## Key Controls

- Arrows: Move
- Left Ctrl: Jump
- Left Alt: Shoot
- F1: X-Ray mode
- F2: Practice Mode (infinite lives)
- F3: Toggle REAL sprites vs bootstrap
- F4/F5: Ghost record / playback
- F5/F9: Savestate save/load
- P + Space: Pause + frame advance
- F12: Ghost comparison mode

## Project Structure

- `python_game/` — Main playable prototype (Pygame)
- `zig_game/` — High-fidelity Zig + Raylib engine
- `tools/` — Parsers (rlew, egatiles, huff) + utilities
- `docs/` — Reverse engineering notes (formats.md, mechanics.md)
- `assets/original/` — Symlinks to pristine DD2 files (not committed)

## Current Focus Areas (Good Tasks for Codex / Copilot)

1. **Complete the pure HUFF decoder** — The current high-quality real sprites come from smart extraction using frame hints + 4-plane planar. A full bitstream decoder would allow even better/cleaner animation frames directly from the compressed data.
2. **Port real sprite logic to Zig** — Mirror the Python real surface extraction + 4-plane unpacking in the Zig engine.
3. **Improve collision & ladders** — Current collision is functional but not pixel-perfect with the original.
4. **More monster behaviors** — Some object tags and special enemies still need implementation.
5. **Sound** — PC speaker emulation or sample-based.
6. **Web/WASM build** of the Zig version.
7. Polish remaining edge cases in the Python prototype (exact door/teleport behavior, scoring, full 8-level support).

## Collaboration

This repo is intended for active collaboration with AI coding assistants (GitHub Copilot / Codex) and humans.

Feel free to open issues with specific implementation tasks or start working on any of the focus areas above.

## License / Notes

This is a reverse-engineering / preservation project. Original game files are required locally and are not redistributed here.

---

**Last major updates**: Linux/X11 robustness, 4-plane EGA unpacking improvements, expanded real sprite animation (up to 4-frame real walk + real jump/shoot), real monsters from multiple archives, critical `shoot_cooldown` bug fix.
ENDOFFILE
cat /tmp/README.md