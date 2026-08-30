# ClamZhi BAR widgets

Personal [Beyond All Reason](https://www.beyondallreason.info/) LuaUI widgets.

## Widgets

### ClamZhi AdvPlayersList — `Widgets/gui_advplayerslist_clamzhi.lua`

A fork of the base game's **AdvPlayersList** (by Marmoth, spiced up by Floris) that
adds ways to control the order of the player list:

- **Ctrl + drag a player row** to move it up or down within your team's section.
  A plain Ctrl+click still toggles mute, same as vanilla.
- **Sort button** (small tab at the top‑right corner of the panel, shown on hover
  or before the game starts): orders your team to match the map's **expert
  recommended start positions** (the same data the *Start Position Suggestions*
  widget draws). On maps with no recommendation data it falls back to sorting by
  where teammates actually spawned, west→east / north→south.
- **Right‑click the sort button** to cycle the **name display** (the chosen mode
  is remembered between games):
  1. player names (default)
  2. recommended position label instead of the name (e.g. `Front 1`, `Pond`,
     `Sea Geo`) — glyph turns green
  3. 2‑letter position code + the username (e.g. `F1 SomePlayer`) — glyph turns cyan
- The list is **sorted automatically ~1 second after the game starts**, once
  everyone's start position is known.

Per‑map slot orders and position labels live in `StartposProfile()` in the widget
file. A profile is matched by the exact sequence of position *roles* in the map's
recommendation data, so it is map‑name independent. **Supreme Isthmus** (8 players
per team) is included.

Actions (bind with `/bind <key> <action>`):

| Action | Effect |
| --- | --- |
| `advplayerlist_autosort_by_position` | Same as the sort button |
| `advplayerlist_cycle_name_mode` | Cycle name display (names → labels → code+name) |
| `advplayerlist_startpos_dump` | Print the loaded recommendation slots to the console (for adding new map profiles) |

## Install

1. Open the BAR launcher → **Open Install Directory**.
2. Copy the widget file into `data/LuaUI/Widgets/`.
3. In game, press **F11**, disable the built‑in **AdvPlayersList**, enable
   **ClamZhi AdvPlayersList**. (They can't both run — they draw the same panel.)
4. `/luaui reload` to pick up changes.

## License

GPL‑2.0‑or‑later, inherited from the original AdvPlayersList widget. See `LICENSE`.
