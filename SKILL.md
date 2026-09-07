---
name: the-winning-offer
description: Use this when the founder is building their offer, from people they already know or from the market. They say "/the-winning-offer I put my interview with <name> in squad/interviews. Build the offer from it." (the warm entry), "/the-winning-offer" (the cold entry; spoken, "run the Winning Offer"), "Here is my Apify token: ____. Use it for the Winning Offer." (the optional wiring), or "continue the Winning Offer" (picking a stopped run back up). 2 entries, one equation, one document. Warm: every interview dropped in squad/interviews/ becomes a folder under squad/clients/ and squad/business.md is rebuilt from every call so far. Cold: 5 questions, then the market read. Both score the same 7 gates and end on one answer: this holds, here is the blind spot, start. It never sends, never prices past the number the founder said, and never invents a quote.
---

# The Winning Offer

One equation, 2 sources. **Your work, in one line: turn what buyers said, on a call or in
public, into ONE offer document at `squad/business.md`, scored through 7 gates and closed on
one answer.** The founder's part: the calls, one file per call in `squad/interviews/`, the yes
on the words, and one number.

Warm outranks cold. An offer built from 1 to 5 calls with people who already know the founder
is written in the buyers' own nouns. An offer read off the market is written from what
strangers say in public. The cold entry is for the founder with nobody to call, or whose
calls gave nothing. Both end in
the same file, the same gates and the same 2 closing sentences. A gate the calls never touched
prints `unscored: no call touched it`, and that blank is what the cold run, or week one,
attacks. Client folders, when they exist, are read first on every run, and a line from a call
outranks a line from a scrape every time.

This skill runs in ANY founder's repo. `.claude/squad-roots.md` is the per-repo instance file
every member-run skill reads first (founder name, voice sample, and the rows this skill
fills), and its values win over the `squad/` paths below, which are worked examples. A row
reading "(none yet)" is an unanswered field, not an override.

## The 2 entries, and how they are called

| Entry | The founder says | Beats |
|---|---|---|
| warm | "/the-winning-offer I put my interview with <name> in squad/interviews. Build the offer from it." | W0 and W1 once per unprocessed file, then W2 and W3 once. Then THE ROOTS |
| cold | `/the-winning-offer` (spoken, "run the Winning Offer") | C0 to C7. Then THE ROOTS |
| wiring | "Here is my Apify token: ____. Use it for the Winning Offer." | the one paragraph in C1, then stop |

A bare "continue the Winning Offer" reads the outputs, picks the beat off the resume table, and
says in one line which entry it entered and why.

## The run map (where you run, where you STOP)

| Beat | Mode |
|---|---|
| W0 THE INTERVIEWS | HUMAN INPUT: the recording or the transcript dropped in `squad/interviews/`, named after the person. AUTO: every file in that folder the run has not processed is read; audio and video are transcribed on the laptop, after one yes, once. One question only when nothing says who the person is |
| W1 THE FOLDER | AUTO: `transcript.md` (its first line naming the source file), `notes.md`, the `clients` and `interviews` roots rows once |
| W2 THE DOCUMENT | AUTO: `squad/business.md` rebuilt from every folder so far. HUMAN INPUT, at most 2 questions in one numbered message, only for what no call answered: the sentence, and one number held up for the price |
| W3 THE YES | **STOP · GATE: the path and the lines the founder reads out loud. "One more call" ends the run for tonight; the yes stamps it** |
| C0 THE FIVE | HUMAN INPUT: the 5 answers, pre-filled from a warm document when one exists |
| C1 THE PLAN | AUTO: the gap list and the Apify line. Then **STOP · GATE: the yes before any research runs, and 5 to 10 lines from the founder's own inbox with it** |
| C2 LISTEN | AUTO |
| C3 MAP | AUTO |
| C4 THE NUMBERS | AUTO: the model check. Then **STOP · GATE: one number held up; the founder says yes or a different number** |
| C5 BUILD · SCORE · ATTACK | AUTO |
| C6 THE DOCUMENT | AUTO: written whole into `squad/business.md` |
| C7 THE YES | **STOP · GATE: the same gate as W3** |
| THE ROOTS | AUTO: the rows this run answered |

