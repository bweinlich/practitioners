---
kind: decision
status: open
priority: 1
order: 40
area: people
owner: Benedikt
evidence: "Blind review 06.11. (3 personas, Claude twice and Codex once each); practitioner-bio skill, route By mail"
recommended: mail
options:
  - key: mail
    label: Each trainer confirms or corrects their own entry by replying to a mail
    detail: "The mail shows only their entry (the text the website publishes, portrait, links, what is missing) and one consent statement. Reply: it fits, corrections or a new photo, or take me off. An agent applies it; only corrections get a second mail. The repo goes private and trainers lose write access. Built here: skill route, consent field. Trainer 2 to 10 minutes, no tools; h&w about 15 minutes of agent work plus a founder's check and send per trainer."
    score: 8.67
    noise: 0.25
  - key: link
    label: A personal expiring link to a web page showing only their entry
    detail: "Form or guided AI interview, consent tick box, approval becomes a change h&w merges. Trainer 5 to 15 minutes in a browser; h&w builds and hosts an app, about 4 to 6 days plus data-processing agreements and upkeep."
    score: 7.44
    noise: 0.25
  - key: folder
    label: Private repo with GitHub access per trainer and a per-folder owner rule
    detail: "Interview in Claude Code on the trainer's machine, pull request a founder merges. Trainers still read every other entry. Trainer 30 to 60 minutes the first time with git, Bun and Claude Code."
    score: 4.22
    noise: 0.25
  - key: current
    label: Keep today's flow
    detail: "Public repo, every trainer can write every entry, no consent recorded, git, Bun and Claude Code needed."
    score: 1.33
    noise: 0.25
---

# How does a trainer complete their profile: by mail reply, a personal link, or their own folder?

You asked (06.11.) how completing a profile works, whether trainers may commit, and for a concept
where each trainer sees only their own entry when the mail arrives. Recommendation: **by mail**. It
works whichever store the open Company OS decision `practitioners-repo` picks, and it removes the
reason trainers needed access to any repo.

## How it works today

Measured 06.11.: the repo is public with 40 collaborators who can write every entry, `main` has no
branch protection and two public forks exist. 16 of 54 entries are `active`, 38 are seed drafts h&w
wrote. 11 trainers committed their own bio, each once, the last on 05.10. The path needs a GitHub
account, git, Bun and Claude Code. Four surfaces describe it differently: trainer-hub's onboarding
says "start Claude in this repository" (trainer-hub), Seymour says clone practitioners, the seed
text says "tell Seymour", the README says to ask for write access. Nothing records consent or photo
rights. The link `hackersandwizards.dev/practitioners/` now redirects to `/team/`.

## Research (fetched 06.11.)

