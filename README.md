# Mason Recreation competition pool page — Pool Relay embed preview

An unofficial replica of the George Mason University **Mason Recreation** competition pool
page with a live [Pool Relay](https://www.poolrelay.com) lane calendar in place of the
schedule PDF.

**This is not a George Mason University website.** The official site is
<https://recreation.gmu.edu>. This is a working preview of one proposed change to it, and
the page says so in a ribbon across the top.

## What it replaces

The schedule is currently a PDF, and its filename tells the story:

```
Comp-Pool-No-Trinity_Master-26-27-3.pdf
```

Revision three of a master document for the year — re-exported and re-uploaded every time
a practice moves. A PDF cannot say "today": a swimmer has to download it, find the right
day, and hope the copy on the site is the current one.

## Why this pool makes the point

The competition pool is a 50 m tank with two bulkheads: **20 lanes short course** or
**8 long course**. On a given morning Varsity has lanes 1–14 while diving has 17–20 and
open swim has 15–16. That lane split is the whole point of the document, and it survives
here rather than being flattened to "pool busy".

```html
<iframe src="https://www.poolrelay.com/embed/CodrdkVH4MK9fdDixW2rSA"
        width="100%" height="780" style="border:0"
        title="Mason Aquatic and Fitness Center competition pool schedule"></iframe>
```

## Notes

- The calendar breaks **out of the text column** into a full-width band: twenty lane
  columns will not fit a 600px measure.
- The tab is saved as a **Day** view with `fit: width`, so every lane fits the frame.
- The Mason logo is a CSS placeholder rather than the university's mark.
- Navigation links point at the live site. `noindex` is set.

## Local preview

```
python3 -m http.server 8806
```