THE ROOTS runs after either yes, and after a gate-2 kill. Never pause an automated beat to
ask a small question (batch it into the next gate); never run through a gate because the
answer seems obvious.

**Resuming.** The rule keys on the OUTPUTS, never on a session's memory. Check them in this
order and continue at the first one missing or incomplete.

| Missing or incomplete | Resume at |
|---|---|
| `squad/interviews/` holds a transcript or recording file whose name no `squad/clients/*/transcript.md` carries on its first line | W0 for that file, then W1, then the rebuild |
| no `squad/clients/` and no `squad/business.md` yet | no run has started: say so in one line and ask which entry, since a file in `squad/interviews/` starts the warm run and `/the-winning-offer` starts the cold run |
| a `squad/clients/*/` folder holds `transcript.md` and no `notes.md` | W1 for that folder |
| a `notes.md` is newer than `squad/business.md`, or no `squad/business.md` exists yet | W2, the rebuild |
| `squad/business.md` holds `## THE FIVE ANSWERS`, and `squad/offer-research.md` is absent or has no `## ALLOWED WORDS` | C1: restate the 5 answers for a confirm, never re-ask them. A `confirmed` stamp does not block this row: a warm document is the normal road into the cold entry |
| `squad/offer-research.md`'s `## SCORECARD` records gate 2 failing, and `squad/business.md` holds no offer document (it is absent, or holds only `## THE FIVE ANSWERS`) | the run is over on that buyer. Say gate 2 killed it and name the receipt. A new buyer at question 2 starts C0 again |
| `squad/offer-research.md` holds `## BUYER LANGUAGE`, and either a later heading `references/research-method.md` names is missing, or `squad/business.md` still holds `## THE FIVE ANSWERS` | the beat that writes the missing heading (`## SCORECARD` missing is C4 first, then C5); every heading present, C6 |
| `squad/business.md` holds the offer document (THE SENTENCE on it) and its last line carries no `confirmed <date>` stamp | THE YES only: never re-run the research, never re-read the calls |
| `.claude/squad-roots.md` is missing a row this run answers | THE ROOTS |
| every output present and `squad/business.md` stamped | nothing to continue: say so in one line |

A stamped document plus a new interview file is a rebuild: W0 and W1 run on the new file, W2
runs, the stamp comes off, and W3 asks the yes again on the lines that changed. Never re-ask a
question the files already answer; never re-run a research pass whose findings are on disk;
never parse a file a folder already holds twice.

## The outputs

1. `squad/business.md`: THE file. Its finished form is the one-page offer document, and every
   later skill reads it. On a cold run it first holds `## THE FIVE ANSWERS`; C6 replaces the
   whole file.
2. `squad/offer-research.md`, on a cold run only: the receipts, under the exact heading
   strings `references/research-method.md` names. `## BUYER LANGUAGE` is compiled from
   `squad/clients/*/notes.md` first, and nobody else writes that heading. A warm run writes
   nothing here; its gate grades, and the quote each rests on, go under THE ANSWER in the
   document.
3. `squad/clients/<first-last>/transcript.md` and `notes.md` (warm), one folder per person.
   The first line of `transcript.md` is `source: <file name> · <date>`; that line is the only
   record a file was processed.
4. `.claude/squad-roots.md`, given the `clients`, `interviews`, `product word`,
   `accent color`, `data sources` and `research mode` rows.
   Nothing else in it touched.
5. `.mcp.json` in the company folder, on the wiring paste only.
6. `~/.squad/whisper` (Mac and Linux) or `%USERPROFILE%\.squad\whisper` (Windows): the local
   transcriber, on a recording only, on the founder's one yes. That folder existing IS the
   record that the yes was given; a later recording goes straight to the transcription and the
   yes is never re-asked.

`squad/interviews/` is the founder's folder. This skill reads it, creates it empty when it is
missing, and never writes, renames or deletes a file in it.

## The equation (both entries run through this)

**The install check, before you spend any of the founder's input.** 4 files inside THIS
skill's folder, next to `SKILL.md`, must open: `references/recording.md`,
`references/card-template.md`, `references/scorecard.md`, `references/research-method.md`.
Any missing: stop and say the folder was downloaded without its `references/`, and to copy
the whole skill folder in again.

