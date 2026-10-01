# Speaker notes: Electronic Timing Circuits (Group 10)

A general overview of about 16 to 17 minutes at a quick pace, then questions, for a 15 to 20 minute slot. No math. The audience only needs to know that "on" can mean 1 and "off" can mean 0.

## How to drive the page

- **Next beat:** →, ↓, Page Down or Space. A presentation clicker sends these keys too. A mouse wheel or a swipe also works.
- **Previous beat:** ←, ↑ or Page Up.
- **First and last beat:** Home and End.
- **N** shows a small counter, for example "sheet 7 · beat 2". The headings below use the same numbers.
- **F** toggles fullscreen.
- **L** turns off the hand-drawn wobble, in case an old laptop struggles.
- **Quiz keys (sheets 15 to 17):** Q flips the next clue card, Shift+Q hides the last one, A shows or hides the answer. Nothing else reveals clues, so scrolling or clicking is safe.
- **Lab keys (sheet 13 only):** hold S or R for SET and RESET, G swaps NOR and NAND gates, B swaps the bucket size, P swaps the pipe.

Each beat stops on a finished picture that keeps moving. Say your line, then press next.

## Timing plan

| Sheet | Topic | Target | Running total |
|---|---|---|---|
| 1 | Cover | 0:30 | 0:30 |
| 2 | Timers are everywhere | 0:45 | 1:15 |
| 3 | Why keep time | 1:00 | 2:15 |
| 4 | Timing with a bucket | 1:00 | 3:15 |
| 5 | The 555 timer | 1:00 | 4:15 |
| 6 | Inside the 555 | 1:00 | 5:15 |
| 7 | The NOR SR latch, step by step | 2:30 | 7:45 |
| 8 | The NAND SR latch, step by step | 3:00 | 10:45 |
| 9 | The 555 loop | 0:45 | 11:30 |
| 10 | Three ways to use it | 1:00 | 12:30 |
| 11 | Quartz | 1:00 | 13:30 |
| 12 | Inside a computer | 1:00 | 14:30 |
| 13 | Try it | 1:30 | 16:00 |
| 14 | Recap and questions | 0:30 | 16:30 |
| 15 to 17 | Quiz, 3 questions | 4:00 | 20:30 |

The full plan runs a little over 20 minutes, so plan one cut in advance. If you run long, use fewer clues per question, skip the lab, cut sheet 10 to one beat, or skip beat 8.9 (the 7400 chip). If you run short, let someone from the audience drive the lab.

---

## Sheet 1 · Cover (0:30)

**1.1** "We are Group 10, and our topic is electronic timing circuits. A timing circuit is any circuit that knows how long to wait. In the next few minutes we go from a bucket of water to the clock inside your laptop, and on the way we open up one tiny memory called the SR latch."

## Sheet 2 · Timers are everywhere (0:45)

**2.1** "Look around. A car's blinker, a traffic light, a microwave counting down, a watch, a washing machine, a computer. Every one of these has a timing circuit inside. Some blink, some count down, some keep a steady beat."

## Sheet 3 · Why keep time (1:00)

**3.1** "Three signals leave at the same moment over wires of different lengths. The short one arrives first, the long one arrives late. If we read too early, we get some new values and some old ones. That mix is wrong."

**3.2** "The fix is a shared beat, like a drummer in a band. Everyone waits for the tick, then reads together. That shared beat is called a clock. So where does a beat come from?"

## Sheet 4 · Timing with a bucket (1:00)

**4.1** "The simplest timer is a bucket and a narrow pipe. The bucket is a **capacitor**: it stores electricity. The narrow pipe is a **resistor**: it slows the flow. The bucket fills fast at first, then slower as it gets full. The card on the table draws that: up means fuller, right means later."

**4.2** "Now a bigger bucket with the same pipe. It takes longer. A narrower pipe would do the same. So by picking the parts, we pick the time."

## Sheet 5 · The 555 timer (1:00)

**5.1** "One slow fill is not a beat yet. The 555 is a cheap and famous chip, made since 1972, billions of them. It fills the bucket, and when it is almost full, it drains it. When it is almost empty, it fills it again. Fill, drain, repeat. The light is on while it fills."

**5.2** "Now forget the curve and keep only the light. On is 1, off is 0. Every jump up is a tick. That is a clock."

## Sheet 6 · Inside the 555 (1:00)

**6.1** "Inside the chip there are two watchers. One keeps asking: is the bucket almost full? The other asks: is it almost empty?"

**6.2** "When the top one shouts 'full!', it presses a button called RESET, and the drain opens. When the bottom one shouts 'empty!', it presses SET, and the drain closes. Between the shouts, something has to remember which way we are going. That tiny memory is called an SR latch. Let's open it up."

## Sheet 7 · The NOR SR latch, step by step (2:30)

