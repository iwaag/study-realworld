# Pew Research Center — Report Series

## What it is

Pew Research Center (pewresearch.org) is a nonpartisan, nonadvocacy American
think tank based in Washington, D.C. It publishes public-opinion polling and
data-driven social science research on U.S. and global topics — politics,
religion, technology, race and ethnicity, immigration, media, and social
trends. Reports are grounded in named, dated surveys (e.g., the American
Trends Panel) with disclosed methodology (sample size, field dates, weighting),
which makes it a credible, citable institutional research source. It does not
take policy positions; it describes what its surveys and analyses find.

## Acquisition method: report-page / PDF fetching

Each Pew report is published at a stable, dated URL of the form:

```
https://www.pewresearch.org/<topic-section>/<YYYY>/<MM>/<DD>/<report-slug>/
```

New reports can be discovered over time via:

- The publications listing/index page: `https://www.pewresearch.org/publications/`
- Topic section pages (e.g., `https://www.pewresearch.org/race-and-ethnicity/`,
  `.../politics/`, `.../religion/`, `.../internet-technology/`), which list
  reports newest-first.
- Site search or general web search restricted to `pewresearch.org`, e.g.
  `site:pewresearch.org <topic> <year>`.
- Pew's own newsletters/weekly roundups (also on-site, e.g.
  `https://www.pewresearch.org/newsletter/weekly-roundup/...`), which round up
  the week's new reports.

Once a report URL is found, the report page itself is fetched directly
(HTML body of the article); many reports also link a downloadable PDF version
and/or a separate "topline"/methodology PDF, which can be fetched the same
way when more survey detail is needed.

## Worked example recipe (repeatable)

1. Searched the web restricted to `pewresearch.org` for recent report pages
   (query: "pewresearch.org report September 2026"). This surfaced several
   dated report URLs, including
   `https://www.pewresearch.org/race-and-ethnicity/2026/09/01/latinos-are-split-on-whether-the-american-dream-is-achievable/`.
2. Fetched that report page directly and extracted: the underlying survey
   (Pew's National Survey of Latinos, fielded Oct 6–16, 2025, ~8,046 U.S.
   adults including 4,923 Hispanic respondents, drawn from the American
   Trends Panel and SSRS Opinion Panel, bilingual, weighted to the U.S. adult
   population), and the key statistics on Latinos' views of the American
   dream's achievability and intergenerational economic progress.
3. Wrote a short original-language summary report from that extracted
   material (see `../reports/pew-research-reports/2026-09-09-001/report.md`).

This recipe generalizes to any Pew report: find a dated report URL via the
publications/topic index or a site-restricted search, fetch the page body,
extract methodology + key findings, and summarize in original wording (Pew
text itself is copyrighted, so do not reproduce it verbatim).

## Status: VERIFIED

Retrieval succeeded on 2026-09-09: pewresearch.org was reachable, a current
report was located via web search, and its page body was fetched and yielded
substantive, extractable content (methodology and findings) as shown above.
