# Speaker notes: From Ticks to Memory

About 12 minutes of talk, then questions. No math needed. The audience only needs to know that computers use 0 and 1, and how to read a binary number.

## How to drive the page

- **Next beat:** →, ↓, Page Down or Space. A presentation clicker sends these keys too.
- **Previous beat:** ←, ↑ or Page Up.
- **First and last beat:** Home and End.
- **N** shows a small counter in the corner, for example "sheet 7 · beat 2". The headings below use the same numbers.
- **F** toggles fullscreen.
- **The lab has its own keys:**
  - Hold S or R for set and reset.
  - D flips D, and C ticks the clock.
  - M toggles slow motion, and P pauses.

Each beat stops on a finished picture. Say your line, then press next.

## Timing plan

| Sheet | Topic | Target | Running total |
|---|---|---|---|
| 1 | Intro | 0:30 | 0:30 |
| 2 | Why keep time | 0:50 | 1:20 |
| 3 | Timing with a bucket | 0:50 | 2:10 |
| 4 | The 555 timer | 0:50 | 3:00 |
| 5 | The clock | 1:00 | 4:00 |
| 6 | Gates | 0:50 | 4:50 |
| 7 | The SR latch | 1:10 | 6:00 |
| 8 | Latch vs flip-flop | 0:50 | 6:50 |
| 9 | Bits to bytes | 0:40 | 7:30 |
| 10 | The cost of a bit | 0:30 | 8:00 |
| 11 | DRAM | 1:10 | 9:10 |
| 12 | Flash | 1:00 | 10:10 |
| 13 | Compare | 0:30 | 10:40 |
| 14 | Memory lab | 1:00 | 11:40 |
| 15 | Recap and questions | 0:20 | 12:00 |

If you run long, shorten the lab. If you run short, let someone from the audience drive the lab.

---

## Sheet 1 · Intro (0:30)

**1.1** "Every computer does two things all the time. It keeps time, and it remembers. Today we go from the first to the second. We start with one blinking light and end with the chips inside your phone."

Point at the light. "This light blinks because a signal goes up and down. By the end you will know where that beat comes from, and how a circuit uses it to remember."

## Sheet 2 · Why keep time (0:50)

**2.1** "Three signals leave at the same moment, over wires of different lengths. The short one arrives first. The long one arrives last. If we read at the dashed line, two are new and one is old. That mix is wrong."

**2.2** "The fix is a shared beat, like a drummer in a band. Everyone agrees to read only on the tick. Between ticks, signals have time to arrive. On the tick, they all agree. That shared beat is called a clock. So where does a beat come from?"

## Sheet 3 · Timing with a bucket (0:50)

**3.1** "The simplest timer is a bucket and a narrow pipe. The bucket is a **capacitor**. It stores electricity. The narrow pipe is a **resistor**. It slows the flow. Close the switch and the bucket starts to fill. It fills fast at first, then slower as it gets full. The screen is like a heart monitor: up means fuller, right means later."

**3.2** "The dashed line is a bigger bucket. It takes longer. So by picking the parts, we pick how long it takes. That is how a circuit measures time."

## Sheet 4 · The 555 timer (0:50)

**4.1** "One slow fill is not a beat yet. The 555 is a cheap and famous chip that repeats it. When the bucket reaches 2/3 full, the chip drains it. At 1/3, it lets it fill again. Fill, drain, fill, drain. That is a steady beat."

**4.2** "Inside the chip, two watchers keep an eye on the level. When one of them trips, it flips a tiny memory called a **flip-flop**, and the flip-flop opens or closes the drain. Remember that word. We need it later."

## Sheet 5 · The clock (1:00)

**5.1** "We do not care about the wavy shape. We only keep the on and off. On while filling, off while draining. On is 1, off is 0. Every jump up is a tick. That is a clock."

**5.2** "Buckets are not very precise, so real clocks use quartz. A tiny quartz crystal shakes 32,768 times a second, very steadily. That number is a power of two. You all know what halving does in binary. Each flip-flop in this chain halves the beat. After 15 of them, you get exactly one tick per second. That is how your watch counts seconds."

**5.3** "A laptop ticks about 3 billion times a second. One tick is so short that light, the fastest thing there is, only travels about a hand's width. Engineers really have to worry about how long wires are."

## Sheet 6 · Gates (0:50)

**6.1** "Now, the parts that remember. It starts with the transistor. A transistor is a switch, but you flip it with electricity instead of a finger. Power on its gate lets current through. No power, no current. A modern chip has billions of them."

**6.2** "Put a few transistors together and you get a logic gate. NOT flips its input: 0 becomes 1, 1 becomes 0. NOR gives a 1 only when both inputs are 0. Watch the table light up row by row. Keep NOR in mind, because next we loop two of them together."

## Sheet 7 · The SR latch (1:10)

**7.1** "Two NOR gates, each feeding its output into the other. Follow the steps at the bottom. Press SET. The bottom gate goes to 0. Now the top gate sees 0 and 0, so it outputs 1. That 1 feeds back around. Now let go of SET. Nothing changes. The loop holds itself. That is one bit of memory."

