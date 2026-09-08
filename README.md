# study-realworld

A collection of reusable, citable sources of public institutional
information — government and local-authority minutes, official documents
and statements, think-tank and research-institute reports, humanitarian and
foundation studies, university and research-institute publications, and
large-company press releases — together with short investigation reports
that summarize specific documents found through those sources.

The aim is twofold: to record how to reliably get at a given kind of source
again (which official pages to check, what URL pattern its documents follow,
how to tell a new item from an old one), and to record what was actually
found when someone did that.

## Layout

```
sources/
  INDEX.md          one row per source: id, publisher, topic/geography,
                     status, last verified
  <source-id>.md     one source: what it is, its publisher, its official
                      entry points (index/calendar/feed pages), how to find
                      new items, a worked example of retrieving one, and
                      the date the recipe was last confirmed to work

reports/
  <source-id>/
    INDEX.md          one row per investigation: date, scope, result, link
    YYYY-MM-DD-NNN/
      report.md        the investigation: what document(s) it covers, the
                        findings in original wording, and citation details
                        for each document used
```

## What a source is

A source file describes one *acquisition unit* — a specific institution's
minutes collection, a report series, an update feed — rather than a whole
institution. It has a stable identifier and explains, in enough detail to
repeat, how to find the official page or feed for that source, how to
recognize a new item, and how to fetch a document once you've found one. A
source is marked `VERIFIED` once its retrieval recipe has actually been
carried out successfully at least once, and `candidate` before that.

## What an investigation report is

A report is a short, self-contained write-up of one or more specific
documents found via a source: what the document is, what it says, and
where it came from. Reports cite their sources precisely — for each
document used: its title, publisher, publication date, the period it
covers, its version if it has one, when it was retrieved, and which pages
or sections were used. Findings are written in the report author's own
words; anything genuinely quoted from the original document is marked as a
quotation and kept short. Where a report distinguishes what the publishing
organization itself claims from the report author's own interpretation of
that material, that distinction is kept clear in the text.

## Using this repository

Start from `sources/INDEX.md` to see which sources are available and their
current status, then open a specific `sources/<source-id>.md` file for how
to retrieve documents from it yourself. To see what has already been
investigated for a given source, check `reports/<source-id>/INDEX.md`, then
open the linked `report.md` for the write-up and its citations.
