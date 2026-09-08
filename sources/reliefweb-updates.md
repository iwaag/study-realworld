# ReliefWeb — Updates Feed

## What it is

ReliefWeb (reliefweb.int) is the humanitarian information service run by the
UN Office for the Coordination of Humanitarian Affairs (OCHA). Since 1996 it
has aggregated situation reports, press releases, assessments, appeals and
infographics from UN agencies, NGOs, governments and other humanitarian
actors worldwide, each item tagged with source organization, country and
publication date. Because it republishes and indexes primary material from
named institutional sources (UNICEF, UNHCR, WFP, IOM, OCHA, clusters, ACLED,
etc.) rather than authoring original commentary, it is a credible aggregator
of institutional and humanitarian reporting, widely cited and used by the
humanitarian sector itself.

## Acquisition method: RSS feed (with a documented but access-gated REST API)

The primary, reliably reachable acquisition path is the public RSS feed:

```
https://reliefweb.int/updates/rss.xml
```

This returns the ~20 most recent updates across all countries/sources, each
item carrying `<title>`, `<link>` (the permanent report page), `<pubDate>`,
`<source>`/`<author>` (the publishing organization), `<category>` tags
(country/org), an `<enclosure>` when a PDF/infographic attachment exists, and
a `<description>` with country/source tags plus either a short body excerpt
or "Please refer to the attached file/Infographic" when the substance is in
an attachment. Polling this URL periodically (e.g. daily) and diffing against
previously seen `<guid>`/`<link>` values is sufficient to pick up new items
over time; the feed is sorted newest-first and updates continuously.

ReliefWeb also documents a structured REST API at
`https://api.reliefweb.int/v2/reports` (apidoc.reliefweb.int) supporting
filtered/paginated queries. It requires a pre-approved `appname` parameter —
an unregistered or ad hoc `appname` value is rejected with HTTP 403
("You are not using an approved appname"), and the legacy `v1` path returns
HTTP 410 (decommissioned). The RSS feed requires no registration and needs
no query parameters, so it is the practical default acquisition method; the
API is a documented fallback once an approved `appname` is obtained.

## Worked example recipe (repeatable)

1. Fetched `https://reliefweb.int/updates/rss.xml` (a normal browser-like
   User-Agent header avoids a bare-request block some fetchers hit; a plain
   `curl` with a UA string succeeded). This returned a well-formed RSS 2.0
   document with 20 `<item>` entries.
2. Parsed the XML and scanned the `<description>` of each item, skipping the
   several that are attachment-only ("Please refer to the attached
   Infographic/file"), to find one with a substantive text body suitable for
   a report.
3. Selected item 17 of 20: a UNICEF press release, link
   `https://reliefweb.int/report/venezuela-bolivarian-republic/unicef-and-venezuelan-authorities-begin-rehabilitation-water-systems-la-guaira-earthquake-recovery-enters-new-phase`,
   published 2026-09-08. Extracted title, source organization (UN Children's
   Fund / UNICEF), country tag (Venezuela), publication date, and the full
   multi-paragraph description body (funding figures, named spokesperson
   quote, beneficiary counts).
4. Wrote a short original-language summary report from that extracted
   material (see
   `../reports/reliefweb-updates/2026-09-09-001/report.md`).

This recipe generalizes: fetch the RSS URL, parse `<item>` entries, prefer
ones with a real `<description>` body over attachment-only stubs, and
summarize in original wording (do not reproduce ReliefWeb/source-org text
verbatim beyond short quoted phrases).

## Status: VERIFIED

Retrieval succeeded on 2026-09-09: `https://reliefweb.int/updates/rss.xml`
was reachable and returned current, well-formed items, and one item's real
content (the UNICEF Venezuela water-rehabilitation release above) was
extracted and used. The `api.reliefweb.int/v2/reports` endpoint was also
reached but rejected the request with HTTP 403 pending an approved `appname`
— noted here as a limitation of the API path, not of the source overall,
since the RSS feed already provides working acquisition.
