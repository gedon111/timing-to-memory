# From Ticks to Memory

A scrolling, presentable explainer for people with no electronics background. It is built for a talk of about 15 minutes plus questions. It goes from a charging capacitor to a clock, then from logic gates to latches and flip-flops, and ends with DRAM and NAND flash. The last part is a hands-on memory lab.

Live site: https://gedon111.github.io/timing-to-memory/

## Files

- `index.html` is the whole site. It has no build step.
- `notes.md` is the speaker script, with time targets per sheet and likely questions with answers.

## Sheets

1. Intro
2. Why keep time
3. Timing with a bucket (RC and the time constant τ)
4. The 555 timer (sawtooth, what is inside, the speed formula)
5. The clock (square wave, quartz and 32,768 Hz, GHz and PLLs)
6. Gates (a transistor as a valve, NOT and NOR)
7. The SR latch (set, reset, both)
8. Latch vs flip-flop (level versus edge)
9. Bits to bytes (a byte, a 64-bit register)
10. The cost of a bit (transistors per bit)
11. DRAM (cell grid, leak, refresh, destructive read)
12. NAND flash (trapped electrons, tunneling and wear, pages and blocks, TLC and 3D)
13. Compare the three kinds of memory
14. Memory lab
15. Recap and questions

## Presenting

| Key | Action |
|---|---|
| → ↓ Page Down Space | next beat (clickers send these) |
| ← ↑ Page Up | previous beat |
| Home, End | first or last beat |
| N | show the "sheet · beat" counter that matches `notes.md` |
| F | fullscreen |

### Memory lab

The lab simulates real logic gates. Every gate takes one step (one "gate delay") to respond, so slow motion shows signals moving through the circuit one gate at a time.

- **Modes:**
  - SR latch (two NOR gates).
  - D latch (NOT, two AND gates and an SR latch).
  - D flip-flop (master and slave latches).
  - Compare, where a latch and a flip-flop share the same inputs.
- **Controls:**
  - Hold set and reset.
  - Toggle D.
  - Clock on auto, or manual with Tick.
  - Clock period.
  - 1x, 0.25x and 0.1x speed.
  - Pause and single step.
  - Show inside wires.
- **Keys** (only while the lab is on screen):
  - S and R hold.
  - D toggles.
  - C ticks.
  - P pauses.
  - The . key steps.
  - 1, 2 and 3 set the speed.

Releasing S and R together makes the latch wobble. Real gates are never exactly equal, so after a few wobbles the simulator lets one side win at random.

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
