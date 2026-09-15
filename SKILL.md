---
name: the-winning-offer
description: Use this when the founder is building their offer, from people they already know or from the market. They say "/the-winning-offer I put my interview with <name> in squad/interviews. Build the offer from it." (the warm entry), "/the-winning-offer" (the cold entry; spoken, "run the Winning Offer"), or "Here is my Apify token: ____. Use it for the Winning Offer." (the optional wiring). Warm: each interview becomes a folder under squad/clients/ and rebuilds squad/business.md. Cold: 5 questions, then the market read. Both score 7 gates and end on one answer: this holds, or it fails a gate and why. It never sends, never prices past the founder's number, and never invents a quote.
---

# The Winning Offer

Turn what buyers said, on a call or in public, into ONE offer document at `squad/business.md`,
scored through 7 gates and closed on one answer.

**The first message of a fresh run** (no `squad/business.md`, no `squad/clients/`) carries this
line, word for word:

> This skill is a base. Once you have done it your way, tell your squad "update the skill to do
> it like this."

`.claude/squad-roots.md` is the per-repo instance file every member-run skill reads first, in
any founder's repo, and its rows win over the `squad/` paths below, which are worked examples.
A row reading "(none yet)" is unanswered, not an override.

**The 3 lines the founder says:**

- "/the-winning-offer I put my interview with <name> in squad/interviews. Build the offer from it." The warm run.
- "/the-winning-offer" (spoken, "run the Winning Offer"). The cold run.
- "Here is my Apify token: ____. Use it for the Winning Offer." The wiring.

**First, 4 files next to this one must open:** `references/recording.md`,
`references/card-template.md`, `references/scorecard.md`, `references/research-method.md`. Any
missing: stop and say the skill folder was copied without its `references/`.

## The files

1. `squad/business.md`: THE file, the offer document, read by every later skill. A cold run
   writes `## THE FIVE ANSWERS` here first, then the document replaces the whole file.
2. `squad/offer-research.md`, cold run only: the receipts, under the exact headings
   `references/research-method.md` names. `## BUYER LANGUAGE` is compiled from
   `squad/clients/*/notes.md` first, and nobody else writes it. A warm run writes nothing here.
3. `squad/clients/<first-last>/transcript.md` and `notes.md`, one per person. `transcript.md`'s
   first line is `source: <file name> · <date>`, the only record a file was processed.
4. `.claude/squad-roots.md`: the 6 rows in THE ROOTS, nothing else touched.
5. `.mcp.json` in the company folder, on the wiring paste only.
6. `~/.squad/whisper` (`%USERPROFILE%\.squad\whisper` on Windows), on a recording, on one yes.

`squad/interviews/` is the founder's folder. Read it, create it empty when missing, never
write, rename or delete a file in it.

**Resuming.** Read `squad/interviews/`, `squad/clients/`, `squad/business.md` and
`squad/offer-research.md` before asking anything, and continue at the first thing missing. A
stamped document plus a new interview file is a rebuild, and the yes is asked again on the lines
that changed. Never re-ask what the files answer, never re-run research on disk, never process a
file twice.

## The warm run

**The interviews.** Every file in `squad/interviews/` that no `squad/clients/*/transcript.md`
names on its first line is this run's work, oldest first, even when the founder named only one;
say which you found. Any other file type is named in one line and skipped. The name is the file
name (`daniel-kim.txt` is Daniel Kim); the date comes from the text, the founder's line, or the
file. Ask "Who was this with?" only when the file name says nothing (`call-1.m4a`). Nothing
unprocessed: ask for the recording or the transcript in `squad/interviews/`, named after the
person, and wait. A recording is transcribed on the laptop the way `references/recording.md`
says. Its one yes is asked only when `~/.squad/whisper` is missing; that folder is the record
it was given. Never a paid service, nothing uploaded. Language is read, never asked. Quotes
stay in the language they were said in; the notes and the document follow the roots file's
voice sample.

**The folder.** `squad/clients/<first-last>/`, the name as the file names it, lowercased and
hyphenated (a first name alone is the folder name). `transcript.md` opens with
`source: <file name> · <date>`, then the text as it arrived; a transcript missing that line gets
it added first. `notes.md` opens with `# Name · what they do · date` and holds these 7 headings,
by exact string, in this order:

| Heading | Holds |
|---|---|
| `## QUOTES` | verbatim lines: a problem, a cost, a spend, an ask, a next step. Each labeled `(warm call · Name · date)` |
| `## THE PROBLEM` | 3 at most, each pointing at its quote |
| `## THE COST` | a number the text supports, or the question that gets it |
| `## WHAT THEY PAY NOW` | a fact ("$400 a month on a VA"), or "unknown". Never a price |
| `## THE IDEA` | what the founder would deliver to this person |
| `## THE MODEL` | agency, consulting or software, and why in 6 words |
| `## THE NEXT STEP` | the date they agreed to, or "none" |

Then one line, **Saved: `squad/clients/<first-last>/notes.md`**, and nothing of its contents.

**The document.** Read every `squad/clients/*/notes.md` on disk and rebuild `squad/business.md`
whole, in the shape of `references/card-template.md`, scored by `references/scorecard.md`.
Every buyer-worded line comes off `## QUOTES`; when folders split on THE MODEL, the one the
strongest quotes back wins. The document always prints. A cold run's market headings in
`squad/offer-research.md` keep their receipts; only call-sourced sections are rewritten, and
the mode line reads `cold · market + N calls`; `warm · N calls` prints only where no cold run
has happened. Ask at most 2 things no call and no document answered, in one message: what you
sell in one sentence, and the price. A price already on the document carries forward as it
stands, and the yes is the confirm.

