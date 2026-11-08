# Portraits: larger originals and the retouch, 08.11.2026

Three portraits changed, each a larger copy of the same shot: `johann-laur` (480 to 978 px),
`jannik-streek` (480 to 636 px) and `tereza-iofciu` (480 to 508 px). Each got the retouch,
without sharp-2. Every other portrait keeps its file. Across 33 people, retouch alone tied
with the current files (mean −0.02 on a 10-point scale) and retouch plus sharp-2 lost (mean −0.21).
`bun run portrait` (`scripts/retouch-portrait.ts`) holds the treatment for the next portrait.

## Scope

The 33 folders with a portrait below 960 px that hackersandwizards.dev shows. Left out: the 15
folders whose names stay off the website, which have no slot to improve and may not be named
outside their own folder, plus `reachy` and `robert-glaser`, which the site does not show either.
Measured with `sips -g pixelWidth` on all 56 portraits: 50 below 960 px.

What the live site shows (headless Chrome for Testing, 08.11.): at a 1440 px window the first
`/team/` group renders at 302 CSS px and every profile page at 240 CSS px; on a 390 px phone, 208
and 160 CSS px. At 2x a 480 px file fills a 240 px slot exactly, so a larger file mainly helps the
first group and screens wider than these two. `src/lib/photo-size.test.ts` keeps the 918 px minimum
for the 459 CSS px slot at a 767 px window.

## Sources

Searched per person: the website, GitHub and Mastodon profiles named in the entry, Sessionize and
speakerinnen.org profiles, company team pages (Tudock, WPS, WAPP, Heureka Labs, productful,
Beyond7), the Digitale Leute media library, OOP and WeAreDevelopers speaker pages, web search, and
Benedikt's Gmail (171 messages with an image attachment and a photo word, read-only). GitHub serves
avatars at 460 px at most and Sessionize at 400 px, below every current file. Gmail held no usable
portrait. A candidate counted only at an OpenCV SFace cosine of at least 0.90 against the current
portrait, measured at matched scale, and after a side-by-side check. Controls: Benedikt's portrait
against itself at 300 px 0.93, against two other people 0.14 and 0.28.

| Folder             | Source                                                                         | Size        | Face match | Outcome                                                         |
| ------------------ | ------------------------------------------------------------------------------ | ----------- | ---------- | --------------------------------------------------------------- |
| `johann-laur`      | tudock.de/wp-content/uploads/CDTDK\_\_0063_1000px.jpg                          | 1000 × 1000 | 0.955      | swapped, 978 px crop                                            |
| `jannik-streek`    | b310.de/assets/img/photos/jannik.jpg                                           | 636 × 636   | 0.962      | swapped, whole image                                            |
| `tereza-iofciu`    | terezaiofciu.com, its share image (cdn.prod.website-files.com, `meta-img.jpg`) | 1200 × 630  | 0.959      | swapped, 508 px crop                                            |
| `hendrik-hemken`   | beyond7.ai/assets/images/hendrik-portrait.jpeg                                 | 1167 × 1200 | 0.959      | tie, current kept                                               |
| `felix-duus`       | productful.io, `felix-duus_productful-co-founder.jpg`                          | 880 × 919   | 0.942      | tie, current kept                                               |
| `steffen-clemens`  | tudock.de/wp-content/uploads/2026-06-02-Mitarbeiterfoto-3.jpg                  | 1500 × 1500 | 0.982      | lost, current kept                                              |
| `ralf-hueller`     | hit-services.de/img/hueller_portrait_1024px.webp                               | 1024 × 1078 | 0.953      | rejected: the same frame with the hedge replaced by a grey wall |
| `jost-kuenzel`     | jostkuenzel.de, portrait 900 px                                                | 900 × 900   | 0.965      | same size as the current file                                   |
| `kamil-kubica`     | kamilkubica.com/kamil.png                                                      | 1200 × 1471 | 0.80       | below 0.90                                                      |
| `jan-milz`         | digitale-leute.de/wp-content/uploads/2018/09/jan_milz.jpg                      | 1024 × 1024 | 0.79       | below 0.90                                                      |
| `ingo-eichhorst`   | WeAreDevelopers speaker image                                                  | 1200 × 630  | 0.81       | below 0.90, background cut out                                  |
| `viktor-shcherban` | viktor.shcherban.de/viktor.jpg                                                 | 675 × 639   | 0.75       | below 0.90                                                      |
| `christian-tietze` | christiantietze.de/contact/profile-square.jpg                                  | 1000 × 1000 | 0.74       | below 0.90                                                      |
| `stefan-grothkopp` | grothkopp.com/profil_2.png                                                     | 1792 × 1970 | 0.66       | below 0.90                                                      |
| `bjorn-rochel`     | bjro.de/assets/images/bjro.jpg                                                 | 800 × 800   | 0.54       | below 0.90                                                      |
| `tobias-schlitt`   | schlitt.info, about page portrait                                              | 3792 × 4085 | 0.52       | below 0.90                                                      |

