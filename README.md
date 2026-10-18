# Stolperbeats Visualiser

This is a visualiser and emulator of the MSM Stolperbeats module. I made this to help my eyes understand what my ears were hearing, and also to experiment with hypothetical "alt timings" that may be able to be added to the firmware at some stage. I built this for educational purposes only.

It's unofficial. See the [disclaimer](#disclaimer).

## Using it

It's a single HTML file with no build step and no dependencies.

- **Locally:** open `index.html` in Chrome, Firefox, Safari or Edge.
- **GitHub Pages:** in the repo settings, go to Pages, deploy from the `main` branch root and open the URL it gives you.

Pick a Timing, turn the knob and press Play. Audio starts on your first click, because browsers block sound until you interact with the page.

## What's on the page

- **Timing, Feel and the 0 to 6 knob**, laid out like the module.
- **Six tracks** in the module's order: Kick, Snare, Hihat 1, Hihat 2, Perc 1, Perc 2. Click or drag to write your own beat; it's saved in your browser.
- **Four bars, like the module.** Kick and Snare run 4 bars (64 steps). The hats and percs loop 1 bar (16 steps) under them. See [Four bars](#four-bars).
- **15 preset beats**, including busier ones with both Perc tracks working (Afrobeat, Samba, Jungle, Dembow).
- **Hear straight**, to compare any setting with straight 16ths.
- **808, 909 and 606 kits**, synthesised in the browser.
- **A close-up** of half a bar (or the whole bar for bar-long styles), with the tick each step lands on and its offset in ms.
- **A timing creator** (the CREATOR switch at the top) for making your own Timing tables by hand. See below.
- **Mute buttons, tempo, light and dark mode**, and a layout that keeps the controls and the grid on one screen.

## Timings

### From the module (firmware 163)

| Timing | Feel |
|---|---|
| Trip | Uneven tuplet grooves where steps trip over each other |
| Shake | Long-short swing on every pair of 16ths |
| Push | Steps lean late, making room for each downbeat |
| Clave | 3:3:2 anchors hold while the other steps swing |

### Alt timings (the green four)

| Style | What it does | On the module |
|---|---|---|
| DRNK | Trip's six shuffled rows, from the Deluge community firmware patch | It *is* Trip |
| HOPP | MPC / Linn 16th swing in whole ticks (54.2% to 70.8%) | Table swap |
| DEEP | Two-level swing: the 8ths swing, then the 16ths inside them | Table swap, tested on hardware |
| SQEZ | Made in the creator: starts like CLSTR, then the & and a squeeze up against the next downbeat. Module rows only, no DELUGE 96 version | Table swap (test build 166) |

### Archive (press MORE)

| Style | What it does |
|---|---|
| CLSTR | DRNK inside out: the e, & and a cluster mid-beat, and levels 4 to 6 shift right to lean hard late (table swap, test build 165) |
| FOLD | The "e" and "a" of every beat fold in toward the "&" (table swap, tested on hardware in build 164) |
| AFOLD | FOLD alternating: in on beats 1 and 3, out on 2 and 4 |
| XFOLD | The original FOLD: hats fold in while Kick and Snare fold out (needs per-track firing) |
| TRIO | Off-beats pulled toward quarter-note triplets |
| PROG | The bar split 7+9, after Tool's odd groupings |
| VOODOO | Each track drags by its own amount in ms, after D'Angelo's *Voodoo* |
| LOTUS | A different swing ratio per track, after Flying Lotus |
| SKEW | Each track on its own drifting clock, resyncing on the one |
| DROP, FLOP, FAFF | Hybrids of HOPP and DRNK, split by track |
| BALL, TOSS | A bouncing ball and its mirror across the bar |
| SWAY | The tempo breathing across the bar |
| LIMP | 2+2+2+3 aksak: one long beat |

Every style runs 0 to 6 like the module's Shuffle, with 0 meaning straight 16ths.

### Grid: MODULE 36 or DELUGE 96

DRNK, HOPP and DEEP have two versions, chosen with the Grid switch:

- **MODULE 36 (default):** whole ticks at 16 to 36 ticks per beat, exactly how Stolperbeats would have to hold them. The Feels run on that grid too.
- **DELUGE 96:** the Deluge's 96 ticks per beat.

The two versions are within a few ms of each other (HOPP 4.6 ms, DEEP 8.2 ms at 90 bpm). DRNK on MODULE 36 is exactly Trip. SQEZ only exists as module rows, so it always plays on its own grid.

## Feels

| Feel | What it does | Source |
|---|---|---|
| Tight | All six tracks shuffle together | Module |
| Rolls | Hihat 2 retriggers until the next step | Module |
| Flam | Kick and Snare land one tick late | Module |
| Slop | Like Flam, plus the hats a tick late where they hit with Kick or Snare | Module |
| Lock | The Kick stays on the straight grid | Proposed |
| Late | Kick straight, Snare one tick late | Proposed |
| Stut | Trap-style Hihat 1 ratchets where producers usually put them | Proposed |

## Four bars

The manual's Pattern Edit lengths: Kick and Snare are 4 x 16 = 64 steps, Hihat 1, Hihat 2, Perc 1 and Perc 2 are 16 steps.

- **Bar tabs 1 to 4** pick which bar the grid shows and edits. Each tab has a mini map of that bar's Kick (top row) and Snare (bottom row).
- **Follow** keeps the grid on the bar that's playing. Pick a tab while playing to stay on that bar and edit it while the loop runs.
- In bars 2 to 4 the hats and percs are dimmed and labelled *1-bar loop*: they're bar 1 repeating, so editing them there edits the one bar they share.
- **Copy bar N to all** copies the shown bar's Kick and Snare into the other three.
- Play always starts from bar 1. Linear, Slop, Rolls and Stut work bar by bar, since they depend on that bar's Kick and Snare.
- The presets repeat one bar of Kick and Snare four times. Beats saved before this change load the same way.

## SKETCH and MODULE

The switch above the grid picks what the grid plays.

- **SKETCH:** the presets and your own beat, as before.
- **MODULE:** your pattern banks, picked the way the module does it. A **Bank** picker, then one picker per track: **Kick**, **Snare**, **Hihat 1**, **Hihat 2**, **Perc 1** and **Perc 2**, each 1 to 24. Each track picks its own number, so Kick on 3 with Hihat 1 on 17 is normal. Click the arrows, scroll over the number, or focus it and use the arrow keys.
- In MODULE, edits on the grid go straight into the bank, like Pattern Edit on the module.
- Every change lands straight away while playing, like the module: bank and pattern picks, grid edits, Timing, Shuffle, Feel, Linear and tempo. There's no wait for the next bar.
- Switching back to SKETCH brings back whatever you had there.
- The page remembers your mode, bank and pattern numbers.

All six tracks pick their pattern separately and changes land straight away, as on the hardware. Default until checked: Bank changes move every track at once and keep their numbers.

## Pattern banks

Program the module's pattern banks here and load them through its SD card. The **Pattern banks** panel under the grid starts closed; click it to open.

- **Import from SD** opens one or more `PatternBankNNN.txt` files. `PatternBank000.txt` is Bank 1. The bank number comes from the file name.
- **Bank chips** pick the bank. **File** renumbers it, **Remove** drops it from the browser.
- **Six rows of 24 tiles**, one row per track: Kick and Snare (each tile maps all 4 bars), then Hihat 1, Hihat 2, Perc 1 and Perc 2. Click a tile to put that track on that pattern, same as the MODULE pickers.
- **Send sketch to bank** (SKETCH mode) writes the beat on the grid into the bank at the numbers the rows show. **Tracks** picks which tracks it writes, so you can send just a new Kick. **Undo** reverses it.
- **New bank** starts an empty one on the first free number.
- **Download bank** saves the selected bank's file. **Download all** zips every bank.
- Banks stay in this browser until you remove them. No banks ship with the page.

### File format

Read from the module's own files. Six groups in this order: `KICK`, `SNARE`, `HIHAT1`, `HIHAT2`, `PERC1`, `PERC2`. Each has 24 lines, `PTN0` to `PTN23`:

```
KICK > PTN0: 1000000000000000, 1000000000000000, 1000000000000000, 1000000000000001;
HIHAT1 > PTN0: 1000100010001000;
```

Kick and Snare hold four 16-step bars separated by `, `. The others hold one. `1` is a hit. Windows line endings (CRLF), one blank line between groups, and a line ending after the last line. A full bank is 7462 bytes. The file stores hits only, no accents or velocity. Exports match the module's files byte for byte.

### Getting banks onto the module

1. Press Stop, then power off the rack. The module writes its data to the card when it stops, so never swap files while it's on.
2. Take out the SD card and back up every file on it.
3. Copy the downloaded PatternBank files into the same folder as the card's own, replacing any with the same name.
4. Put the card back and power on.
5. A bank number the module hasn't used yet starts switched off. Hold either Bank button for 2 seconds, turn the Kick encoder to the bank and click to switch it on.

## Firmware lab

Build your own experimental Stolperbeats firmware, then flash it, all in the page. The **Firmware lab** panel near the bottom starts closed.

This repo and page never contain firmware. You download the official file from [Making Sound Machines](https://makingsoundmachines.com/firmware/), the page changes it in your browser, and hands it back. For personal, educational experiments only.

1. **Open the .bin** (or drop it on the panel). The page checks it's an STM32 image, then finds the four Timing tables and the ticks-per-beat table by their factory values, never by fixed addresses. If anything doesn't match exactly once, it stops and changes nothing. Start from an unmodified official file.
2. **Pick your mods.** Each Timing button (Trip, Shake, Push, Clave) gets a menu: Factory, another factory table, a style from this page (HOPP, DEEP, SQEZ, CLSTR, FOLD), or your own Timings from the CREATOR. **Hear it** plays the pick in the visualiser. A pick that breaks the module's rules is marked in orange and can't be built.
3. **Build** downloads the new file, named for what changed (e.g. `..._hw_rev4-163-mod-PushDEEP-ClaveSQEZ.bin`), with a list of every byte range changed and its SHA-256.
4. **Flash** over USB in Chrome or Edge: hold BOOT, press and release RESET, let go of BOOT, then **Connect** and **Flash my build**. The page erases only the sectors it needs, writes, reads everything back to check it byte for byte, then restarts the module. **Flash official file** puts the original back. Elsewhere, use `dfu-util` as the manual describes.

The STM32 bootloader lives in the chip's ROM, so a bad flash can always be undone by flashing the official file again.

**Recipes.** Save recipe writes a small `.json` of your picks (and the rows of any of your own Timings), with no firmware in it. Anyone can open it with their own official file and build the same firmware. Share recipes, not `.bin` files.

**What's been checked.** Opened on the official 163 file (SHA-256 `c04df924…`), the lab finds every table, and building Push = DEEP with Clave = SQEZ gives a file byte for byte identical to test build 166, which ran on a real module. The USB flashing is tested against a simulated bootloader; flashing a real module from the page hasn't been tried yet.

### Adding a mod

Mods live in `fwPatches()` in `index.html`. A mod is a list of byte writes. The rules:

- Find what you change by its known content, and require exactly one match. Never hard-code an address.
- Keep the module's own rules (for Timings: whole ticks, 16 to 36 ticks per beat in steps of 4, the half bar adds up to 2N). Check them before building, and throw if they fail.
- Never add firmware bytes to the repo. Values you search for should be small and documented, like the timing tables.

## Linear

From the module, next to the grid. When tracks clash on a step only the highest priority one plays: Snare beats Kick, both beat the hats and percs, open hat beats closed, Perc 2 beats Perc 1. Hats and percs don't silence each other. Silenced hits show as dashed outlines.

## Download tables

The button by the Timings saves the **currently selected style** as a zip:

- a README
- the step positions at 96 ticks per beat (JSON and CSV)
- Stolperbeats-format rows, for HOPP, DEEP, FOLD and CLSTR
- one-bar MIDI groove clips for Ableton Live: right-click a clip and choose *Extract Groove(s)*

It's disabled for the four factory Timings. No firmware, addresses or patching steps are included.

## Download MIDI

The **Download MIDI** button above the grid saves all 4 bars exactly as they play, swing and all, so the groove survives in Ableton or any DAW even on a straight grid: every hit where the grid shows it, with the Timing, Shuffle, Feel, Rolls and Stut, accents as velocity, at the current tempo. Muted tracks and hits Linear silences are left out. It's four bars of GM drums on channel 10 (Kick 36, Snare 38, Hihat 1 42, Hihat 2 46, Perc 1 39, Perc 2 63) at 960 ticks per beat, so hits are placed to within 1/960 of a beat. The file name says what it is, e.g. `stolperbeats-Boom-bap-SQEZ-5-Tight-90-bpm.mid`.

## Creator

The **VISUALISER | CREATOR** switch next to Dark turns the Timing row into a table maker. The grid, kits, beats, Feels and playback all stay the same.

- **Start from** any Timing the module could hold as a table (Trip, Shake, Push, Clave, DRNK, HOPP, DEEP, CLSTR, FOLD, or one of your own), or from straight.
- **Drag steps** 2 to 4 and 6 to 8 in the half-bar view while it plays. Steps 1 and 5 are pinned to the beat. Or click a step and use the arrow keys.
- **The Shuffle slider picks the level.** Level 0 is always straight. A level you haven't touched yet starts as a copy of the one before, and **Copy previous level** re-copies it.
- **Grid** sets the level's ticks per beat (16 to 36 in steps of 4). **Snap** moves by single ticks or by 4-tick slots (N/4 slots per beat, like Trip).
- **Beats:** *Every beat* makes beat 2 copy beat 1 (like Shake, Push, DEEP and CLSTR). *Beat 1 ≠ 2* edits all 8 steps of the half bar (like Trip and Clave).
- The table under the half bar shows all 7 rows exactly as the firmware holds them: ticks per beat and 16 step lengths.

Every Timing made here keeps to the module's rules: whole ticks, 16 to 36 ticks per beat in steps of 4, every step at least 1 tick, and the half bar's 8 lengths adding up to 2N. The badge turns amber for things that are allowed but worth knowing: 1-tick steps (2 is the shortest tested on hardware), step 5 off the beat (factory Clave does this), and the Rolls buzz at level 3 on grids above 20.

- **Save to visualiser** adds it under MORE, with a teal light. Saved Timings stay in this browser only.
- **Export** downloads `NAME.timing.json`: the 7 rows in the same `stolperbeatsRows` format Download tables uses.
- **Import** loads a `.timing.json`, or a style's JSON from Download tables, back into the creator.

## How accurate is it

**Read from firmware 163:**
- Ticks per beat for each Shuffle setting, and the step-length table for each Timing.
- How steps are placed: each fires at the running total of the step lengths before it, and a tick is 1/N of a beat.
- Flam, Slop, Rolls and Linear, as described above.

**Confirmed on a real module:** a private test build with DEEP and FOLD swapped into the PUSH and CLAVE tables played as the page shows. That also confirms the PUSH and CLAVE buttons play those two tables.

**Matched, not traced or measured:**
- Feel colours, from the manual.
- Trip and Shake's buttons, from the manual's button order.
- How the Feels appear on MIDI out.
- The preset beats are examples, not the module's pattern banks, and the kits are approximations.

DRNK and HOPP come from `swing_style.cpp` in the Deluge community firmware branch `swing-styles-drnk-hopp`. Everything marked proposed is a model, not something on any hardware.

## Disclaimer

This is an unofficial, independent project made for education. It is not affiliated with, endorsed by, or supported by Making Sound Machines or Synthstrom Audible.

Stolperbeats is designed and made by [Making Sound Machines](https://makingsoundmachines.com/stolperbeats/), and all rights in the module, its firmware and its documentation remain theirs. The small set of timing values used here was read from publicly available firmware purely to illustrate how the shuffle behaves. No firmware is included in or distributed by this repository.

The alt timings are not part of Stolperbeats. DRNK reproduces the Trip patterns published in the Stolperbeats manual, and the Trip timing is Making Sound Machines' design.

For official information, use the [Stolperbeats manual](https://makingsoundmachines.com/stolperbeats/) and Making Sound Machines' own support channels.

## Credits

- Stolperbeats and its Trip, Shake, Push and Clave timings are by Making Sound Machines.
- The Deluge is made by Synthstrom Audible.
- The 808, 909 and 606 names refer to the classic drum machines whose character the kits loosely imitate. The trademarks belong to their owners.