**The document** is `references/card-template.md`, in that order, under its law (a heading
per section, one-line paragraphs, a table wherever there are 3 or more columns of facts, THE
SENTENCE and THE ANSWER in bold, no paragraph over 40 words, no section past one screen),
written INTO `squad/business.md` as the whole file. Every unconditional heading present, THE
ANSWER and BRAND included; each conditional present or its condition false (SCARCITY + URGENCY only when something is
genuinely scarce, THE SWITCHING ITCH only when C0 question 5 surfaced one, THE NUMBERS only
when a chain was asked, at a cold run's numbers gate, WHAT WEEK ONE MAY ATTACK NEXT absent
when there is nothing in it).
Never invent content so a heading can appear; later skills read these headings by name. **The
mode line**, the document's last line, reads `warm · N calls`, `cold · market` or
`cold · market + N calls`; a cold run adds the tool mode in parens (`wired`, or `unwired
ladder`) and `thin` when the public read came back under about 5 quotes; the yes adds
`confirmed <date>`.

**The 7 gates** are `references/scorecard.md`, in its order: the model check, the value
equation, the gates, the self-attacks. Receipts or nothing. Where a gate can be graded off
something a buyer said on a call, grade it off that; a scraped receipt is the fallback. A gate
with no receipt prints `unscored`, on a warm run `unscored: no call touched it`, and an
unscored gate never fails the offer. On a cold run gate 2 failing kills the run (no document; a
different buyer, not a different offer); gates 1, 3, 4 and 5 failing print the second closing
sentence; 6 and 7 are diagnostic. On a warm run the document always prints, and any failing
gate prints the second closing sentence. The document ends on exactly one of the 2 forms in
the template, word for word: **"This offer holds. The blind spot is ___. Week one attacks ___.
Stop choosing. Start."** or **"This offer fails gate ___ because ___. Fix that before you build
anything else."**

**The numbers gate: one number held up, and the founder decides.** One number, never a range,
and you never print a price, a tier or a cap the founder did not decide. For a service the
ladder is $997, then $2,997, then $4,997. Hold up ONE number: the price already on
`squad/business.md` when one is there, else the first rung, $997 (a higher rung only when a
call or the operator table argues it, and say why in one line). Ask for a yes or a different
number, never an open question. A number a buyer said on a call (what they pay now, what they
were quoted) is a fact to hold up, never the price. Present the model pick with its precedent
and the held number together; when the fee is recurring, ask in the same message what visibly
stops for the buyer the day they cancel; then stop. The yes takes the held number, a different
number takes that one, and anything else leaves the held number standing. PRICE prints the
number as a fact, never blank and never marked.

