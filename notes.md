# Speaker notes: From Ticks to Memory

About 15 minutes of talk, then about 5 minutes of questions.

## How to drive the page

- **Next beat:** →, ↓, Page Down or Space. A presentation clicker sends these keys too.
- **Previous beat:** ←, ↑ or Page Up.
- **First and last beat:** Home and End.
- **N** shows a small counter in the corner, for example "sheet 7 · beat 2". The headings below use the same numbers.
- **F** toggles fullscreen.
- **The lab has its own keys:**
  - S and R hold set and reset.
  - D toggles D, and C ticks the clock.
  - P pauses, and the . key steps one gate delay.
  - 1, 2 and 3 set the speed.

Each beat stops on a finished picture. Say your line, then press next.

## Timing plan

| Sheet | Topic | Target | Running total |
|---|---|---|---|
| 1 | Intro | 0:30 | 0:30 |
| 2 | Why keep time | 1:00 | 1:30 |
| 3 | Timing with a bucket | 1:15 | 2:45 |
| 4 | The 555 timer | 1:15 | 4:00 |
| 5 | The clock | 1:15 | 5:15 |
| 6 | Gates | 1:00 | 6:15 |
| 7 | The SR latch | 1:30 | 7:45 |
| 8 | Latch vs flip-flop | 1:15 | 9:00 |
| 9 | Bits to bytes | 0:45 | 9:45 |
| 10 | The cost of a bit | 0:45 | 10:30 |
| 11 | DRAM | 1:30 | 12:00 |
| 12 | NAND flash | 1:30 | 13:30 |
| 13 | Compare | 0:45 | 14:15 |
| 14 | Memory lab | 1:00 | 15:15 |
| 15 | Recap and questions | 0:15 | 15:30 |

If you run long, shorten sheet 10 and the lab first.

---

## Sheet 1 · Intro (0:30)

**1.1** "Every computer does two things all the time. It keeps time, and it remembers. Today we go from the first to the second. We start with a single blinking light and end with the chips inside your phone."

Point at the LED. "This light blinks because a signal goes up and down. By the end you will know how a circuit makes that beat, and how it uses the beat to remember things."

## Sheet 2 · Why keep time (1:00)

**2.1** "Imagine three messages leaving at once over three wires of different lengths. The short one arrives first and the long one arrives last. If the reader looks at the dashed line, it sees two new values and one old one. That mix is garbage."

**2.2** "The fix is a shared beat. Everyone agrees to read only on the tick. Between ticks, signals have time to settle. On the tick, every value is new, so every part of the chip acts together. That shared beat is called a clock. So where does a beat come from?"

## Sheet 3 · Timing with a bucket (1:15)

**3.1** "The simplest timer is a bucket and a narrow pipe. The bucket is a **capacitor**, which stores electric charge. The narrow pipe is a **resistor**, which slows the flow down. Close the switch and charge flows in. It fills fast at first, then slower and slower as the bucket gets full. The screen works like a heart monitor: up means more voltage, right means later. The important part is that filling takes a predictable amount of time."

**3.2** "Engineers call that time the **time constant**, written τ, the Greek letter tau. τ is R times C: the resistance times the capacitance. After one τ the bucket is 63 percent full. After five τ it is basically full. With a 10 kilohm resistor and a 100 microfarad capacitor, τ is exactly one second. The dashed curve is a bucket twice as big: it takes twice as long. So choosing two parts sets a time."

## Sheet 4 · The 555 timer (1:15)

**4.1** "One fill is a one-shot timer. For a beat, we need it to repeat. The **555** is a chip from 1972, and billions have been made. It watches the bucket. At two thirds full, it opens a drain. At one third, it closes the drain again. Fill, drain, fill, drain. That is the sawtooth on the screen."

**4.2** "Inside, two comparators act as watchers. One asks 'are we above two thirds?' The other asks 'are we below one third?' They flip a tiny one-bit memory called a **flip-flop**. The flip-flop works the drain switch and the output pin. Keep that flip-flop in mind. Memory is already hiding inside our timer."

**4.3** "The speed is set by the parts. The formula is on screen, but the idea is simple: bigger resistors or a bigger capacitor give a slower beat. The 555 is great for blinking lights, buzzers and toys. It drifts with temperature, though, so computers need something steadier."

## Sheet 5 · The clock (1:15)

**5.1** "If we only look at the 555's output pin, it is on while filling and off while draining. That on-off shape is a **square wave**. High means 1, low means 0. Every jump up is a **tick**. This is a clock."

**5.2** "Real clocks use a **quartz crystal**. When you squeeze quartz it makes a voltage, and a voltage makes it bend. Cut it the right size and it rings like a tuning fork, very steadily. Watch crystals ring 32,768 times a second. That odd number is 2 multiplied by itself 15 times. Each flip-flop can halve a beat. Chain 15 of them and you get exactly one tick per second. That is how a quartz watch counts seconds."

