---
name: job-application
description: "Tailor a CV and cover letter to a specific job posting from the user's real experience, English or German. Use for /apply, a pasted job ad, 'cover letter for...', Anschreiben."
---

# Job application

Only the user's real experience. Never invent employers, titles, dates, metrics or tools.

## 1. Inputs
- The posting (fetch the URL or use the paste).
- The user's CV / portfolio / past notes. Missing -> ask for the CV once.

## 2. Decode the posting
| Extract | Notes |
|---|---|
| Must-haves | hard requirements, stated years, tools |
| Nice-to-haves | |
| The real problem | what this hire is meant to fix (read between the lines; label as inference) |
| Their words | recurring terms to mirror |
| Logistics | location/remote, contract type, language, deadline, how to apply |

## 3. Match
| Requirement | Evidence from the user's history | Strength: strong / partial / gap |
Tell the user the gaps plainly. For each gap: adjacent experience to cite, or leave it out. Verdict: **APPLY / STRETCH / SKIP**, one line why.

## 4. CV tailoring
- Reorder and trim; lead each role with the bullets that match must-haves.
- Bullet shape: action + what + result. Use numbers only if the user supplied them.
- Mirror the posting's terms where true. 1-2 pages.

## 5. Cover letter
- 180-280 words, 3-4 short paragraphs:
  1. Why this company/role - one specific, checked fact about them.
  2. The two strongest matches, as short stories with outcomes.
  3. What the user would do in the first months (tied to "the real problem").
  4. Close: availability, portfolio link.
- No "I am writing to apply", no adjective stacks, no restating the CV.
- **German:** formal register (Sie), "Sehr geehrte/r ..." with a named contact if findable, otherwise "Sehr geehrtes Team von X"; close "Mit freundlichen Grüßen". Natural German, not translated English; keep it equally short.

## 6. Check
- Every claim traceable to the CV or the user's words.
- Company name, role title, contact name spelled exactly as in the posting.
- Read once for AI-sounding phrases; cut them.

## Output
Match table + verdict, tailored CV changes (as a diff list), the letter, 3 likely interview questions from the gaps.
