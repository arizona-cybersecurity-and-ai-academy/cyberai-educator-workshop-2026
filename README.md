# CyberAI Educator Workshop 2026

Participant site for the CyberAI Educator Workshop, CORE Center at the University of
Arkansas at Little Rock, July 29-30, 2026.

## What this is

A single-page portal built with [Quarto](https://quarto.org): schedule for both days,
presenters, and practical information, with per-session pages behind the schedule where a
presenter has supplied materials. Sessions with nothing posted yet show a "to come" marker
rather than a dead link.

## Build

```bash
quarto render     # outputs to docs/
quarto preview    # local preview with live reload
```

Output goes to `docs/` and is committed, so the site can be served from GitHub Pages when
the organizers are ready to publish it. Pages is not enabled yet.

`site-url` in `_quarto.yml` is set to the default Pages URL for this repo. It makes
link-preview cards resolve correctly. Change it if the site is published on another host.

## Layout

```
index.qmd                    the portal: schedule, presenters, practical info
sessions/                    per-session pages
  _template.qmd              copy this to start a new one
resources/ai-disclosure.qmd  take-away disclosure statements for participants
ua-style.scss                University of Arizona styling
assets/                      favicon and link-preview card
docs/                        rendered output, committed
```

## Adding a session page

1. Copy `sessions/_template.qmd` to `sessions/dayN-sN-slug.qmd`. The leading underscore on
   the template keeps it out of the render.
2. Fill it in.
3. In `index.qmd`, replace that session's `<span class="pill pill-pending">to come</span>`
   with a link to the new page.

Send materials to Ryan Straight (<ryanstraight@arizona.edu>) if you'd rather not edit the
site directly.

## Before publishing

The site currently carries editorial notes in `.draft-note` blocks and `tktk` markers where
information is still missing. Both come out before it is circulated to participants. Search
for `tktk` to find them.

## AI contribution

This site was drafted with AI assistance (Claude). I set the structure, supplied the source
agenda, directed the writing, and reviewed and edited everything here. I'm responsible for
its accuracy. Commits carry a `Co-Authored-By` trailer where AI did substantial drafting.

AI was not used to make any decision about a participant, and it isn't used anywhere in the
workshop's research component. The same statement appears on the site itself, in the
colophon and on the [disclosure page](resources/ai-disclosure.qmd).