**5.3** "Computers go much faster. A laptop processor ticks about 3 billion times a second, which is 3 gigahertz. A circuit called a **phase-locked loop**, or PLL, takes a steady reference clock, say 100 megahertz, and multiplies it up. At 3 gigahertz, one tick lasts a third of a nanosecond. In that time light travels only 10 centimeters. That is one reason chips are small."

## Sheet 6 · Gates (1:00)

**6.1** "Now, the parts that decide things. A **transistor** is a switch with no moving parts. Think of a water valve. A small voltage on the transistor's **gate** opens the path, and current flows. Remove the voltage and it closes. A modern chip holds billions of these."

**6.2** "Wire a few transistors together and you get a **logic gate**. A NOT gate flips its input: 0 becomes 1, 1 becomes 0. A NOR gate outputs 1 only when both inputs are 0. Watch the table light up row by row. Here is the surprising part: loop two NOR gates into each other and you get memory."

## Sheet 7 · The SR latch (1:30)

**7.1** "This is an **SR latch**, for set and reset. Each gate's output feeds the other's input. Q is the output. Q-bar is its opposite. Let's step through. One: press SET. Two: the bottom gate now sees a 1, so its output, Q-bar, drops to 0. Three: the top gate now sees 0 and 0, so Q rises to 1. Four: let go of SET. Q is still 1, because Q feeds back and holds itself. Nothing is pressed, yet the circuit remembers. That is the whole trick of memory: a loop that holds itself."

**7.2** "RESET does the opposite. Press it and Q drops to 0, Q-bar rises to 1. Let go and it stays reset."

**7.3** "What if you press both? Both outputs go to 0, which breaks the rule that they are opposites. Worse, if you let go of both at the same instant, the two gates race. Whichever is a hair faster wins, so the result is random. Designers avoid this case. You will see it wobble in the lab later."

## Sheet 8 · Latch vs flip-flop (1:15)

**8.1** "Pressing buttons is fine, but computers want to store data on the tick. The **D latch** adds a data input, D, and a clock input. Think of it as a door. While the clock is high, the door is open and Q copies D, even if D changes. Look at the shaded windows: every wiggle of D inside a window shows up in Q."

**8.2** "The **D flip-flop** is stricter. It is like a camera flash: it copies D only at the **rising edge**, the instant the clock goes up. Then it holds, no matter what D does. Compare the purple row with the blue one. The flip-flop changes only at the dashed lines. That is why computers use flip-flops: every part changes at the same instant, in step with the clock. Inside, a flip-flop is just two latches back to back, one open while the clock is low and one while it is high."

## Sheet 9 · Bits to bytes (0:45)

**9.1** "One flip-flop holds one **bit**, a 0 or a 1. Eight in a row hold a **byte**. The pattern 01000001 is the number 65, and text files use 65 to mean the capital letter A."

**9.2** "Line up 64 flip-flops and you have a 64-bit **register**. Registers hold the numbers the processor is working on right now. On every tick, all of them can update together."

## Sheet 10 · The cost of a bit (0:45)

**10.1** "So why not build all memory from flip-flops? Cost. A flip-flop takes about 20 transistors for one bit. **SRAM**, used for the processor's cache, takes 6. **DRAM**, your computer's main memory, takes just 1 transistor and 1 tiny capacitor."

**10.2** "16 gigabytes of RAM is about 128 billion bits. As flip-flops, that would be over 2.5 trillion transistors, far too big and too hot. So we trade some speed for size."

## Sheet 11 · DRAM (1:30)

**11.1** "A DRAM cell is our bucket again, with a tap. A full bucket means 1, an empty bucket means 0. The cells sit in a grid. A **word line** opens a whole row of taps at once, and the **bit lines** carry each cell's charge out."

**11.2** "The problem is that these buckets are tiny and they leak. The charge slowly escapes. Wait too long and a 1 looks like a 0."

**11.3** "So the memory chip **refreshes**. At least every 64 milliseconds, every row is read and topped back up. Fill, leak, fill, leak. Look at the screen: it is the sawtooth again, just like the 555. Your RAM does this thousands of times a second, even while the computer sits idle."

**11.4** "Reading is destructive. Opening the tap spills the charge onto the bit line, so the bucket is partly empty afterwards. A **sense amplifier** decides whether it was a 0 or a 1, then writes the value straight back. Cut the power and refresh stops. Within seconds to a minute, everything fades. That is what **volatile** means."

## Sheet 12 · NAND flash (1:30)

**12.1** "Your SSD and your phone keep data with the power off. They use **NAND flash**. Each cell has a pocket, called a floating gate or charge trap, wrapped completely in insulation. Electrons trapped in there change how the transistor behaves, and that is how the cell is read. The insulation is so good that electrons stay for years. That is **non-volatile**."