Tereza Iofciu's site also holds event photos up to 3333 × 5000 px; they scored 0.54 to 0.63. Below
0.90 is often the same person in another picture; the bar only lets a copy of the current shot through.
For the 24 people without a candidate, a larger original would need a signed-in LinkedIn
browser or the person: `aaron-spring`, `alexander-greim`, `bastian-weinlich`, `bjorn-rochel`,
`christian-tietze`, `dana-buss`, `ingo-eichhorst`, `jan-milz`, `julia-bastian`, `kai-wendlandt`,
`kamil-kubica`, `malte-burkert`, `markus-andrezak`, `markus-rother`, `martin-westphal`,
`matthias-lau`, `nermin-caluk`, `oliver-tischlinger`, `sebastian-jespersen`, `semjon-mossinger`,
`stefan-grothkopp`, `tobias-schlitt`, `verena-traub`, `viktor-shcherban`. Ralf Hüller's and
Christian Tietze's other photos on their own websites need their yes, as the work item says.

## Treatment

`scripts/retouch-portrait.ts`, after the recipe in Company OS (`profile-photos.md` and the event
photos report of 29.10.): square crop, white balance by channel gain (gray-world at half strength,
each gain within 5 %), a tone curve that lowers highlights above 0.75 by up to 4 grey levels and
keeps white, a Lanczos resize to the master size, and with `--sharpen` sharp-2, an unsharp mask on
luminance only at radius 1.2 px, amount 70 %, threshold 2. WebP q82, effort 6, smart subsampling,
as the website's `optimize-media.mjs`.

Three departures from the transcripts. The event-photo script's roll-off formula raised the values
just above its knee (slope 1.33) instead of lowering them, so the script uses a shoulder that only
lowers. Denoise is left out: the Immerkær estimate put 54 of 56 portraits at 1.9 to 2.9 grey levels.
The two above, Verena Traub at 4.3 (sharpened once already) and Jannik Streek's
current file at 7.8, are texture and earlier sharpening, not sensor noise. Masters stop at 1024 px, the cap in the
`practitioner-bio` skill, rather than 1760 px: the largest practitioner slot needs 972 px.

## Blind review

Medium: one persona on two devices, the CTO of a 300-person software company checking trainers
before booking, on a 14-inch 2x laptop at 1440 px and on a 390 px 3x phone. Claude Opus and Codex
(gpt-6.1-sol, high), two runs each: 72 calls, 888 scored images, none missing. Each reviewer saw
four trainers per call, each in every version, as a screenshot of the live page at device pixels
with the portrait requests answered from the version file. That is the first `/team/` group's
card for Bastian Weinlich, Dana Buß, Johann Laur, Steffen Clemens and Verena Traub, and the
profile page portrait for everyone else. Names were neutral (`t1-a.png`) and shuffled per call;
the key stayed outside the folders. The criteria were fixed before the first call.

The laptop prompt, verbatim, folder path shortened:

> You are the CTO of a 300-person software company. You are checking the trainers of a training provider's website before you book a training for your engineering teams, on a 14-inch laptop with a 2x (Retina) screen at a 1440 CSS px wide window; each image is a screenshot at device pixels, so 2 image pixels make 1 CSS pixel on that screen. The website shows trainers as portrait cards on its team page and a portrait at the top of each trainer's own page.
>
> You see screenshots of 4 trainers. For each trainer you see the same place on the page in several versions that differ only in the portrait photo. The files are in the folder …/b1-laptop-claude-r1: [file list]
>
> Read every image. Judge only the portrait photo as you would see it on that screen. Score each image from 1 to 10 on each criterion: 1. sharpness: the face looks crisp at this display size, no blur, no blockiness 2. natural: the photo looks like a real, untouched photograph, no halos, crunchy edges or plastic skin 3. trust: the person looks credible and professional as a trainer you would put in front of your engineers 4. fit: the portrait fits with the page around it 5. calm: the image reads calmly, nothing distracting
>
> Answer with only a JSON array, one object per image, nothing else

Score is the mean of the five criteria over all eight cells (two devices, two models, two runs).
Noise is the largest gap between the run-1 and run-2 means of one version of that person. Across
all images the run-to-run gap averages 0.33 for Claude and 0.21 for Codex. A version replaces the
current file only where its lead exceeds the noise with each model and in each run. `cur` is the
current file, `-r` retouched, `-rs` retouched with sharp-2, `src` the larger original.

