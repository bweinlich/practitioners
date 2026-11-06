---
kind: decision
status: assumed
priority: 2
owner: Benedikt
area: people
evidence: "Blind review 06.11., 2 personas, Claude twice and Codex once each; screenshots at 375 and 1440 px against hackersandwizards.dev/team/benedikt-stemmildt/ and /stefan-munz/"
assumption: "A build that could go public carries only entries with status active; drafts and seeds render in the dev server alone (src/lib/entry.ts, shown). Every page carries noindex."
recommended: status-first
options:
  - key: status-first
    label: Status box under the hero, English and German side by side
    detail: "Night hero with name and portrait as on the website, then a box saying what the entry still lacks and how to send it, then both bios in two columns from 1024 px, then the links. Approved entries show no box."
    score: 7.0
    noise: 0.5
  - key: website-order
    label: Website order, status as the closing band
    detail: "Hero, English bio, links, German bio, then the entry's state in a night band where the website has its call to talk."
    score: 6.33
    noise: 0.5
  - key: card
    label: Today's overview card, no page of its own
    detail: "Portrait, name, both bios and link chips in one card on the overview."
    score: 1.17
    noise: 0
---

# Each practitioner's page, and which pages a public build carries

Each entry now has a page at `/<slug>/`, linked from the overview, built from brand's tokens,
fonts, header and elements to look like the person's page on hackersandwizards.dev. Nothing here
is hosted today: the repo is public, the site runs only in `bun run dev`.

## Publication rule (assumed)

A public build shows an entry only when it is `active`, which the person's own change or yes sets.
`bun run build` produced the overview and the 16 `active` pages on 06.11. Five of them were
committed by Stefan or Claude Code, never by the person: Björn Rochel, Christian Tietze, Johann
Laur, Nils Eckelt, Tobias Schlitt. No public host before each of them is confirmed by the person's
own change or their yes to the text (`profile-mail-round`), or returns to `draft`.
The gate also builds a preview of
every page into `.preview/` (gitignored), so a broken page fails it.

Gap before any public host: the public build still copies every portrait into `dist/_astro/`
(54 files measured 06.11.), since the schema's `image()` processes each entry's photo whether its
page renders or not. Nothing links to those files and the repo serves them anyway, but a host
would publish them; until fixed, deploy no `dist/`.

## Blind review

Medium review: a trainer checking their own entry after the mail, a client's engineering lead
vetting a trainer. Each saw the website page as reference and three candidates under shuffled
neutral labels, Benedikt and Stefan at 375 and 1440 px. Criteria fixed before scoring: C1 match
to the reference, C2 reading one's own entry, C3 vetting, C4 calm. Noise is the gap between the two
Claude runs of one persona.

| Option        | trainer (C/C/Codex) | lead (C/C/Codex) | Mean | C1   | C2   | C3   | C4   |
| ------------- | ------------------- | ---------------- | ---- | ---- | ---- | ---- | ---- |
| status-first  | 6/7/8               | 7/7/7            | 7.0  | 7.5  | 6.83 | 6.33 | 8.17 |
| website-order | 5/6/7               | 6/6/8            | 6.33 | 7.67 | 5.83 | 6.33 | 7.83 |
| card          | 1/1/2               | 1/1/1            | 1.17 | 2.0  | 1.5  | 1.83 | 3.33 |

The lead of 0.67 stands just outside the noise of 0.5. Claude prefers status-first for both
personas, Codex for the trainer only. On match alone the two tie (7.5 and 7.67); status-first wins
on reading one's own entry. The card's screenshots of Stefan came out blank and
Benedikt's phone card was cut off, so its score understates it; it ranks last on match either way.

Fixed after the round: all six reviewers saw "Approved entry" on Stefan's page above a missing
field. The hero no longer carries a status, and the box shows on every draft and whenever anything
mandatory is missing. Left as it is: the role line and topics the website shows under the name.
Both are the website's own data, and this repo holds no role.