Go slowly here. This is the heart of the talk. The tracker at the bottom of the picture shows which step you are on.

**7.1** "Two gates in a loop. These are NOR gates. Each one has one simple rule: its output is on only when both of its inputs are off. The gates feed each other, so each one's output is the other one's input. The top light is called Q. That is our memory. Right now it is off."

**7.2** "Step 1: press SET. Watch the wires. SET turns on an input of the bottom gate, so the bottom gate turns off. Now the top gate sees two offs, so Q turns on."

**7.3** "Step 2: let go of SET. Q stays on. Why? Q itself feeds the bottom gate and keeps it off, so the loop holds itself. That is memory: the circuit remembers that we pressed SET."

**7.4** "Step 3: press RESET. Now the top gate gets an input that is on, so Q turns off. That lets the bottom gate turn back on."

**7.5** "Step 4: let go. Q stays off. The latch remembers off, too."

**7.6** "Step 5: what if you press both? Both gates turn off, so both lights are off. They are supposed to be opposites. And if you let go of both at the very same moment, it is a coin toss which way it lands. So circuits never do that."

**7.7** "That is the whole trick. SET turns Q on. RESET turns Q off. Do nothing, and it remembers. Never press both."

## Sheet 8 · The NAND SR latch, step by step (3:00)

Same latch, built from the other popular gate. Keep it quick: the audience already knows the steps, so each beat is one or two sentences. The tracker at the bottom works like the one on sheet 7.

**8.1** "There is a twin. Same loop, but with NAND gates. A NAND gate flips the rule: its output is off only when both inputs are on. Any off input, and the output is on. Look at the four little rows: only the last one, on and on, turns the light off."

**8.2** "Here is the twist. In this version the button wires rest on, all the time. Pressing a button pulls its wire off. That is why you will see the names written with a bar on top, S-bar and R-bar. The bar means 'works when off'."

**8.3** "Step 1: press SET. Its wire turns off. That wire goes straight into the top gate, Q's own gate. One off input is enough, so Q turns on. Now the bottom gate sees two ons, RESET resting on and Q on, so the opposite turns off."

**8.4** "Step 2: let go. SET's wire is back on, but Q stays on. The opposite is off, and an off input keeps the top gate on. Memory again."

**8.5** "Step 3: press RESET. Its wire turns off, so the bottom gate turns on: the opposite lights up. Now the top gate sees two ons, so Q turns off."

**8.6** "Step 4: let go. Q stays off. It remembers off too."

**8.7** "Step 5: press both. Both wires are off, so both gates turn on and both lights are on. The NOR latch did the reverse: both off. Either way they are no longer opposites. Let go of both together and it is a coin toss, so this is still not allowed."

**8.8** "Side by side. NOR buttons rest off and a press pushes a wire on. NAND buttons rest on and a press pulls a wire off. In NOR, SET talks to the other gate. In NAND, SET talks to Q's own gate. And pressing both gives both lights off in NOR, both on in NAND. Same job: set, reset, remember."

**8.9** "Why bother with NAND? NAND gates are small and fast to make, so they are the favorite brick. One tiny chip, the 7400, has four of them inside. And with enough NAND gates you can build any logic at all, even a whole computer."

**8.10** "A real job for it, and it is about timing. Metal buttons bounce. One press makes a quick clatter, on, off, on, off, in a few thousandths of a second. A computer would count that as many presses. So we use a two-sided switch: one side presses SET, the other presses RESET. The first touch flips the latch, and the bounces only tap the same side again, which changes nothing. One press, one clean step."

## Sheet 9 · The 555 loop (0:45)

**9.1** "Now the 555 makes sense. Follow the red dot. Fill until almost full, then RESET, so it drains. Drain until almost empty, then SET, so it fills. The latch in the middle remembers whether we are filling or draining. Round and round, and that is the beat."

## Sheet 10 · Three ways to use it (1:00)

**10.1** "The same chip can be used three ways. One-shot: press once, the light stays on for a set time, then turns off by itself. Like a stairway light or a hand dryer."

**10.2** "Blinker: fill, drain, repeat, forever. Like a turn signal or a bike light."

**10.3** "On and off: use just the latch. SET turns it on, RESET turns it off, and it stays that way. Like the start and stop buttons on a machine."

## Sheet 11 · Quartz (1:00)

**11.1** "Buckets are not very precise. They change with heat and with age, so their timing drifts. Real clocks use a tiny quartz crystal. Give it power and it shakes at a very steady speed. Your watch has one inside."

**11.2** "It shakes 32,768 times a second, far too fast for a watch. So a chain of small circuits slows it down. Each step in the chain blinks half as often as the one before. At the end of the chain: exactly one tick per second."

## Sheet 12 · Inside a computer (1:00)

