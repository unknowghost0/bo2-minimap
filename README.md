# BO2 Zombies Minimap

A simple script-only radar/minimap for BO2 Zombies on Plutonium.

This is not a full native engine minimap with a real map texture.
It is a lightweight top-right radar that shows nearby teammates and zombies.

## Features

- Top-right minimap/radar
- Circular-style white radar ring
- White center dot for the local player
- Cyan dots for teammates
- Red dots for zombies
- Radar rotates with the player's view
- Nearby entity tracking with distance limiting
- Dot clamping so markers stay inside the radar area
- Round-based zombie-dot scaling
- Dynamic teammate slot usage so it does not waste HUD space on empty player slots

## Current Defaults

- `mm_enable` = `1`
- `mm_range` = `1400`
- `mm_max_teammates` = `7`
- `mm_max_zombies` = `10`

Notes:

- The mod supports up to 8-player servers better by only reserving teammate dots for real connected players.
- Zombie-dot display scales up by round, but still respects a safe HUD budget so the radar stays stable.

## Install

Put [minimap.gsc](C:/Users/Administrator/Documents/bo2%20server/mods/minimap/minimap.gsc) into your Zombies scripts folder:

```text
%localappdata%\Plutonium\storage\t6\scripts\zm
```

Example:

```text
C:\Users\Administrator\AppData\Local\Plutonium\storage\t6\scripts\zm\minimap.gsc
```

Then restart the BO2 Zombies server.

## How It Works

The mod creates a small HUD radar in the top-right corner and updates it while the player is alive.

It:

- watches player connections and spawns
- creates radar HUD elements when a player spawns
- updates teammate and zombie marker positions every tick
- cleans itself up on death, down, disconnect, and end game

## Dvars

These are the main dvars used by the script right now:

- `mm_enable`
  - enables or disables the minimap
- `mm_range`
  - controls how far out the radar checks for entities
- `mm_max_teammates`
  - base teammate marker limit
- `mm_max_zombies`
  - base zombie marker limit

The script currently initializes these itself in `init()`.

## Known Limits

- This is not a textured/native BO2 minimap
- Large maps like Transit and Origins may still need more tuning
- Heavy HUD usage from other mods can affect radar stability
- Long matches and map transitions should still be tested more

## Recommended Use

This mod is best used if you want:

- a simple radar
- nearby teammate awareness
- nearby zombie awareness
- a lightweight HUD add-on instead of a full UI overhaul

## Status

Working now:

- teammate dots
- zombie dots
- left/right radar orientation fix
- circular-style radar ring
- round-based scaling

Still worth testing more:

- map transitions
- reconnecting mid-match
- long sessions
- higher player counts
- different maps

## Roadmap

See [TODO.md](C:/Users/Administrator/Documents/bo2%20server/mods/minimap/TODO.md) for the current checklist, verification notes, and future ideas.

## Credits

Built as a custom BO2 Zombies script mod for Plutonium.
