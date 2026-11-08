# AI-regenerated portraits, 08.11.2026: nothing swapped

No portrait changed. All 12 candidates, four per person for three people, fail the identity gate.
Two of Markus Andrezak's reach 0.90 against his current portrait, but none reaches its reference
photos. So no schema field was added and nothing was released.

## Scope

The bar is a score below 7 of 10 once the noise of that person's row is taken off, in today's
review (`2026-11-08-portraits.md`). The repository's median of 7.78 would have taken in 15 of the 33
people, which does not fit a photo that is really bad. Retouch and sharp-2 won for none of the
three.

| Folder             | Current | Noise | Retouch | Retouch + sharp-2 | Status in the entry |
| ------------------ | ------- | ----- | ------- | ----------------- | ------------------- |
| `markus-andrezak`  | 6.85    | 0.1   | 6.75    | 6.72              | draft               |
| `bastian-weinlich` | 7.0     | 0.1   | 6.95    | 6.95              | draft, black-white  |
| `bjorn-rochel`     | 7.05    | 0.1   | 7.05    | 6.97              | active              |

`markus-rother` (7.17, noise 0.1) is the first one above the bar.

## Sources and references

All are public pages, fetched 08.11. LinkedIn was out of reach for this run.

| Person           | Reference                                                  | Size       | Cosine to the current portrait |
| ---------------- | ---------------------------------------------------------- | ---------- | ------------------------------ |
| Markus Andrezak  | IT-Tage speaker page, `200-Markus-Andrezak.jpg`            | 200 × 200  | 0.678                          |
| Markus Andrezak  | Sessionize profile                                         | 400 × 400  | 0.520                          |
| Markus Andrezak  | Crafting Products speaker page, `markus_portraet-high.png` | 557 × 701  | 0.629                          |
| Bastian Weinlich | GitHub avatar (the same shot as the current file)          | 389 × 389  | 0.965                          |
| Bastian Weinlich | tecnovy trainer page, `weinlich.webp` (colour)             | 450 × 450  | 0.626                          |
| Bastian Weinlich | wps.de team page, `04-weinlich-ne5a9980.jpg` (colour)      | 1240 × 960 | 0.654                          |
| Björn Rochel     | GitHub avatar (the same shot as the current file)          | 400 × 400  | 0.964                          |
| Björn Rochel     | bjro.de, `bjro.jpg`                                        | 800 × 800  | 0.517                          |
| Björn Rochel     | agentic.hamburg speaker image                              | 800 × 800  | 0.529                          |

Björn Rochel's 180 px `bjoern-portrait.png` on bjro.de (0.533) is too small to use. Gmail, read-only:
30 messages naming one of the three carry an attachment, four of those an image above 15 KB, and
none of the four shows a face. A control query for any `.jpg` attachment returned its limit of 50
messages (estimate 201), so the search works.

Controls for the face match (OpenCV SFace, faces scaled to the same width first): other people
against Markus Andrezak's portrait 0.218 and 0.018. Each reference was checked by eye on a contact
sheet and shows the right person.

## Method

Codex image generation (`codex exec`, gpt-6.1-terra) from the current portrait plus the references.
Method 1 edits the current portrait. Method 2 creates a new photo with the current portrait as the
main identity source. Each ran twice with the same prompt, with no re-rolls and no prompt changed
after a measurement. Every prompt asked for the same person and age, the same expression and head
pose, the repository's framing, a calm background, and no invented pores, wrinkles, stubble or
skin texture. Bastian Weinlich's prompts colourise from his two colour references.

## The identity gate, fixed before the first measurement

- A: cosine against the current portrait at least 0.90.
- B: landmark residual at most 6.9 %, the largest value among the earlier run's four candidates
  (website item `review-portraits-ai`).
- C: cosine against each reference at least 0.90, as the brief states it.
- D, reported beside C: against a reference from another shoot, the candidate's cosine is at least
  the real current portrait's cosine to that reference.

## Results

Cosines to the references in the order of the table above.

| Candidate    | Cur   | LM % | Ref 1 | Ref 2 | Ref 3 | A   | B   | C   | D   |
| ------------ | ----- | ---- | ----- | ----- | ----- | --- | --- | --- | --- |
| markus m1-1  | 0.896 | 1.5  | 0.645 | 0.433 | 0.623 | no  | yes | no  | no  |
| markus m1-2  | 0.890 | 2.3  | 0.629 | 0.440 | 0.588 | no  | yes | no  | no  |
| markus m2-1  | 0.906 | 1.0  | 0.669 | 0.520 | 0.586 | yes | yes | no  | no  |
| markus m2-2  | 0.925 | 2.3  | 0.609 | 0.496 | 0.593 | yes | yes | no  | no  |
| bastian m1-1 | 0.884 | 1.1  | 0.879 | 0.666 | 0.698 | no  | yes | no  | no  |
| bastian m1-2 | 0.814 | 1.2  | 0.821 | 0.619 | 0.640 | no  | yes | no  | no  |
| bastian m2-1 | 0.771 | 0.9  | 0.790 | 0.643 | 0.681 | no  | yes | no  | no  |
| bastian m2-2 | 0.812 | 1.7  | 0.804 | 0.667 | 0.668 | no  | yes | no  | no  |
| bjorn m1-1   | 0.893 | 1.0  | 0.883 | 0.524 | 0.536 | no  | yes | no  | no  |
| bjorn m1-2   | 0.852 | 1.4  | 0.855 | 0.472 | 0.488 | no  | yes | no  | no  |
| bjorn m2-1   | 0.832 | 2.3  | 0.810 | 0.532 | 0.526 | no  | yes | no  | no  |
| bjorn m2-2   | 0.810 | 1.5  | 0.824 | 0.557 | 0.561 | no  | yes | no  | no  |

Why each candidate failed is not yet explained beyond these numbers; no control separated colour,
pose or prompt.

## Gate C cannot be met as written

Two photos of one person from different shoots score 0.52 to 0.68 here. A portrait within 0.90 of
both the current file and such a reference has to sit between them: two angles of at most 25.8°
add up to at most 51.7°, which is a cosine of 0.62 between the two photos. Björn Rochel's two
references (0.517, 0.529) and Markus Andrezak's Sessionize photo (0.520) lie below that, so no
image can pass there; the others leave only a narrow midpoint. The bar holds for a same-shot
reference, as in the earlier controls at 0.91 to 0.93, and says nothing about a photo from another
day. Rejecting on it here changes no outcome: bar D, the fairer version, fails for all 12 too, and
A alone would leave only the two Markus Andrezak candidates.

## Blind review

Not run. The brief rejects every candidate that fails the gate, so no candidate was left to score.
For the same reason there are no identity answers from reviewers.

Review: none, because no candidate survived the identity gate.
