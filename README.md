# Stolperbeats Visualiser

An interactive web page that shows what the Stolperbeats shuffle does to a grid of 16th notes. Pick a Timing, turn the Shuffle control, and watch each hit get pushed off the straight grid, then hear it played back.

This is an unofficial educational tool. See the [disclaimer](#disclaimer) below.

## What it does

- **All four Timings:** Trip, Shake, Push and Clave.
- **All seven Shuffle settings (0 to 6)**, on a slider with fixed notches like the module's encoder.
- **Ten Deluge groove styles: DRNK, HOPP, DEEP and FOLD as buttons, lit green as the main four. A Grid switch (DELUGE 96 / MODULE 36) rebuilds the green four in whole ticks at 16 to 36 ticks per beat, the way Stolperbeats would hold them: DRNK becomes exactly Trip, HOPP lands within 4.6 ms, DEEP within 8.2 ms and FOLD within 2.4 ms of the 96-tick versions, on the module's own 16 to 36 tick grids (all divisible by 4, so the Subdiv clock out stays even), and the Feels run on that grid. Traced in firmware 163, XFOLD's per-track firing would work with a firmware change of roughly 80 lines of C (see NOTES.md). AFOLD, XFOLD, TRIO, PROG, VOODOO, LOTUS, SKEW, DROP, FLOP, FAFF, BALL, TOSS, SWAY and LIMP are archived: press MORE and they join the row.** Every one runs 0 to 6 like the module's Shuffle, with 0 meaning straight. These are swing tables written for the Synthstrom Deluge community firmware (branch `swing-styles-drnk-hopp`), shown at the Deluge's 96 ticks per beat. DRNK is Trip's six shuffled rows from the Stolperbeats manual, on a 1-beat window: each beat is cut into N slots (7, 9, 5, 6, 8, 9) and its four 16ths play on chosen slots. HOPP is MPC/Linn 16th swing in whole ticks (54.2% to 70.8%), cut from the patch's 7 levels to 6 by dropping 60.4%. BALL (proposed and not yet in the patch) treats the bar like a bouncing ball: each 16th gap is r times the one before (r = 0.995 down to 0.96), so the bar starts loose and stacks up toward the end, with the next downbeat on time. TOSS, SWAY and LIMP are also proposed bar-long styles: TOSS is BALL in reverse (tight, then opening out, everything early), SWAY bends the tempo in one wave per bar (beat 2 late, beat 4 early), and LIMP stretches beat 4 against the other three, up to 2+2+2+3 aksak at level 6. DEEP, also proposed, swings at two levels in a 1-beat window: the 8ths (52% up to triplet 66.7%) and each 8th's 16ths inside them (52% to 60%). DROP and FLOP, also proposed, are hybrids with 6 levels: DROP puts Kick and Snare on HOPP level L and the other four tracks on DRNK level L, FLOP does the opposite, and FAFF puts only the Kick on DRNK and the other five tracks on HOPP. TRIO, also proposed, pulls the off-beats toward the bar's six quarter-note triplets (all the way at level 6) while the four downbeats stay put, for a false 3-against-2 feel. PROG, also proposed, splits the bar 7+9 in the spirit of Tool's odd groupings: the first 7 steps stretch over half a bar and the last 9 rush through the other half, with a Seven nine preset that accents the groups. VOODOO, FOLD, LOTUS and SKEW give each track its own timing, which no other style does: VOODOO drags each track by its own amount in ms (D'Angelo's Voodoo, Kick +35, Snare +50, clap +70, Perc 2 +100 as the bass, hats straight); FOLD folds the "e" and "a" of every beat in toward the "&", on one grid, so on Stolperbeats it would be a plain table change; AFOLD in the archive alternates (in on beats 1 and 3, out on 2 and 4), and XFOLD keeps the original per-track version, where hats fold in while Kick and Snare fold out (after Flume); LOTUS swings each track at its own ratio, from a straight Kick to 4:1 percs (after Flying Lotus); SKEW runs each track on its own drifting clock that resyncs on the one. All four reach about 100 ms at level 6 (at 90 bpm). The Deluge has no Feels, so the page models them: DRNK level L runs them on Trip's Shuffle L clock, and the other Deluge styles run them on Stolperbeats' straight 16-tick clock.
- **All four Feels:** Tight, Rolls, Flam and Slop, as backlit buttons in the manual's colours. Rolls draws and plays Hihat 2's ratchet bursts. Flam and Slop show their one-tick delays.
- **Lock, a proposed fifth Feel.** The Kick stays on the straight 16ths while every other track shuffles exactly as the Timing says. It isn't on the module or in the Deluge patch. It works on all six Timings.
- **Late, a proposed sixth Feel.** The Kick stays straight like Lock, and every Snare lands one Feel tick late, the same push Flam gives it. Hihats and percs shuffle as normal. Also not on any hardware, and works on all six Timings.
- **Linear**, as OFF/ON tiles beside the tempo, traced in firmware 163 and matching the manual: Snare beats Kick, both beat the hats and percs, open hat beats closed, Perc 2 beats Perc 1 (hats and percs are separate chains, so they can share a step). Silenced hits show as dashed outlines and don't play.
- **Stut, a proposed seventh Feel.** Trap-style Hihat 1 ratchets placed where producers usually put them: 32nd-triplet rolls on steps 7 and 15 (until the next hat, up to 2 steps), and a 32nd pickup on the hat before each snare and at the end of the bar, getting louder into each target. The ratchets follow the Timing's grid. Two new presets, Trap and Quarter trips, show off Stut and TRIO. Four busier presets, Afrobeat, Samba, Jungle and Dembow, keep both Perc tracks working, which is where the per-track styles show most.
- **Six tracks in the module's order:** Kick, Snare, Hihat 1, Hihat 2, Perc 1, Perc 2.
- **8 preset beats, plus a blank "Your beat" slot.** Click or drag on the grid to program it; it's saved in your browser.
- **Hear straight**, an A/B toggle that bypasses the shuffle so you can compare it with straight 16ths.
- **808, 909 and 606 kits**, synthesised in the browser.
- **A close-up of half a bar**, showing the exact tick every step lands on and its offset in milliseconds at the current tempo.
- **Mute buttons per track, a tempo control, and light/dark mode.**

## How to use

It's a single HTML file with no build step and no dependencies.

- **Locally:** download `index.html` and open it in a modern browser (Chrome, Firefox, Safari or Edge).
- **GitHub Pages:** in the repo settings, go to Pages, choose to deploy from the `main` branch root, and open the URL it gives you.

Audio starts on your first click, because browsers block sound until you interact with the page.

## How accurate is it

The hit positions are calculated the same way the module calculates them, using timing values read from Stolperbeats firmware 163.

**Taken from the firmware:**
- Ticks per beat for each Shuffle setting.
- The step-length tables for each Timing.
- How steps are placed: each step fires at the running total of the step lengths before it, and each tick lasts 1/N of a beat.
- What each Feel does to the timing:
  - **Flam:** Kick and Snare fire one tick after their step.
  - **Slop:** Kick and Snare fire one tick late, and the hihats do too on steps where Kick or Snare also hits.
  - **Rolls:** Hihat 2 retriggers on every tick (Shuffle 0 and 3) or every second tick (the other settings) until the next step.

**DRNK and HOPP:** the tables are copied from `swing_style.cpp` (`kHoppEven16th`, `kDrnkTuplet`, `kDrnkSlots`) and match `gen_tables.py`. DRNK's slots are the same ones the firmware 163 Trip tables give at Shuffle 1 to 6. The page shows the 16th steps at the default 16th swing interval. On the Deluge, notes between steps are warped smoothly too.

**Inferred, not confirmed:**
- **Which table belongs to which Timing button.** The tables are in button order and match the descriptions in the official manual.
- **Feel colours.** These come from the manual. The firmware only switches one of four LEDs per button.
- **Trigger pulse length and MIDI output** of the Feels haven't been traced.
- **Hardware.** None of this has been measured on a real module.
- **Beats and sounds.** The preset beats are examples, not the module's pattern banks. The kits are approximations, not samples of the original machines.

## Disclaimer

This is an unofficial, independent project made for education. It is not affiliated with, endorsed by, or supported by Making Sound Machines.

Stolperbeats is designed and made by [Making Sound Machines](https://makingsoundmachines.com/stolperbeats/), and all rights in the module, its firmware and its documentation remain theirs. The small set of timing values used here was read from publicly available firmware purely to illustrate how the shuffle behaves. No firmware is included in or distributed by this repository.

The Deluge styles (DRNK, HOPP, DEEP, DROP, FLOP, FAFF, BALL, TOSS, SWAY and LIMP) are not part of Stolperbeats. They are groove styles proposed for the open-source Synthstrom Deluge community firmware. DRNK reproduces the Trip patterns published in the Stolperbeats manual, and the Trip timing is Making Sound Machines' design. Neither style is an official release of, or endorsed by, Synthstrom Audible or Making Sound Machines.

For official information, use the [Stolperbeats manual](https://makingsoundmachines.com/stolperbeats/) and Making Sound Machines' own support channels.

## Credits

- Stolperbeats and its Trip, Shake, Push and Clave timings are by Making Sound Machines.
- DRNK and HOPP are groove styles for the Deluge community firmware. DRNK's patterns are Stolperbeats' Trip timing, by Making Sound Machines. The Deluge is made by Synthstrom Audible.
- The 808, 909 and 606 names refer to the classic drum machines whose character the kits loosely imitate. The trademarks belong to their owners.