**7.2** "RESET does the opposite. Q drops to 0, and when you let go it stays 0."

**7.3** "Q and Q-bar are supposed to be opposites. Press both buttons and they are both 0, which breaks the rule. If you let go of both at the same time, it is a race, and it lands on 0 or 1 at random. So the rule is: never press both."

## Sheet 8 · Latch vs flip-flop (0:50)

**8.1** "Real memory needs to store data at the right time. D is the data, CLK is the clock. A D latch is like an open door. While the clock is high, Q copies D the whole time, even if D is wobbling around. Look at the shaded windows."

**8.2** "A D flip-flop is like a camera flash. It takes one snapshot of D at the instant the clock goes up, then ignores D until the next tick. Compare the purple line with the blue one. This is why computers use flip-flops: every part changes at exactly the same moment."

## Sheet 9 · Bits to bytes (0:40)

**9.1** "One flip-flop holds one bit. Line up eight and you have a byte. 01000001 in binary is 65, and computers use 65 for the capital letter A."

**9.2** "A register is the processor's notepad. 64 flip-flops side by side hold one 64-bit number. On every tick, they all update together."

## Sheet 10 · The cost of a bit (0:30)

**10.1** "So why not build all memory from flip-flops? Each one needs about 20 transistors for one bit. Your RAM holds billions of bits, so that would be far too big and too expensive. The trick is a much smaller cell: one transistor and one tiny bucket. That is DRAM."

## Sheet 11 · DRAM, your computer's RAM (1:10)

**11.1** "Here is DRAM. Each dot is one tiny bucket with a tap. Full means 1, empty means 0. The chip opens a whole row of taps at once."

**11.2** "The problem: the bucket leaks. The level slowly drops. Wait too long and a 1 falls below the line and looks like a 0."

**11.3** "So the chip tops every row back up, many times a second, forever. Fill, leak, fill, leak. It looks just like the 555 from earlier. This is why RAM needs power all the time."

**11.4** "Reading is strange too. When you read a cell, the charge spills out. The chip checks whether it was a 1 or a 0, then fills it back. And when the power goes off, everything is forgotten. That is why unsaved work disappears."

## Sheet 12 · Flash, your SSD (1:00)

**12.1** "Flash memory, in your SSD and your phone, remembers without power. Each cell has a tiny pocket wrapped in insulation. Electrons locked in the pocket stay there for years, even with the power off."

**12.2** "Getting electrons in is the hard part. It takes a strong push to force them through the insulation. Each push damages it a little. After thousands of writes, a cell wears out. Your SSD spreads writes around so no cell wears out too early."

**12.3** "Two tricks make flash cheap. First, a pocket can be filled to 8 different levels. 8 levels hold 3 bits, as you can see from the binary labels. Second, the cells are stacked like a skyscraper, over 200 floors high. Cheap and huge, but slower than RAM."

## Sheet 13 · Compare (0:30)

**13.1** "So we have three kinds of memory. Flip-flops are like your hands: very fast, but you can hold only a little. DRAM is your desk: big and quick, but cleared when you leave. Flash is a bookshelf: huge and permanent, but slower to reach. A computer uses all three."

## Sheet 14 · Memory lab (1:00)

**14.1** Live demo. A good order:

1. SR latch. Hold **Set**: Q turns on. Let go: it stays on. That is memory. Tap **Reset**: it clears.
2. Turn on **Slow motion** and press **Press both, then let go**. Q and Q-bar flip back and forth, then one side wins at random.
3. Switch to **D flip-flop**. Flip **D** a few times. Point out that Q only changes when the green CLK line steps up.
4. If there is time, press **Tick** to step the clock yourself. Or invite someone from the audience.

## Sheet 15 · Recap and questions (0:20)

**15.1** Read the four lines. "A bucket measures time. A clock turns it into ticks. Gates in a loop remember. And the memory in your devices trades speed, size and lasting power. Questions?"

---

## Likely questions

**Why do computers need a clock at all?**
Signals take different amounts of time to arrive. The clock tells every part when it is safe to read, so they all act together.

**Why use quartz instead of a 555?**
A 555 depends on its parts, and they change with heat and age. Quartz shakes at a very steady rate, so the clock stays accurate.

**Why 32,768?**
It is a power of two. Halving it 15 times gives exactly one tick per second, and halving is easy for a flip-flop.

**What happens if you press both buttons on the latch?**
Q and Q-bar are no longer opposites. If you let go of both together, it becomes a race and the result is random. That is why circuits avoid it.

**Why does RAM forget when the power is off?**
Each bit is a tiny bucket of charge that leaks. Without power, nothing tops it up, so it drains in a moment.

**Why does an SSD not forget?**
Its electrons are locked in an insulated pocket. They cannot leak out without a strong push.

**Why do SSDs wear out?**
Every write pushes electrons through the insulation, and that slowly damages it. Modern SSDs last for many years of normal use.

**Why not use flash for everything?**
It is too slow to write, and it wears out. The processor needs something fast that can change billions of times a second.
