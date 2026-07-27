# CyberAI Educator Workshop 2026

Participant site for the CyberAI Educator Workshop, CORE Center at the University of
Arkansas at Little Rock, July 29-30, 2026.

Published at
<https://arizona-cybersecurity-and-ai-academy.github.io/cyberai-educator-workshop-2026/>.

## What this is

A single-page portal built with [Quarto](https://quarto.org): schedule for both days,
presenters, and practical information, with per-session pages behind the schedule where a
presenter has supplied materials. A session with no page yet is plain text in the schedule
rather than a link, so nothing points at a page that isn't there.

## Build

```bash
quarto render     # outputs to docs/
quarto preview    # local preview with live reload
```

**You do not need to render to publish.** Pushing to `main` triggers the workflow in
`.github/workflows/publish.yml`, which renders the site and publishes it to the `gh-pages`
branch. GitHub Pages serves from there. Editing a `.qmd` in the GitHub web interface is
enough, no local setup required.

Rendered output is not committed. `docs/` is gitignored and built in CI, so the published
site always matches the source rather than matching whoever last remembered to render.

If a local preview starts showing stale content, the `quarto preview` daemon is holding an
old snapshot and writing it into `docs/`. Stop the process, delete `.quarto/` and `docs/`,
and run `quarto render` again.

`site-url` in `_quarto.yml` sets the published address, which is what makes link-preview
cards resolve. Change it if the site moves to another host.

## Layout

```
index.qmd                    the portal: schedule, presenters, practical info
sessions/                    per-session pages
  _template.qmd              copy this to start a new one
resources/ai-disclosure.qmd  take-away disclosure statements for participants
ua-style.scss                University of Arizona styling
assets/                      favicon and link-preview card
```

## Adding a session page

1. Copy `sessions/_template.qmd` to `sessions/dayN-sN-slug.qmd`. The leading underscore on
   the template keeps it out of the render.
2. Fill it in. The template carries the house style: no em-dashes, no semicolons,
   contractions by default.
3. In `index.qmd`, wrap that session's `<h3>` title in a link to the new page, matching the
   sessions that already have one.

Send materials to Ryan Straight (<ryanstraight@arizona.edu>) if you'd rather not edit the
site directly.

## AI contribution

This site was drafted with AI assistance (Claude). I set the structure, supplied the source
agenda, directed the writing, and reviewed and edited everything here. I'm responsible for
its accuracy. Commits carry a `Co-Authored-By` trailer where AI did substantial drafting.

AI was not used to make any decision about a participant, and it isn't used anywhere in the
workshop's research component. The same statement appears on the site itself, in the
colophon and on the [disclosure page](resources/ai-disclosure.qmd).