**The yes,** below, with one extra exit. Say the files processed back in one line first. **"One
more call"** ends the run for tonight, the document stays unstamped, and the last line says to
drop the next file in `squad/interviews/` and say the line again.

## The cold run

**The 5 questions.** Read every `squad/clients/*/notes.md` first, compile `## BUYER LANGUAGE` in
`squad/offer-research.md` from them, and say back in one line how many calls, how many quotes,
and what they never touched. Then ask, in one numbered message:

1. What do you sell, in one sentence?
2. Who buys it? (job title or situation, not demographics)
3. What does it cost, and how does it get delivered?
4. How did anyone who ever paid you find you? If nobody has, say so.
5. Is there something different you keep thinking you SHOULD sell instead?

Nobody has paid yet is an answer. In the same message, and only here, ask for 5 to 10 real lines
from the founder's own inbox, DMs or group, "skip if you have none". A warm document already
answers the first 3 (THE SENTENCE, WHO, PRICE and THE MODEL): restate each for a confirm or a
correction, never the question again, and the same for `## THE FIVE ANSWERS` on disk. Write the
answers into `squad/business.md` under `## THE FIVE ANSWERS`, directly above the mode line, so
the `confirmed` stamp stays the last line. A changed answer to question 2, a new buyer, rewrites
every market heading in `squad/offer-research.md` and its `## SCORECARD`.

**The wiring** runs alone, on the token paste. Write `.mcp.json` in the company folder from this
skill's `mcp.json.example`, the token in place of the placeholder; an existing `.mcp.json` gets
the block merged in, nothing else touched. Never print the token back, never ask the founder to
open or edit a file. Then one line: quit and reopen Claude Code here, and type
`/the-winning-offer` again.

**The read.** `references/research-method.md`, followed exactly, with one amendment: the calls
already ran pass 1, so LISTEN fills the gaps they left, and scraped quotes go BELOW the warm
ones under `## BUYER LANGUAGE`, each with its own source label. Apify tools not loaded this
session: say one sentence first, "Reddit and YouTube comments are out until a token is pasted;
everything else is read."

**The price,** below. Gate 7's number chain from `references/scorecard.md` goes in that same
message; "I do not know" is an answer.

**The document.** Build, score and attack by `references/scorecard.md`, receipts under
`## SCORECARD` and the 3 self-attacks under `## ATTACK LOG`. Then write `squad/business.md`
whole, in the shape of `references/card-template.md` (`## THE FIVE ANSWERS` and any warm
document fold into WHO and THE MODEL). Never invent content so a heading can appear; later
skills read these headings by name. The mode line and its stamp are that template's last
section. Gate 2 failing kills the run: no document, say so with the receipt, and ask for a buyer
who has money.

## The price

One number, never a range, and never a price, a tier or a cap the founder did not decide. For a
service the ladder is $997, then $2,997, then $4,997.

Hold up ONE number: the price already on `squad/business.md`, else the first rung, $997 (a
higher rung only when a call or the operator table argues it, and say why in one line).

Ask for a yes or a different number, never an open question. The yes takes the held number, a
different number takes that one, anything else leaves it standing.

A number a buyer said on a call (what they pay now, what they were quoted) is a fact, never
the price.

PRICE prints the number as a fact, never blank and never marked.

## The yes

Print the file path, then THE SENTENCE, THE PROMISE, the first line of PRICE and the bold line
of THE ANSWER, as they stand, and nothing else of the document.

Then 2 lines, and stop: read the sentence and the promise out loud and change any word that does
not sound like you; then the yes (warm run, or "one more call").

The yes stamps the mode line `confirmed <today's date>`, the only record the gate happened.

A no is an objection with a name: rewrite that one thing from the quotes (cold run, one more
entry under `## ATTACK LOG`), re-print only the lines it changed, then ask again.

THE WARRANTY covers what the founder controls, never money the buyer will make.

## The roots

Last, no questions. Fill only the rows THIS run answered, in place, change nothing else. Never
guess a row.

| Row | Value |
|---|---|
| clients | `squad/clients/` (warm, written once) |
| interviews | `squad/interviews/` (warm, written once) |
| product word | the one word, off the BRAND line |
| accent color | the hex from the BRAND line, or `#146ef5 until you pick one` |
| data sources | `squad/business.md`, plus `squad/offer-research.md` once a cold run wrote it |
| research mode | `wired` or `unwired ladder`, the cold run's mode; `warm only` when none has run |

Then what to type next: after a yes, `/the-close script`; after a gate-2 kill, `/the-winning-offer`
again with the new buyer.

## Never

- Never send, post or book.
- Never price past the founder's own number. One number, decided by them; a buyer's number is a fact.
- Never invent a quote, a number, a name or a need. A cost the text does not support is a
  question; a need nobody said stays out.
- Never paraphrase a quote, or save a paraphrase as one. Verbatim, labeled, dated. A call's line
  outranks a scrape's; same claim, 2 sources, the one with a name on it wins.
- Never a guarantee.
- Never a menu of options. One answer.
- Never ask the founder to edit a file or organise their notes. The one thing they do by hand is
  drop one file per call in `squad/interviews/`, named after the person.
- Never make the founder re-narrate a call whose words are on disk.
- Never print the whole document into chat: the path, and the lines the yes needs.