- Sessionize: an organizer adds a speaker, the speaker accepts an emailed invitation and then edits
  only their own details ([Sessionize](https://sessionize.com/playbook/adding-sessions-and-speakers)).
- talque: speakers get an email, click Edit and see their own forms; the flow "doesn't require
  contributors to register" ([talque](https://web.talque.com/en/editing-your-speaker-profile)).
- GitLab: each employee edits their own YAML file by merge request; the onboarding contact and the
  manager approve and merge ([GitLab Handbook](https://handbook.gitlab.com/handbook/about/editing-handbook/edit-team-page/)).
  Employees inside their employer's repo, with review.
- Decap CMS Open Authoring takes outside edits as pull requests, but needs the GitHub backend and,
  for a private repo, read access for the contributor ([Decap](https://decapcms.org/docs/open-authoring/)).

Networks of outside contributors ask by invitation and show one profile; the repo-per-team model
fits employees.

## Blind review

Medium review. Personas: a freelance trainer who is not a developer, a trainer who is, the h&w
person who runs the network. Text memo on a laptop, four options under shuffled neutral labels,
criteria fixed before scoring. Claude opus twice per persona, Codex once. Noise is the gap between
Claude's two runs. Mail leads link by 1.23, both models agree.

| Option  | non-dev (C/C/Codex) | developer | network lead | Mean | C1 own only | C2 trainer effort | C3 consent | C4 h&w effort | C5 stays current |
| ------- | ------------------- | --------- | ------------ | ---- | ----------- | ----------------- | ---------- | ------------- | ---------------- |
| mail    | 9/9/9               | 8/8/9     | 9/8/9        | 8.67 | 9.22        | 9.33              | 8.67       | 6.56          | 7.33             |
| link    | 8/7/8               | 7/7/8     | 7/7/8        | 7.44 | 9.33        | 8.56              | 9.33       | 3.44          | 6.89             |
| folder  | 3/3/2               | 6/7/6     | 4/4/3        | 4.22 | 4.00        | 4.11              | 7.00       | 6.44          | 4.89             |
| current | 1/1/1               | 2/2/2     | 1/1/1        | 1.33 | 1.11        | 2.89              | 1.11       | 7.56          | 2.67             |

Folded in from the reviewers: no confirmation mail when the reply is "it fits" (two mails per
trainer were the network lead's main cost); the do-it-yourself interview stays for people with
write access only, so it exposes no drafts. Left as it is: consent by reply rather than a tick box.
A reply is a dated, written record.

Effort, my judgement: the trainer's time from the step count of each option. h&w per trainer is
about 15 minutes of agent work plus a founder's minute to check and send, about two working days
for 50 trainers. Cross-check: the current flow, which needs no h&w time, reached 11 trainers in two
months.

## What you release (nothing has been sent or changed outside this repo)

1. **The repo goes private, and trainers lose write access** (40 collaborators today; you and
   Stefan keep admin). Either here or in trainer-hub, per `practitioners-repo`.
2. **The mail round.** The 21 Gmail drafts „Deine Profilseite auf unserer Website“ are adapted to
   the skill's route `By mail` (own entry inline, what is missing, the consent statement, the three
   replies) and sent by you or Stefan. Then the 18 seed drafts without a website page (Reachy and
   Thomas Kern among them, who need none) and the 16 `active` entries, which record no consent
   either.
3. **The consent statement** (in the skill, under Mandatory) checked by Dana or the lawyer before
   the first mail.
4. **Your own entry is the first case:** it now carries the bio and portrait the website publishes,
   as `draft`. Reply „passt“ here or in a session, and it turns `active` with the date of your yes.
   Stefan Munz's entry still has the old portrait (the website shows the 28.10. shoot) and names the
   old training names (Agentic Product Engineering, Agentic Factory Engineering); his mail shows
   both, and his reply decides.

## What each mail asks for (measured 06.11., `src/content/practitioners/`)

Each entry's page at `/<slug>/` in `bun run dev` lists what it lacks; the mail links the person to
their page on `hackersandwizards.dev/team/<slug>/`, never to this repo.

- 16 `active` entries lack only consent.
- Benedikt's entry lacks only consent. It now carries the links his own site publishes (X, GitLab,
  Xing, Speaker Deck, Wikidata), added on his message of 06.11. that many of his profile links were
  missing. Company OS lists more that he publishes nowhere (Bluesky, Sessionize, Hugging Face,
  Stack Overflow, Luma, Meetup, the Amazon author page, haw.dev/call as booking link): his reply
  decides which go in.
- 35 seed drafts lack the English and German bio and consent; Dana Buß and Reachy lack LinkedIn too.
- Links proposed in the mail, already published but not in the entry: Stefan Munz
  `x.com/stefanmunz` (stefanmunz.com). From the website's own profiles: Felix Duus productful.io,
  Hendrik Hemken beyond7.ai, Jannik Streek b310.de and github.com/JannikStreek, Julia Bastian
  juliabastian.medium.com, Kai Wendlandt github.com/kaiwend, Kamil Kubica kamilkubica.com, Martin
  Westphal martin.westphal.pw, westphal.ai and sessionize.com/adeanima, Matthias Lau
  heureka-labs.de and github.com/matthiaslau, Oliver Tischlinger github.com/Metabor, Zamina Ahmad
  zamina.de.
- The website has profiles with no entry here: Andreas Stephan, Markus Andrezak, Sebastian
  Jespersen.

After the round, `consent` becomes required for `active` in `src/lib/schema.ts`.
