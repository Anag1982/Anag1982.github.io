# Editing the site content

`index.html` never needs to change to add content. Everything on the page is
loaded at runtime from the JSON files in this folder. Edit the JSON, commit,
push — GitHub Pages redeploys and the change is live.

---

## `news.json` — News & Updates

An array, newest first. `text` may contain HTML (e.g. `<em>`).

```json
[
  { "date": "July 2026", "title": "Three new books published", "text": "…" }
]
```

---

## `publications.json` — Publications

An array. The page groups these by `year` automatically and renders the two
most recent years expanded, the rest collapsed. Sort order within a year is
whatever order the file is in, so keep journals before conferences.

```json
{
  "title":   "Grover's Search-Inspired Quantum Reinforcement Learning …",
  "authors": "R. Fan, X. Huang, M. Chakraborty, A. Nag, A. Mukherjee",
  "venue":   "IEEE Wireless Communications and Networking Conference (WCNC)",
  "details": "pp. 1–5, 2026",
  "year":    2026,
  "type":    "conference",
  "doi":     "10.1109/wcnc65185.2026.11555408"
}
```

`type` is one of `journal`, `conference`, `book`, `book-chapter`, `preprint`,
`report` — it drives the small grey badge. `doi` is optional; omit it and the
DOI link is left out.

---

## `books.json` — Authored Books

An array. `category` is `authored` or `edited`; the page renders those as two
labelled groups, each sorted newest first.

```json
{
  "title":     "Maths for AI",
  "subtitle":  "Linear Algebra, Calculus, Probability and Optimization …",
  "role":      "Author",
  "series":    "Mathematics for Everything, Book 2",
  "publisher": "Independently published",
  "year":      2026,
  "date":      "July 2026",
  "format":    "Kindle Edition · 119 pages",
  "cover":     "books/maths-for-ai.jpg",
  "link":      "https://www.amazon.co.uk/dp/B0H7QM2BB6",
  "doi":       "optional",
  "editors":   "optional — shown only for edited volumes",
  "blurb":     "One paragraph.",
  "category":  "authored"
}
```

Cover images live in `/books/` at the repo root. Save them around 400 px wide —
the page displays them at 104 px, so anything larger is wasted bandwidth.

---

## `blogs.json` — Blogs and Newsletter

**The whole section is hidden while `items` is empty.** Add entries and it
appears; empty it again and it disappears. No HTML edit either way.

```json
{
  "intro": "Optional one-paragraph standfirst. May contain HTML.",
  "items": [
    {
      "date":        "2026-07-14",
      "title":       "Why deep learning has to be deep — in one figure",
      "outlet":      "Mathematics for Everything (Newsletter)",
      "link":        "https://…",
      "description": "One or two sentences."
    }
  ]
}
```

`date` accepts either an ISO date (`2026-07-14`, rendered as *14 July 2026*) or
free text (`July 2026`, rendered verbatim). Items are sorted newest first, so
prefer ISO dates — they sort correctly. `link` and `description` are optional;
without a link the title renders as plain text and the "Read" link is dropped.

---

## `students.json` — Research group

Consumed by `research-group.html`. Photos live in `/students/`.
