# Electronic Timing Circuits

Group 10. A hand-drawn, poster-style slide deck that gives a general overview of electronic timing circuits for people with no electronics background. There is no math. It runs about 13 minutes plus questions and is built for a TV.

The look is a retro packaging-poster style: cream paper, tomato red, sunshine yellow and cobalt blue, crayon scribbles, ink splats, sparkles, stickers, checkered tablecloths and little characters with faces. Outlines gently "boil" like hand-drawn animation.

Live site: https://gedon111.github.io/timing-to-memory/

## Files

- `index.html` is the whole site. It has no build step and no JavaScript libraries.
- `notes.md` is the speaker script, with time targets per sheet and likely questions with answers.

## Sheets

1. Cover
2. Timers are everywhere
3. Why keep time (signals arrive at different times, a clock is a shared beat)
4. Timing with a bucket (capacitor = bucket, resistor = narrow pipe)
5. The 555 timer (fill, drain, repeat; keep only on and off)
6. Inside the 555 (two watchers, SET and RESET, a tiny memory)
7. The SR latch, step by step (the loop, SET, let go, RESET, let go, never both, summary)
8. The 555 loop (the whole cycle around a wheel)
9. Three ways to use it (one-shot, blinker, on/off)
10. Quartz (a steadier beat, slowed down to one tick per second)
11. Inside a computer (billions of ticks, the flip-flop as a camera)
12. Try it (a live SR latch and a 555 blinker)
13. Recap and questions

## Presenting

The deck is a fixed 1920x1080 page that scales to fit any screen.

| Key | Action |
|---|---|
| → ↓ Page Down Space | next beat (clickers send these) |
| ← ↑ Page Up | previous beat |
| Home, End | first or last beat |
| N | show the "sheet · beat" counter that matches `notes.md` |
| F | fullscreen |
| L | turn the hand-drawn wobble off or on (also `?lite` in the URL) |

A mouse wheel, a swipe, or the dots at the bottom also move between slides. Links like `index.html#7.3` open a specific beat.

### The lab (sheet 12)

- **SR latch:** hold SET or RESET (or the S and R keys). "Press both" holds both, then lets go of both at once, so the latch wobbles and lands at random.
- **555 blinker:** pick a small or big bucket (B key) and a wide or narrow pipe (P key). A bigger bucket or a narrower pipe blinks more slowly. The strip below draws the on and off beat.

## Run it

Open `index.html` in a browser. Fonts (Bowlby One, Instrument Serif, Caveat, Bricolage Grotesque, Space Mono) load from Google Fonts and fall back to system fonts offline. Everything else is inline.

With reduced motion turned on, slide transitions and decorative motion are switched off.

## Publish with GitHub Pages

Settings > Pages > Build and deployment > Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)**.
