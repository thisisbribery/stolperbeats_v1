# Stolperbeats Visualiser

An interactive web page that shows what the Stolperbeats shuffle does to a grid of 16th notes. Pick a Timing, turn the Shuffle control, and watch each hit get pushed off the straight grid, then hear it played back.

This is an unofficial educational tool. See the [disclaimer](#disclaimer) below.

## What it does

- **All four Timings:** Trip, Shake, Push and Clave.
- **All seven Shuffle settings (0 to 6)**, on a slider with fixed notches like the module's encoder.
- **All four Feels:** Tight, Rolls, Flam and Slop, as backlit buttons in the manual's colours. Rolls draws and plays Hihat 2's ratchet bursts. Flam and Slop show their one-tick delays.
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
  - **Slop:** Kick, Snare and both hihats fire one tick late.
  - **Rolls:** Hihat 2 retriggers on every tick (Shuffle 0 and 3) or every second tick (the other settings) until the next step.

**Inferred, not confirmed:**
- **Which table belongs to which Timing button.** The tables are in button order and match the descriptions in the official manual.
- **Feel colours.** These come from the manual. The firmware only switches one of four LEDs per button.
- **Trigger pulse length and MIDI output** of the Feels haven't been traced.
- **Hardware.** None of this has been measured on a real module.
- **Beats and sounds.** The preset beats are examples, not the module's pattern banks. The kits are approximations, not samples of the original machines.

## Disclaimer

This is an unofficial, independent project made for education. It is not affiliated with, endorsed by, or supported by Making Sound Machines.

Stolperbeats is designed and made by [Making Sound Machines](https://makingsoundmachines.com/stolperbeats/), and all rights in the module, its firmware and its documentation remain theirs. The small set of timing values used here was read from publicly available firmware purely to illustrate how the shuffle behaves. No firmware is included in or distributed by this repository.

For official information, use the [Stolperbeats manual](https://makingsoundmachines.com/stolperbeats/) and Making Sound Machines' own support channels.

## Credits

- Stolperbeats and its Trip, Shake, Push and Clave timings are by Making Sound Machines.
- The 808, 909 and 606 names refer to the classic drum machines whose character the kits loosely imitate. The trademarks belong to their owners.
