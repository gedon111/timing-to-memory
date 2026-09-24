# Electronic Timing Circuit Memory

Group 10. A scrolling, presentable explainer for people with no electronics background. It uses everyday comparisons instead of math, and only assumes the audience can read binary numbers. It is built for a talk of about 11 minutes plus questions, shown on a TV. It goes from a bucket that fills with charge to a clock, then from logic gates to latches and flip-flops, and ends with DRAM, which needs a timer to keep its bits. The last part is a hands-on memory lab.

Text is sized for a TV at 1920x1080 (42px body text). The diagrams keep their size.

Live site: https://gedon111.github.io/timing-to-memory/

## Files

- `index.html` is the whole site. It has no build step.
- `notes.md` is the speaker script, in plain language, with time targets per sheet and likely questions with answers.

## Sheets

1. Intro
2. Why keep time
3. Timing with a bucket (a capacitor filling through a resistor)
4. The 555 timer (fill, drain, repeat, and what is inside)
5. The clock (on and off, quartz halved down to 1 tick per second, billions of ticks)
6. Gates (a transistor as a switch, NOT and NOR)
7. The SR latch (set, reset, both)
8. Latch vs flip-flop (open door versus camera flash)
9. Bits to bytes (a byte, a register)
10. The cost of a bit (why RAM uses a smaller cell)
11. DRAM (tiny leaking buckets, a timer that tops them up, reading empties them)
12. Compare flip-flops and DRAM (including which timer each needs)
13. Memory lab
14. Recap and questions

## Presenting

| Key | Action |
|---|---|
| → ↓ Page Down Space | next beat (clickers send these) |
| ← ↑ Page Up | previous beat |
| Home, End | first or last beat |
| N | show the "sheet · beat" counter that matches `notes.md` |
| F | fullscreen |

### Memory lab

The lab simulates real logic gates. Every gate takes one small step to respond, so slow motion shows signals moving through the circuit one gate at a time.

- **Circuits:** SR latch (two NOR gates) and D flip-flop (two latches in a row).
- **Controls:**
  - Set and Reset (hold), and "Press both" (presses both, then lets go).
  - D, the clock on auto, and Tick to step the clock by hand.
  - Slow motion and Pause.
- **Keys** (only while the lab is on screen): hold S or R, D flips D, C ticks, M toggles slow motion, P pauses.

Releasing Set and Reset together makes the latch wobble. Real gates are never exactly equal, so after a few wobbles the simulator lets one side win at random.

## Run it

Open `index.html` in a browser. It loads GSAP 3.13 (core, ScrollTrigger, MorphSVGPlugin) from the jsDelivr CDN. Without GSAP, the text and the memory lab still work, but the animated diagrams are hidden.

The page is landscape only. On a portrait screen it asks you to rotate the device. With reduced motion turned on, the page skips scrubbing and loops and shows each finished diagram.

## Publish with GitHub Pages

Settings > Pages > Build and deployment > Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)**.

## Motion notes

Most animation uses only transform and opacity. These exceptions only repaint, and none of them change the page layout:

- MorphSVG changes the main trace's shape between sheets.
- The latch's feedback loop animates `stroke-dashoffset`.
- The lab redraws its waveform on a canvas and recolors schematic wires as signals change.
