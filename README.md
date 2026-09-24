# From Ticks to Memory

A single-page scrolling explainer for people with no electronics background. It covers how a timing circuit keeps time, how that timing becomes a clock, and how a clock plus a latch gives you memory.

## Sheets

1. **Intro.** A looping pulse and a blinking LED.
2. **Keeping time.** An RC circuit (battery, switch, resistor, capacitor) explained as a bucket filled through a narrow pipe. Then a 555 timer chip turns the charge curve into a repeating fill-and-drain sawtooth.
3. **Making a clock.** The sawtooth morphs into a square wave. High is 1, low is 0, and each rise is a tick.
4. **Remembering.** An SR latch built from two cross-coupled gates, then a D flip-flop with a CLK, D and Q timing diagram. The wave collapses into one bit.
5. **Recap and try it.** An interactive SR latch (hold SET or RESET) and a D flip-flop (toggle D, press Tick).

## Run it

Open `index.html` in a browser. There is no build step. The page needs internet access because it loads GSAP 3.13 (core, ScrollTrigger, MorphSVGPlugin) from the jsDelivr CDN. Without GSAP, the text and the two interactive toys still work, but the animated diagrams are hidden.

The page is landscape only. On a portrait screen it asks you to rotate the device. If your system has reduced motion turned on, the page skips the smooth scrubbing and loops and jumps straight to each finished diagram.

## Publish with GitHub Pages

Settings > Pages > Build and deployment > Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)**. The site will appear at `https://<your-user>.github.io/timing-to-memory/`.

## Image credits

Every diagram and icon was drawn as inline SVG code by an AI assistant for this page, and each one has a visible "AI-generated" caption. The page uses no photos and no third-party images.

## Motion notes

Most animation uses only transform and opacity. There are two exceptions, and both only repaint without changing page layout. MorphSVG changes the hero path's shape between the sheets, and the latch's feedback loop animates `stroke-dashoffset`.
