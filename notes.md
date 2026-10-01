# Speaker notes: Electronic Timing Circuits (Group 10)

A general overview of about 13 minutes, then questions. No math. The audience only needs to know that "on" can mean 1 and "off" can mean 0.

## How to drive the page

- **Next beat:** →, ↓, Page Down or Space. A presentation clicker sends these keys too. A mouse wheel or a swipe also works.
- **Previous beat:** ←, ↑ or Page Up.
- **First and last beat:** Home and End.
- **N** shows a small counter, for example "sheet 7 · beat 2". The headings below use the same numbers.
- **F** toggles fullscreen.
- **L** turns off the hand-drawn wobble, in case an old laptop struggles.
- **Lab keys (sheet 12 only):** hold S or R for SET and RESET, B swaps the bucket size, P swaps the pipe.

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
| 7 | The SR latch, step by step | 2:30 | 7:45 |
| 8 | The 555 loop | 0:45 | 8:30 |
| 9 | Three ways to use it | 1:00 | 9:30 |
| 10 | Quartz | 1:00 | 10:30 |
| 11 | Inside a computer | 1:00 | 11:30 |
| 12 | Try it | 1:00 | 12:30 |
| 13 | Recap and questions | 0:30 | 13:00 |

If you run long, skip the lab or cut sheet 9 to one beat. If you run short, let someone from the audience drive the lab.

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

## Sheet 7 · The SR latch, step by step (2:30)

Go slowly here. This is the heart of the talk. The tracker at the bottom of the picture shows which step you are on.

**7.1** "Two gates in a loop. Each gate has one simple rule: its output is on only when both of its inputs are off. The gates feed each other, so each one's output is the other one's input. The top light is called Q. That is our memory. Right now it is off."

**7.2** "Step 1: press SET. Watch the wires. SET turns on an input of the bottom gate, so the bottom gate turns off. Now the top gate sees two offs, so Q turns on."

**7.3** "Step 2: let go of SET. Q stays on. Why? Q itself feeds the bottom gate and keeps it off, so the loop holds itself. That is memory: the circuit remembers that we pressed SET."

**7.4** "Step 3: press RESET. Now the top gate gets an input that is on, so Q turns off. That lets the bottom gate turn back on."

**7.5** "Step 4: let go. Q stays off. The latch remembers off, too."

**7.6** "Step 5: what if you press both? Both gates turn off, so both lights are off. They are supposed to be opposites. And if you let go of both at the very same moment, it is a coin toss which way it lands. So circuits never do that."

**7.7** "That is the whole trick. SET turns Q on. RESET turns Q off. Do nothing, and it remembers. Never press both."

## Sheet 8 · The 555 loop (0:45)

**8.1** "Now the 555 makes sense. Follow the red dot. Fill until almost full, then RESET, so it drains. Drain until almost empty, then SET, so it fills. The latch in the middle remembers whether we are filling or draining. Round and round, and that is the beat."

## Sheet 9 · Three ways to use it (1:00)

**9.1** "The same chip can be used three ways. One-shot: press once, the light stays on for a set time, then turns off by itself. Like a stairway light or a hand dryer."

**9.2** "Blinker: fill, drain, repeat, forever. Like a turn signal or a bike light."

**9.3** "On and off: use just the latch. SET turns it on, RESET turns it off, and it stays that way. Like the start and stop buttons on a machine."

## Sheet 10 · Quartz (1:00)

**10.1** "Buckets are not very precise. They change with heat and with age, so their timing drifts. Real clocks use a tiny quartz crystal. Give it power and it shakes at a very steady speed. Your watch has one inside."

**10.2** "It shakes 32,768 times a second, far too fast for a watch. So a chain of small circuits slows it down. Each step in the chain blinks half as often as the one before. At the end of the chain: exactly one tick per second."

## Sheet 11 · Inside a computer (1:00)

**11.1** "A laptop's clock ticks about 3 billion times every second. One tick is so short that light, the fastest thing there is, only travels about a hand's width."

**11.2** "Computers use a latch that only listens on the tick. It is called a flip-flop. It works like a camera: it takes one snapshot of the data on each tick and ignores the wobbling in between. Look at the red line: it only changes when the camera flashes. That way every part of the computer saves at the same moment."

## Sheet 12 · Try it (1:00)

Live demo. A good order:

1. Hold **SET**: Q turns on. Let go: it stays on. That is memory. Tap **RESET**: it turns off and stays off.
2. Press **Press both**. It holds both, then lets go of both at once. The lights wobble, then one side wins at random.
3. On the right, switch the bucket to **big**, then the pipe to **narrow**. Each change makes the light blink more slowly. The strip below the bucket draws the on and off beat.

## Sheet 13 · Recap and questions (0:30)

**13.1** "A bucket and a pipe measure time. The 555 fills and drains to make a beat. An SR latch remembers: SET for on, RESET for off. And quartz keeps it steady, so computers can save on every tick. Thank you. Questions?"

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

**What is the difference between a latch and a flip-flop?**
A latch reacts whenever its inputs change. A flip-flop only takes in new data on the tick of a clock, like a camera taking one photo per tick.
