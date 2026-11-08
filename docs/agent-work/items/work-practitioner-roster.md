---
kind: work
status: open
priority: 2
owner: Ada
area: people
evidence: "08.11.: 8 seed entries, affiliation on 20 draft entries, 9 Gmail drafts in benedikt@hackersandwizards.dev, none sent. Names live in os (docs/agent-work/2026-11-08-practitioner-roster.md and Ada's run report), since this repo is public."
assumption: "affiliation comes only from `work.company` or `facets.trainer.supply_partner` on the Company OS record (the company record's `name`), `freelance` only where the record says freelance, `hackers&wizards` for staff with an employment record; Slack channels were not read"
order: 180
---

# Every person who delivers for h&w has an entry, with affiliation

Done on 08.11.: `affiliation` in the schema, shown as "Works for" on each page; the overview
groups people into hackers&wizards, At a company (sorted by company), Freelance and Not stated
yet. Seeds without a portrait show initials and list "Portrait" as missing.

## What remains

- **The drafts** "Dein Profil bei hackers&wizards" / "Your profile at
  hackers&wizards" (7 German, 2 English on 08.11.), scheduled for Monday 09.11. 08:00, go to the new entries with a working address and
  the two entries the Monday round leaves out. One new entry was removed on 08.11. by Benedikt's
  ruling: its draft, if one exists, is deleted, not sent. Each asks for bio, portrait, the profile for matching,
  and confirms or asks the affiliation.
- **Follow-up for the other 49** (the Monday round asks for bio and links, not for the profile or
  affiliation): draft only after each person has answered their first mail, so nobody gets two
  asks at once.
- **One new entry has no draft**: the only address on record bounces since 19.10.
- **One new entry lacks LinkedIn**: none on record; the mail asks for it.
- **Three affiliations stay empty**: the company names are on os's confidential list, so each
  waits until the person states it and the name gets an allow entry with their yes.
- **Six `active` entries carry no affiliation yet** although Company OS records one: an approved
  entry changes only with the person's yes, so the follow-up asks them.

## Blind review of the overview, 08.11.

Medium: two personas (h&w colleague staffing a client project, trainer checking their own entry),
Claude twice and Codex once each, three variants under shuffled neutral labels at 1440 and 375 px.
Criteria: telling apart who works where, finding a group, breathing room, visual calm.

| Variant                   | staffing (C/C/Codex) | trainer (C/C/Codex) | Mean |
| ------------------------- | -------------------- | ------------------- | ---- |
| Sections by affiliation   | 7/7/7.5              | 7/7/8               | 7.25 |
| Filter row by affiliation | 6/6/6.5              | 6/6/7               | 6.25 |
| Affiliation line on card  | 4/4/5.5              | 3/4/6.5             | 4.5  |

Noise between the two Claude runs: 0 to 1. Fixed after the round, from the reviewers' reasons:
companies sorted inside their section, and the card repeats no affiliation its heading names.
