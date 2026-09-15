# Mason Recreation **Aquatics** page — Pool Relay embed preview

An unofficial replica of [recreation.gmu.edu/aquatics](https://recreation.gmu.edu/aquatics/) with
**both** pool schedule PDFs replaced by live [Pool Relay](https://www.poolrelay.com) lane
calendars, plus masters swimming and swim lessons on the same page.

**This is not a George Mason University website.** The official site is
<https://recreation.gmu.edu>. The page says so in a ribbon across the top.

Previously this repo held a mock-up of the *competition pool* page only. It now covers the
Aquatics page, because that is where a swimmer actually lands and because the interesting part
is what happens when the two pools, the masters page and the lessons page are read together.

## The three calendars

| Section | Embed | Shape |
|---|---|---|
| Competition Pool | `2uFDBpnL1ugakkn8u8QEiQ` | Day, 20 short-course lanes |
| Recreation Pool | `Fp6ZUyUo00ARHTaJAVXPXl` | Day, 6 lanes |
| Both pools, one calendar | `UMoIDBjRcduOXwl9oe6J1q` | Day, with a **Pools** menu |

The third is the Stingrays pattern: `dimFilters.location` scopes the tab to this facility, so the
Pools menu offers **Competition Pool and Recreation Pool and nothing else** — not the other 57
pools in the system.

## What it replaces

```
Comp-Pool-No-Trinity_Master-26-27-11.pdf     20 lanes, a master for the year
Rec-Pool-9.14-9.20.26.pdf                     6 lanes + ramp, one single week
```

Two documents, two grid formats, two revision cadences, one building. A swimmer wanting a lane at
6pm had to open both, then check the masters page and the lessons page separately.

## What the calendar found

- ⛔ **Friday 5pm is labelled for an hour that is not there.** Lanes 14–16 say *"Open Swim
  5p–7p"*, but the block is drawn only to 6pm — at six the FFX Foxes take those lanes through
  7:15. The grid is ruled in one-hour rows, so a practice ending at 6:15 cannot be drawn honestly;
  that is how the label and the block came apart.
- ⛔ **Tuesday 8pm double-books the whole pool.** A *Splash Night* booking holds all twenty lanes
  8–10pm on top of Masters (1–8), Club Swim (1–8), the Foxes (9–16) and Nova Meteors (17–20). One
  of the two is wrong. *(Splash Night was already in the data and is not in revision 11 of the
  PDF, so it is the more likely candidate — but a PDF cannot raise the question at all.)*
- ⛔ **The swim lessons page is six months stale.** As of 2026-09-15 it still reads *"Registration
  for group lessons will open for Spring 2026 on January 19th, 2026, and close February 4th,
  2026"* and lists February/March class dates. There is no fall session on the page and nothing
  says there isn't one.
- ⛔ **The lessons page never says which pool.** Not for the group classes, not for the private
  ones. And no water is reserved for lessons on either pool schedule — the Wednesday 6pm class
  would need lanes the recreation pool grid gives to Mako.
- **The masters page is headed "Summer 2026 Practice Schedule"** and then lists no-practice dates
  running September through December 2026. Its times *do* match the competition pool grid exactly
  (Tue/Thu 7–8:30pm lanes 1–8; Fri 6–7:30pm lanes 17–20; Sat 10:30–12 lanes 9–16; Sun 8:15–9:45am
  lanes 9–16).
- **The recreation pool legend lists Mason Life and Streamline** and neither appears anywhere in
  the week that legend belongs to.
- **We had been reading revision 3.** This transcription is revision 11, and it added a great deal
  the earlier one had not: Mako's morning and evening blocks, FFX Foxes, Centreville Swim Club,
  the crew swim tests, Shark Tank, and several Club Swim sessions.

## How the PDFs were read

Not by eye. Both PDFs were rendered at 200 dpi and the **cell fills sampled per lane per row**, so
every lane span in the calendar is the span the PDF actually draws rather than a guess at where a
centered label ends. The legend colors are exact (`#FF0000` closed, `#00FF00` lane rental,
`#FFFF00` open swim, `#CC99FF` university clubs, `#FF99FF` class, white varsity), which makes the
read unambiguous. Cell rectangles were then decomposed by *color plus identical vertical run* and
clipped to the PDF's three lane blocks (1–8, 9–16, 17–20), and each rectangle matched to the
label printed inside it.

Two boundaries were checked a second time against a 300 dpi render — Monday 6:30am and Friday
5pm — because a one-lane error there would have been invisible and wrong.

## What is ours rather than theirs

- **The swim lesson pool is inferred.** The GMU page does not say. They are placed in the
  recreation pool because the competition pool is fully booked at every published lesson hour.
  Each lesson event says so in its description.
- **Open lap swimming is drawn as explicit blocks.** The recreation pool PDF uses yellow as a
  background default; a calendar has to say which lanes and when, so the lap-swim blocks are the
  yellow, made explicit.
- **Long-course lanes are excluded** from the competition pool calendar. The pool has a
  long-course configuration but the fall schedule is entirely short course.
- **"Splash Night" is pre-existing data**, not from either PDF.

## Known gaps

- The 47 competition-pool bookings added from revision 11 are entered **for the week of
  14–20 September only**, while the pool's earlier events recur weekly. Bulk edits were blocked in
  this session, so converting them to a standing weekly grid is outstanding.
- A **Pools page filter narrows the events but not the lane columns**, so the combined calendar
  shows the other pool's lanes as empty columns. That is why the page leads with one clean
  calendar per pool.

## Local preview

```
python3 -m http.server 8807
```