**12.1** "A laptop's clock ticks about 3 billion times every second. One tick is so short that light, the fastest thing there is, only travels about a hand's width."

**12.2** "Computers use a latch that only listens on the tick. It is called a flip-flop. It works like a camera: it takes one snapshot of the data on each tick and ignores the wobbling in between. Look at the red line: it only changes when the camera flashes. That way every part of the computer saves at the same moment."

## Sheet 13 · Try it (1:30)

Live demo. A good order:

1. Hold **SET**: Q turns on. Let go: it stays on. That is memory. Tap **RESET**: it turns off and stays off.
2. Press **Press both**. It holds both, then lets go of both at once. The lights wobble, then one side wins at random.
3. Press **NAND** at the top of the latch card (or G) and do the same. The wires now rest on, and "Press both" lights both lamps instead of none.
4. On the right, switch the bucket to **big**, then the pipe to **narrow**. Each change makes the light blink more slowly. The strip below the bucket draws the on and off beat.

## Sheet 14 · Recap and questions (0:30)

**14.1** "A bucket and a pipe measure time. The 555 fills and drains to make a beat. An SR latch, built from NOR or NAND gates, remembers: SET for on, RESET for off. And quartz keeps it steady, so computers can save on every tick. Thank you. Questions?"

## Sheets 15 to 17 · Quiz (3 questions, about 4:00)

One question per sheet. On each one, give the room a moment, then press Q for a clue as needed. Press A to stamp the answer. Each sheet remembers its own clues, so going back keeps them open.

### 15 · Who wins?

**Question:** "In the version 2 latch, both buttons are held. Then you let go of RESET first, and SET a split second later. When it settles, which light is on: Q or the opposite?"

**Answer: Q.** The last one held wins. While SET is still held, it forces Q on, and Q plus the resting RESET wire turn the opposite off. Letting go of SET then changes nothing.

1. Version 2 is the NAND latch. Its buttons rest on, and a press pulls a wire off.
2. While both buttons are held, both lights are on. That is step 5.
3. Let go of RESET and its wire is back on. SET is still held, so SET's wire is still off.
4. One off input keeps a NAND gate on, so Q stays on. The bottom gate now sees RESET on and Q on.
5. Two ons turn a NAND gate off. The opposite goes dark, and when SET lets go, the latch remembers.

### 16 · The light that won't quit

**Question:** "A 555 blinker's light turns on and never turns off. Its almost full watcher is broken. Which button never gets pressed, and what is the bucket doing?"

**Answer: RESET is never pressed.** The drain never opens, so the bucket fills up and stays full, and the light stays on.

1. Inside the 555: two watchers, one for "almost full", one for "almost empty".
2. When the top watcher shouts "full!", it presses one of the two latch buttons.
3. That button is RESET, and RESET is what opens the drain.
4. No shout means no RESET, so the drain stays shut.
5. The bucket fills and stays full. The light is on while filling, so it never goes off.

### 17 · The broken chain

**Question:** "In a quartz watch, one step of the halving chain is skipped. Does the watch run fast or slow, and by how much?"

**Answer: fast, twice as fast.** One fewer halving means 2 ticks per second instead of 1.

1. The crystal shakes 32,768 times a second, far too fast for a watch.
2. Each step in the chain blinks half as often as the one before.
3. The chain is built so the last step gives exactly one tick per second.
4. Skip any one step and you lose one halving.
5. So the end of the chain ticks twice every second, not once.

---

## Likely questions

**Why do computers need a clock at all?**
Signals take different amounts of time to arrive. The clock tells every part when it is safe to read, so they all act together.

**What does the SR in SR latch mean?**
Set and Reset, the two buttons.

**Why use quartz instead of a 555?**
A 555 depends on its bucket and pipe, and those change with heat and age. Quartz shakes at a very steady rate, so the clock stays accurate.

**Why 32,768?**
It halves evenly, again and again, down to exactly one. That makes it easy to slow down with a simple chain of circuits.

**What happens if you press both buttons on the latch?**
Both outputs turn off, so they are no longer opposites. If you let go of both together, it becomes a race and the result is random. That is why circuits avoid it.

**Why are the NAND buttons "upside down"?**
A NAND gate's output only changes when an input goes off. So the inputs rest on, and a press pulls one off. Engineers call that "active low" and mark it with a bar over the name.

**Which one is better, NOR or NAND?**
They do the same job. NAND is more common because NAND gates are smaller and faster to build, and a cheap chip like the 7400 has four of them.

**What does "debouncing" mean?**
Cleaning up a bouncy button so one press counts once. The NAND latch flips on the first touch and ignores the bounces.

**What is the difference between a latch and a flip-flop?**
A latch reacts whenever its inputs change. A flip-flop only takes in new data on the tick of a clock, like a camera taking one photo per tick.
