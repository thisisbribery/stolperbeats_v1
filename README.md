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
- **One bar on six tracks** in the module's order: Kick, Snare, Hihat 1, Hihat 2, Perc 1, Perc 2. Click or drag to write your own beat; it's saved in your browser.
- **15 preset beats**, including busier ones with both Perc tracks working (Afrobeat, Samba, Jungle, Dembow).
- **Hear straight**, to compare any setting with straight 16ths.
- **808, 909 and 606 kits**, synthesised in the browser.
- **A close-up** of half a bar (or the whole bar for bar-long styles), with the tick each step lands on and its offset in ms.
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
| FOLD | The "e" and "a" of every beat fold in toward the "&" | Table swap, tested on hardware |

### Archive (press MORE)

| Style | What it does |
|---|---|
| AFOLD | FOLD alternating: in on beats 1 and 3, out on 2 and 4 |
| XFOLD | The original FOLD: hats fold in while Kick and Snare fold out (needs per-track firing) |
| CLSTR | DRNK inside out: the e, & and a cluster mid-beat, and levels 4 to 6 shift right to lean hard late |
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

The green four have two versions, chosen with the Grid switch:

- **MODULE 36 (default):** whole ticks at 16 to 36 ticks per beat, exactly how Stolperbeats would have to hold them. The Feels run on that grid too.
- **DELUGE 96:** the Deluge's 96 ticks per beat.

The two versions are within a few ms of each other (HOPP 4.6 ms, DEEP 8.2 ms, FOLD 2.4 ms at 90 bpm). DRNK on MODULE 36 is exactly Trip.

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

## Linear

From the module, next to the grid. When tracks clash on a step only the highest priority one plays: Snare beats Kick, both beat the hats and percs, open hat beats closed, Perc 2 beats Perc 1. Hats and percs don't silence each other. Silenced hits show as dashed outlines.

## Download tables

The button by the Timings saves the **currently selected style** as a zip:

- a README
- the step positions at 96 ticks per beat (JSON and CSV)
- Stolperbeats-format rows, for HOPP, DEEP, FOLD and CLSTR
- one-bar MIDI groove clips for Ableton Live: right-click a clip and choose *Extract Groove(s)*

It's disabled for the four factory Timings. No firmware, addresses or patching steps are included.

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
