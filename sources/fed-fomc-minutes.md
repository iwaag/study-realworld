# Federal Reserve — FOMC Meeting Minutes

## What it is

The Federal Open Market Committee (FOMC) is the monetary-policy-setting body
of the U.S. Federal Reserve System. The Federal Reserve Board publishes,
on federalreserve.gov, the official minutes of every regularly scheduled
FOMC meeting — a detailed record of the Desk's market operations review, the
staff's economic and financial assessment, participants' policy discussion,
and the Committee's formal vote on the federal funds rate target range
(including the exact roll-call of members voting for and against). This is
a primary government document, not commentary about the Fed: it is the
Committee's own account of its deliberations, released on a fixed schedule
(minutes are published three weeks after each policy decision), which makes
it a highly authoritative, citable institutional source for monetary policy.

## Acquisition method: page / PDF scraping

Minutes documents are published at a stable, dated URL pattern:

```
https://www.federalreserve.gov/monetarypolicy/fomcminutesYYYYMMDD.htm   (HTML)
https://www.federalreserve.gov/monetarypolicy/files/fomcminutesYYYYMMDD.pdf  (PDF)
```

where `YYYYMMDD` is the *second* day of the (usually two-day) meeting. New
minutes can be discovered over time via the calendar/index page:

```
https://www.federalreserve.gov/monetarypolicy/fomccalendars.htm
```

This page lists all scheduled meetings for the current and next year and
links directly to the Statement, Minutes (HTML/PDF), and (for
projection-meetings) Summary of Economic Projections for each meeting once
released. Meetings without minutes yet simply show no minutes link.

## Worked example recipe (repeatable)

1. Fetched `https://www.federalreserve.gov/monetarypolicy/fomccalendars.htm`
   and asked for every 2026 meeting date together with any adjacent minutes
   link. This returned the meeting schedule (Jan 27–28, Mar 17–18, Apr 28–29,
   Jun 16–17, Jul 28–29, Sep 15–16, Oct 27–28, Dec 8–9) and identified
   July 28–29, 2026 as the most recent meeting with a minutes link, giving
   the URL `https://www.federalreserve.gov/monetarypolicy/files/fomcminutes20260729.pdf`.
2. Fetched that PDF directly. The Fed's own PDF was retrieved as a genuine
   ~424 KB binary document (not an error/404 page) and read in full: a
   15-page official minutes document headed "Minutes of the Federal Open
   Market Committee, July 28–29, 2026," complete with the market-operations
   review, staff economic/financial review, participants' discussion,
   the formal policy-action vote and roll call, and the attendance list
   signed by the Committee Secretary.
3. Extracted the policy decision, vote tally, and key discussion points and
   wrote an original-wording summary report (see
   `../reports/fed-fomc-minutes/2026-09-09-001/report.md`).

This recipe generalizes to any future meeting: check the calendar page for
the newest date with a minutes link, then fetch
`.../files/fomcminutesYYYYMMDD.pdf` (or the `.htm` equivalent) directly.

## Status: VERIFIED

Retrieval succeeded on 2026-09-09: the calendar page was reachable and
correctly enumerated 2026 meetings with minutes links, and the July 28–29,
2026 minutes PDF was fetched as an authentic, full-length Federal Reserve
document and read directly (not merely summarized secondhand), yielding
substantive, extractable content as described above.
