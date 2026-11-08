---
kind: work
status: open
priority: 2
owner: Ada
evidence: "Measured 08.11.2026: every portrait's rendered width on all 580 pages of the live sitemap at windows of 1440, 1023 and 639 px, and on the four team pages at 18 widths from 360 to 1920 px. `src/lib/photo-size.test.ts` holds the minimum and the count."
---

# 51 portraits are below the 918 px minimum

The minimum follows the first team group's slot, 459 CSS px at a 767 px window, which needs 918 px on a 2x screen. `stefan-munz` (486 CSS px) and `benedikt-stemmildt` (866 CSS px) have larger slots. Sharpening does not close that gap, so a larger original is the only fix. Larger originals were looked for in this repository's and trainer-hub's history, pull requests, Company OS, the mailbox, the talks repository and the websites and GitHub profiles named in the entries.

## What remains

1. **The photo ask in the profile follow-up mail**, softest first, for at least 918 px wide and roughly square: the rows of the ranking below with a file under 918 px, except `stefan-munz` (point 2) and `reachy`, which is not on the website: 33 people. A further 16 folders hold protected names, which may stand only in the person's own folder: `sips -g pixelWidth src/content/practitioners/*/photo.webp` lists every portrait with its width. Lower the count in `src/lib/photo-size.test.ts` as originals arrive.
2. **`stefan-munz`:** this repository keeps his own 480 px photo, the website shows the press portrait at 1024 px. He has not said yes to the press portrait for this entry; his yes moves it here.
3. **Larger photos of the person that are other pictures**, for their own yes, as their entries are active: `ralf-hueller` (1024 x 1078 on their website, same pose, another background), `christian-tietze` (1000 px on their website).
4. **`verena-traub`** holds the website's file, cropped to 450 px from a 1000 px source that is in no repository. That source gives at most 450 px at this crop; only the photographer's file would reach the minimum.
5. **The website** still copies by hand. Its copy from the package is a brief for a session there. `benedikt-stemmildt`'s largest slot (866 CSS px) needs 1732 px; the brand press photo holds 2010 px, so that master is the website's to raise.

## Ranking at the largest slot

Score is my own composite, lower is softer: the file's width against twice the slot, capped at 1, times the share of face detail that survives halving the image to 240 px. A portrait not on the website counts as covering its slot. The protected folders are left out of this table.

| Rank | Folder                              | File px | Largest slot, CSS px | Detail lost at 240 px | Score |
| ---: | ----------------------------------- | ------: | -------------------: | --------------------: | ----: |
|    1 | `bastian-weinlich`                  |     480 |                  459 |                  0.46 |  0.28 |
|    2 | `steffen-clemens`                   |     480 |                  459 |                  0.26 |  0.39 |
|    3 | `stefan-munz`                       |     480 |                  486 |                  0.15 |  0.42 |
|    4 | `verena-traub`                      |     480 |                  459 |                  0.15 |  0.44 |
|    5 | `johann-laur`                       |     480 |                  459 |                  0.14 |  0.45 |
|    6 | `dana-buss`                         |     480 |                  459 |                  0.11 |  0.47 |
|    7 | `hendrik-hemken`                    |     480 |                  311 |                  0.39 |  0.47 |
|    8 | `benedikt-stemmildt`                |    1024 |                  866 |                  0.11 |  0.53 |
|    9 | `markus-rother`                     |     480 |                  311 |                  0.30 |  0.54 |
|   10 | `markus-andrezak`                   |     400 |                  240 |                  0.32 |  0.57 |
|   11 | `tereza-iofciu`                     |     480 |                  311 |                  0.26 |  0.57 |
|   12 | `jan-milz`                          |     480 |                  311 |                  0.22 |  0.60 |
|   14 | `kamil-kubica`                      |     480 |                  311 |                  0.18 |  0.63 |
|   15 | `alexander-greim`                   |     480 |                  311 |                  0.15 |  0.66 |
|   16 | `bjorn-rochel`                      |     480 |                  311 |                  0.15 |  0.66 |
|   18 | `viktor-shcherban`                  |     480 |                  240 |                  0.31 |  0.69 |
|   20 | `jannik-streek`                     |     480 |                  311 |                  0.08 |  0.71 |
|   21 | `matthias-lau`                      |     960 |                  240 |                  0.28 |  0.72 |
|   24 | `ralf-hueller`                      |     480 |                  240 |                  0.23 |  0.77 |
|   26 | `julia-bastian`                     |     480 |                  240 |                  0.22 |  0.78 |
|   27 | `christian-tietze`                  |     480 |                  240 |                  0.21 |  0.79 |
|   29 | `kai-wendlandt`                     |     480 |                  240 |                  0.21 |  0.79 |
|   30 | `malte-burkert`                     |     480 |                  240 |                  0.21 |  0.79 |
|   32 | `stefan-grothkopp`                  |     480 |                  240 |                  0.21 |  0.79 |
|   36 | `luis-fernando-de-la-torre-delgado` |     800 |                  240 |                  0.18 |  0.82 |
|   40 | `semjon-mossinger`                  |     480 |                  240 |                  0.17 |  0.83 |
|   41 | `tobias-schlitt`                    |     480 |                  240 |                  0.17 |  0.83 |
|   43 | `martin-westphal`                   |     480 |                  240 |                  0.16 |  0.84 |
|   44 | `reachy`                            |     480 |      not on the site |                  0.16 |  0.84 |
|   45 | `nermin-caluk`                      |     480 |                  240 |                  0.15 |  0.85 |
|   46 | `andreas-stephan`                   |    1024 |                  311 |                  0.14 |  0.86 |
|   47 | `ingo-eichhorst`                    |     480 |                  240 |                  0.14 |  0.86 |
|   48 | `felix-duus`                        |     480 |                  240 |                  0.13 |  0.87 |
|   49 | `jost-kuenzel`                      |     900 |                  240 |                  0.13 |  0.87 |
|   50 | `oliver-tischlinger`                |     480 |                  240 |                  0.13 |  0.87 |
|   52 | `aaron-spring`                      |     480 |                  240 |                  0.12 |  0.88 |
|   53 | `johannes-schmidt`                  |     800 |                  311 |                  0.12 |  0.88 |
|   54 | `nils-eckelt`                       |    1024 |                  311 |                  0.09 |  0.91 |
|   55 | `sebastian-jespersen`               |     480 |                  240 |                  0.09 |  0.91 |
|   56 | `zamina-ahmad`                      |     960 |                  311 |                  0.09 |  0.91 |