**12.2** "How do electrons get through an insulator? With a strong push, about 20 volts, they cross it by a quantum effect called **tunneling**. Each trip damages the insulation a little. That is why flash wears out. A common TLC cell is rated for roughly 1,000 to 3,000 write cycles."

**12.3** "Flash has an awkward rule. You write one **page** at a time, around 16 kilobytes. But you can only erase a whole **block**, which is hundreds of pages. So the SSD's controller constantly moves data around and spreads writes across all cells. This is called wear leveling."

**12.4** "Two tricks make flash cheap. First, a cell does not just store full or empty. A TLC cell stores 8 different charge levels, which is 3 bits. Second, cells are stacked in 3D, over 200 layers tall, like floors of a skyscraper. The name NAND comes from how cells are wired in series, like the transistors inside a NAND gate."

## Sheet 13 · Compare (0:45)

**13.1** "Here are all three side by side. Flip-flops and SRAM are fastest, about a nanosecond, but they cost the most space per bit. DRAM is about 50 nanoseconds and dense, but it forgets without power. Flash is slowest, about 50 microseconds to read, but it remembers for years and is the cheapest per bit. A computer uses all three: your hands, your desk, and your bookshelf."

## Sheet 14 · Memory lab (1:00)

**14.1** Live demo. Suggested order:

1. **SR latch.** Tap S, then R. "It remembers." Set the speed to 0.1x and press "S and R, then let go". "Watch it wobble, then land at random."
2. **D latch.** Press D a few times while CLK is high, then while it is low. "Door open, door shut."
3. **Compare.** Toggle D while CLK is high. "The latch follows at once. The flip-flop waits for the edge."
4. Optional: turn on "Show inside wires" in D flip-flop mode. Point at the master copy, then press Pause and Step to walk through one gate delay at a time.

The simulator gives every gate exactly the same delay. That is why the SR wobble can happen at all. Real gates are never perfectly equal, so a real latch settles to one side, and nobody can predict which.

## Sheet 15 · Recap and questions (0:15)

**15.1** "To sum up. A bucket and a pipe turn charge into time. A clock turns time into ticks. Gates in a loop hold a bit, and a flip-flop stores it on the tick. Fast flip-flops, dense DRAM and lasting flash each trade speed, size and power. Questions?"

---

## Likely questions

**Why does DRAM need refresh but SRAM does not?**
An SRAM cell is a small latch, a loop of transistors that actively holds itself, like the SR latch. A DRAM cell is a passive capacitor that leaks, so something has to top it up.

**Why do SSDs wear out?**
Every write and erase pushes electrons through a thin insulating layer at high voltage. That slowly damages the layer until the cell cannot hold charge reliably. Controllers spread writes out and keep spare cells to delay this.

**How long does an SSD last in practice?**
For normal home use, usually many years. Drives are rated in total terabytes written. A typical 1 TB drive is rated for hundreds of terabytes, far more than most people write.

**What is metastability?**
It is the "coin toss" from the SR latch and the lab. If a flip-flop's input changes right at the clock edge, the loop can balance in the middle for a moment before falling to 0 or 1. Designers add rules about timing, plus extra flip-flops, so it almost never matters.

**Why not use a 555 as a computer's clock?**
Its timing depends on resistor and capacitor values that drift with temperature and age, by around a percent or more. A quartz crystal is steady to about a few parts per million, and it can ring much faster.

**If the clock is 3 GHz, why can't it go faster?**
Each tick must be long enough for signals to cross the gates and settle. Faster ticks also use more power and make more heat. Around 3 to 5 GHz, heat becomes the limit, so chips add more cores instead.

**Does RAM really lose everything when you turn it off?**
Yes, within seconds to about a minute at room temperature. Very cold RAM can hold data longer, and security researchers have shown attacks based on that.

**What is cache?**
Small, fast SRAM memory on the processor. It keeps copies of data from RAM that the processor is likely to need soon, because going out to DRAM takes many ticks.

**Is flash the same as the memory in a USB stick or an SD card?**
Yes. Phones, SSDs, USB sticks and SD cards all use NAND flash. They differ in the controller and how many chips they use.

**What does "volatile" mean exactly?**
Memory that needs power to keep its data. Flip-flops, SRAM and DRAM are volatile. Flash is non-volatile.

**What are SLC, MLC, TLC and QLC?**
1, 2, 3 and 4 bits per cell. More bits per cell means more levels to tell apart. That makes flash cheaper and denser, but slower and less durable.

**Is anything replacing these?**
Researchers work on memories that are fast like DRAM and permanent like flash, using magnetism (MRAM) or material changes (phase-change memory). Some are already used in niche products, but DRAM and NAND still dominate.