**THE YES has 2 parts, and it is the founder's.** Print the file path, then THE SENTENCE, THE
PROMISE, the first line of PRICE and the bold line of THE ANSWER, as they stand, and nothing
else of the document. Then the ask, 2 lines, and stop: read the sentence and the promise out
loud and change any word that does not sound like you; then the yes (or, on a warm run, "one
more call"). The moment it comes, stamp the mode line `confirmed <today's date>`; that stamp
is the only record the gate happened. A no is an objection with a name: rewrite the thing they
objected to from the quotes (on a cold run, as one more entry under `## ATTACK LOG`) and
re-print the lines it changes, then the ask again. Never answer a no with a menu, and never
print the whole document into chat. BRAND is never asked here: the product word is the word
the founder already used for what they sell, and the accent color reads `#146ef5 until you
pick one` until the founder names a hex.

**THE ROOTS, last, no questions.** Fill only the rows THIS run answered, in place, and change
nothing else. Never guess a row.

| Row | Value |
|---|---|
| clients | `squad/clients/` (warm, written once) |
| interviews | `squad/interviews/` (warm, written once) |
| product word | the one word, off the BRAND line |
| accent color | the hex from the BRAND line, or `#146ef5 until you pick one` |
| data sources | `squad/business.md`, and `squad/offer-research.md` once a cold run wrote it |
| research mode | `wired` or `unwired ladder`, the mode the cold run ran in; `warm only` when no cold run has happened |

Then one line to the founder: this file holds their name, brand word, color and paths, and
every later part of the system reads it. Then the next line, what to type next: after a yes,
the offer is stamped at `squad/business.md` and `/the-close script` (g6) turns it into the
sales script; after a gate-2 kill, `/the-winning-offer` again, with the new buyer at
question 2.

## The warm entry

### W0 · THE INTERVIEWS

Reads: `squad/interviews/`. One file per call, named after the person: `daniel.m4a`,
`daniel-kim.txt`, `priya.vtt`.
Transcripts are `.txt`, `.md`, `.srt` or `.vtt`; recordings are `.m4a`, `.mp3`, `.wav`,
`.mp4` or `.mov`. Any other file in the folder is named in one line and skipped.

A file is processed when a `squad/clients/*/transcript.md` names it on its first line. Every
other file is this run's work, oldest first. The founder's line may name one person ("my
interview with Daniel"): still read every unprocessed file, and say which ones you found. The
founder never has to type a file name.

**No `squad/interviews/` folder, or nothing in it this run has not already processed:**
create the folder when it is missing, then one line, "drop the recording or the transcript in
`squad/interviews/`, named after the person", and wait.

The person's name is the file name (`daniel-kim.txt` is Daniel Kim). The call's date comes
from the text, from the founder's line, or from the file's own date, in that order. One
question, only when the file name says nothing (`call-1.m4a`): "Who was this with?"

**A recording** gets transcribed here, on the laptop, the way `references/recording.md` says.
When the transcriber folder is not there yet (`~/.squad/whisper`, or
`%USERPROFILE%\.squad\whisper` on Windows), ask one yes: install a local transcriber
(faster-whisper through pip in its own folder). Say in the same line that the model weights
download once and the recording never leaves the laptop. That folder existing is the record
the yes was given, so a later recording goes straight to the transcription and the yes is
never re-asked. On the yes, run the install, then the transcription with the smallest model
that runs cleanly (that file names the order), and the text lands as this person's
`transcript.md`. A 20-minute call takes a few minutes; say so and wait. An install that fails
gets one line naming MacWhisper on a Mac or Buzz on Windows, "export .txt, drop it in
squad/interviews/", and then waits. Never a paid service, nothing uploaded.

- Language is read, never asked. Quotes stay in the language they were said in; the notes and
  the document are written in the language of the roots file's voice sample.
- Never ask the founder to organise anything past one file per call in the folder. Messy is
  the format.

### W1 · THE FOLDER

Writes `squad/clients/<first-last>/`: the name as the file names it, lowercased and
hyphenated (a first name alone is the folder name).
`transcript.md` opens with `source: <file name> · <date>`, written by the transcriber itself
for a recording and by this beat for a transcript, and then holds the text as it
arrived; that first line is the record the file was processed, and it is never rewritten. A
`transcript.md` that came back without it gets the line added here, before anything else.
`notes.md` opens with `# Name · what they do · date` and holds these 7 headings, by exact
string, in this order, in one pass:

| Heading | Holds |
|---|---|
| `## QUOTES` | every line the person said that carries a problem, a cost, a spend, an ask or a next step, verbatim, each labeled `(warm call · Name · date)`; a one-line gloss under a quote in another language. A paraphrase is never saved as a quote |
| `## THE PROBLEM` | one line per problem, 3 at most, each pointing at the quote that carries it |
| `## THE COST` | a number the text supports (money or hours, and how often), or the question that would get it |
| `## WHAT THEY PAY NOW` | a fact line ("$400 a month on a VA"), or "unknown". Never a price |
| `## THE IDEA` | one line: what the founder would deliver to this person for this problem |
| `## THE MODEL` | one line: agency, consulting or software, and why in 6 words |
| `## THE NEXT STEP` | the date they agreed to, or "none" |

Then add the `clients` and `interviews` rows to `.claude/squad-roots.md` when they are not
there yet. Say one line, **Saved: `squad/clients/<first-last>/notes.md`**, and nothing of its
contents. Another unprocessed file: back to W0 for it. None left: straight into W2.

### W2 · THE DOCUMENT

Read every `squad/clients/*/notes.md` on disk, this run's included, and rebuild
`squad/business.md` whole through the equation: the template, the gates, the closing sentence.
Every call-sourced line is rebuilt from the folders, never carried over from the last document,
so the third call can move what the first call set. Nothing is written to
`squad/offer-research.md` on a warm run.

- **When `squad/offer-research.md` already carries a cold run's market headings,** the rebuild
  keeps those receipts in the document (every gate the market scored, read from
  `## SCORECARD`) and only the call-sourced sections are rewritten from the folders.
  The mode line then reads `cold · market + N calls`. `warm · N calls` prints only in a repo
  where no cold run has happened.
- The receipts are the calls. THE DREAM OUTCOME, THE SENTENCE, THE PROMISE and the fear column
  of THE STACK are built from `## QUOTES`, in the buyers' words. THE MODEL is the model the
  folders agree on; when they split, the one the strongest quotes back, and say so. WHO refuses
  whoever the calls showed has no money or no urgency.
- The gate grades go under THE ANSWER as a short table, `gate · grade · the quote it rests
  on`. Gate 7's chain is not asked here. A gate no folder gives a receipt for, and no cold run
  scored, prints `unscored: no call touched it`. The week-one blank goes to the earliest
  unscored gate.
- **What no call and no `squad/business.md` on disk answered gets asked, 2 questions at most,
  in one numbered message, before the document prints:** what you sell in one sentence (only
  when no folder carries a named ask the founder will stand behind), and the price, held up as
  one number the way the numbers gate says, the first rung, for a yes or a different number. A
  buyer's own number stays a fact on the WHAT THEY PAY NOW line.
- **The price carries forward.** PRICE comes off the document already on disk. Carry it as it
  stands into the rebuild; W3's yes is the confirm, and the number is never asked again.

The mode line reads `warm · N calls`, N being the folders read, and `cold · market + N calls`
when a cold run's market headings are already on disk.

### W3 · THE YES

THE YES from the equation, with one extra exit. Say it back in one line first: the files
processed, by name, and the document rebuilt from N calls. Then the path, and THE SENTENCE,
THE PROMISE, the first line of PRICE and the bold line of THE ANSWER, as they stand. **"One
more call"** ends the run for tonight, the document stays unstamped, and the last line says
what to do next: drop the next file in `squad/interviews/` and say the line again. The yes
stamps it, then THE ROOTS runs.

## The cold entry

### C0 · THE FIVE

**Client folders first.** Read every `squad/clients/*/notes.md` on disk, compile
`## BUYER LANGUAGE` in `squad/offer-research.md` from them (every quote, verbatim, with its
label), and say the read back in one line: how many calls, how many quotes, what the calls
never touched. That last part is the research brief. No folders: say once that the market
read is the thinner source, and go.

**Then the 5 questions, in one numbered message.** A warm document at
`squad/business.md` already answers the first 3 (THE SENTENCE is 1, WHO is 2, PRICE and THE
MODEL are 3): restate each and ask for a confirm or a correction, never the question again.
`## THE FIVE ANSWERS` already on disk: restate all 5 the same way. Otherwise ask only these:

1. What do you sell, in one sentence?
2. Who buys it? (job title or situation, not demographics)
3. What does it cost, and how does it get delivered?
4. How did anyone who ever paid you find you? If nobody has, say so.
5. Is there something different you keep thinking you SHOULD sell instead? (The switching
   itch. Carry it through: the market read tests that category as one of the seats, and the
   document gives it one line.)

Nobody has paid yet is the founder this arc was built for: questions 3 and 4 get one honest
line each, and the run fills the hole at the numbers gate. If an answer is vague, ask a
follow-up until you could explain the business to a stranger in 2 sentences, and stop the
follow-ups the moment the honest answer is that there is nothing there yet; that line is the
answer. Write them to `squad/business.md` under `## THE FIVE ANSWERS`, one labeled line per
question; a warm document stays as it is, and `## THE FIVE ANSWERS` is written directly above
its mode line so the `confirmed` stamp stays the file's last line, until C6 rewrites the file.
A changed answer to question 2, a new buyer, rewrites every market heading in
`squad/offer-research.md` and its `## SCORECARD`; the old receipts belong to a buyer this run
no longer serves.

### C1 · THE PLAN, then the yes

Play back what you heard in 2 sentences. List what you are about to research and why in the 3
to 5 lines the gate needs, each tracing to a gap the calls left. **The
Apify line, one sentence, only when the Apify tools are not loaded in this session:** "Reddit
and YouTube comments are out until a token is pasted; everything else is read." Wired means
the Apify tools are loaded in this session; nothing is probed. **In the same message, ask for
5 to 10 real lines from the founder's own inbox, DMs or group, "skip if you have none"**; this
is the only time the run asks for them. Then get the yes. Research without agreement gets
thrown away.

**The wiring, when the founder pastes "Here is my Apify token: ____. Use it for the Winning
Offer."** Write `.mcp.json` in the company folder yourself, from this skill's
`mcp.json.example`: the `apify` block with the token in place of the placeholder, and an
existing `.mcp.json` gets the block merged in with nothing else in it touched. Never print the
token back, never ask the founder to open or edit a file. Then one line: quit and reopen
Claude Code in this folder, and type `/the-winning-offer` again. Nothing else runs in that
turn.

### C2 · LISTEN, then C3 · MAP

Read `references/research-method.md` and follow it exactly, with 2 standing amendments.
**One:** the calls already ran pass 1, so LISTEN fills the gap list from C0 (the buyers no
folder represents, the objection nobody voiced, the price nobody named) instead of starting
cold, and scraped quotes go BELOW the warm quotes under `## BUYER LANGUAGE`, each with its own
source label. **Two:** the thin test counts PUBLIC quotes only; under about 5 puts the `thin`
flag on the mode line, nothing else, and the inbox lines the founder pasted at C1 go under
`## BUYER LANGUAGE` labeled `(founder's inbox ...)`. MAP runs in full
every time: only the market read says what is already sold to this buyer and for how much.
State the reason before each pass; write pass 1 to the file before pass 2 starts.

### C4 · THE NUMBERS

The model check from `references/scorecard.md`, then the numbers gate from the equation: the
number held up is the price on `squad/business.md` when one is there, else the first rung.
This gate also asks gate 7's number chain (sent, replies, calls, money, plus views and clicks
where a content lane exists), in the same numbered message, never mid-SCORE.

### C5 · BUILD, SCORE, ATTACK

`references/scorecard.md`, in its order. BUILD the sentence and the promise through the value
equation, in the words the calls and the rooms gave you. SCORE the 7 gates with the receipt
next to each, under `## SCORECARD`. ATTACK the draft 3 ways in writing under `## ATTACK LOG`,
and re-read THE PROMISE against gate 6's weakest dial before anything prints.

### C6 · THE DOCUMENT, then C7 · THE YES

Produce the document into `squad/business.md`, replacing the whole file (`## THE FIVE
ANSWERS` and any warm document fold into WHO and THE MODEL). The mode line reads
`cold · market`, or `cold · market + N calls` when folders were read, with the tool mode and
the thin flag. Then THE YES from the equation, and THE ROOTS.

## Rules

- Every message to the founder is short: a header, then the few lines the moment needs.
  Operator maps, price bands and gate grades live in the files; chat carries the file path and
  the lines a gate needs, never a whole file.
- Never send anything, never post, never book.
- Never price past the founder's own number. One number, decided by them at the gate; a
  buyer's number is a fact, never the price.
- Never invent a quote, a number, a name or a need. A cost the text does not support is a
  question; a need nobody said stays out.
- Never paraphrase a quote, and never save a paraphrase as one. Verbatim, labeled, dated. A
  line from a call outranks a line from a scrape; same claim, 2 sources, the one with a name
  on it wins.
- Never a menu of options. The founder came here to stop deciding. Re-run this skill when a
  real season of data says to, not when the doubt itches.
- Never ask the founder to edit a file or organise their notes. The one thing they do by hand
  is drop one file per call in `squad/interviews/`, named after the person. The one install
  this skill makes is the transcriber, on one yes; only when that install fails does the
  founder install anything themselves, and then it is the one line in W0 and nothing more.
- Never make the founder re-narrate a call whose words are already on disk.