| Folder                | cur  | cur-r | cur-rs | src-r | src-rs | Noise | Kept                     |
| --------------------- | ---- | ----- | ------ | ----- | ------ | ----- | ------------------------ |
| `aaron-spring`        | 7.95 | 8.03  | 7.9    |       |        | 0.1   | current                  |
| `alexander-greim`     | 7.98 | 7.9   | 7.5    |       |        | 0.3   | current                  |
| `bastian-weinlich`    | 7.0  | 6.95  | 6.95   |       |        | 0.1   | current                  |
| `bjorn-rochel`        | 7.05 | 7.05  | 6.97   |       |        | 0.1   | current                  |
| `christian-tietze`    | 7.92 | 7.9   | 7.7    |       |        | 0.2   | current                  |
| `dana-buss`           | 7.42 | 7.42  | 7.42   |       |        | 0.15  | current                  |
| `felix-duus`          | 8.18 | 8.2   | 7.78   | 8.07  | 7.95   | 0.35  | current                  |
| `hendrik-hemken`      | 7.65 | 7.67  | 7.47   | 8.08  | 8.08   | 0.4   | current                  |
| `ingo-eichhorst`      | 8.2  | 8.3   | 7.77   |       |        | 0.15  | current                  |
| `jan-milz`            | 7.33 | 7.53  | 7.22   |       |        | 0.15  | current                  |
| `jannik-streek`       | 7.3  | 7.2   | 7.0    | 7.9   | 7.7    | 0.3   | larger original, retouch |
| `johann-laur`         | 7.15 | 7.62  | 7.38   | 8.22  | 8.05   | 0.4   | larger original, retouch |
| `johannes-schmidt`    | 8.25 | 8.22  | 8.35   |       |        | 0.15  | current                  |
| `jost-kuenzel`        | 8.15 | 8.03  | 8.1    |       |        | 0.1   | current                  |
| `julia-bastian`       | 7.8  | 7.8   | 7.55   |       |        | 0.1   | current                  |
| `kai-wendlandt`       | 7.4  | 7.32  | 7.03   |       |        | 0.1   | current                  |
| `kamil-kubica`        | 7.6  | 7.65  | 7.17   |       |        | 0.15  | current                  |
| `malte-burkert`       | 8.45 | 8.38  | 7.9    |       |        | 0.2   | current                  |
| `markus-andrezak`     | 6.85 | 6.75  | 6.72   |       |        | 0.1   | current                  |
| `markus-rother`       | 7.17 | 7.05  | 7.03   |       |        | 0.1   | current                  |
| `martin-westphal`     | 7.62 | 7.62  | 7.47   |       |        | 0.15  | current                  |
| `matthias-lau`        | 8.1  | 8.0   | 7.95   |       |        | 0.3   | current                  |
| `nermin-caluk`        | 8.03 | 7.92  | 7.6    |       |        | 0.15  | current                  |
| `oliver-tischlinger`  | 8.35 | 8.35  | 8.12   |       |        | 0.2   | current                  |
| `ralf-hueller`        | 7.75 | 7.7   | 7.42   |       |        | 0.25  | current                  |
| `sebastian-jespersen` | 7.88 | 7.85  | 7.42   |       |        | 0.1   | current                  |
| `semjon-mossinger`    | 8.25 | 8.2   | 7.97   |       |        | 0.15  | current                  |
| `stefan-grothkopp`    | 7.88 | 7.72  | 7.52   |       |        | 0.25  | current                  |
| `steffen-clemens`     | 7.45 | 7.28  | 7.3    | 6.62  | 6.62   | 0.6   | current                  |
| `tereza-iofciu`       | 7.38 | 7.5   | 7.38   | 7.83  | 7.6    | 0.2   | larger original, retouch |
| `tobias-schlitt`      | 7.78 | 7.78  | 7.75   |       |        | 0.2   | current                  |
| `verena-traub`        | 8.18 | 7.9   | 7.75   |       |        | 0.2   | current                  |
| `viktor-shcherban`    | 7.55 | 7.6   | 7.55   |       |        | 0.1   | current                  |

- `johann-laur`: 8.22 against 7.15, ahead with both models (Claude 7.45 to 6.2, Codex 9.0 to 8.1)
  and in both runs. Sharpness 8.62 against 6.62.
- `jannik-streek`: 7.9 against 7.3. The larger file is the same photo cut closer, so the head is
  larger in the slot.
- `tereza-iofciu`: 7.83 against 7.38. Only 28 px wider; sharpness 7.75 against 6.62.
- `hendrik-hemken`: 8.08 against 7.65, a tie: run 1 led by 0.20 and Codex by 0.30, both inside the
  noise of 0.40. The larger file had to be cut closer (fit 7.5 against 8.25); a wider original
  would likely win.
- `jan-milz`: retouch alone, 7.53 against 7.33, a tie: Claude led by 0.15 at a noise of 0.15.
- `steffen-clemens`: the Tudock original loses, 6.62 against 7.45, on natural (5.75 against 7.88).
- sharp-2 beat its unsharpened twin for 3 of 33 people and won nowhere against the current file.
  Reviewers marked it down on natural.
- `matthias-lau`: his OOP studio portrait scored 8.1, the retouched versions 8.0 and 7.95. The
  website's earlier 4.6 to 6.8 was the AI astronaut image, which practitioners v1.0.3 still carried.

Review: medium, because a CTO's first look at the team page decides whether the trainers seem
credible.
