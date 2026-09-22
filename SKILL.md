---
name: execution-genesis-offer
description: 'Use this when the founder needs their offer. They type "/execution-genesis-offer", say "run execution genesis offer", or paste "Here is my Apify token: ____. Use it for execution genesis offer." It asks 5 questions, finds who already sells to that buyer and for how much, reads the 3 winners whole, digs up the words buyers use about the problem, and writes squad/business.md: the sentence, the buyer, the problem, the price, what he gets, how it gets built and with which tools, and the 5 objections with their answers. It never sends anything and never invents a quote.'
---

# execution-genesis-offer

1 output: `squad/business.md`, the offer. 5 steps: the 5 questions, the sellers, the dig, the page,
the build. The page ends on 4 sections the buyer can hold in his hand: what the winners sell, what he
gets, how it gets built and with what, and what he says before he pays.

The first message of a fresh run (no `squad/business.md`) carries this line, once:

> This agent is a base. Once you have done it your way, tell your squad "update the agent to do it like this."

**Before anything.** Open `references/the-dig.md` and `references/the-page.md` next to this file.
Either one missing: stop and say the agent folder was copied without its `references/`. Read the
`founder name` row of `.claude/squad-roots.md`; "(none yet)" counts as empty.

**Resume.**
- Continue at the first missing piece off disk: an empty BUYER WORDS is step 3, an empty THE PROBLEM or THE PROMISE is step 4, an empty WHAT HE GETS, THE BUILD or OBJECTIONS is step 5.
- Never re-run a paid dig that already wrote its lines: the sellers table and BUYER WORDS are the dig's raw finds, kept on the page, and there is no second file.

## 1. The 5 questions

No page on disk: send this as 1 message, word for word.

```text
This agent is a base. Once you have done it your way, tell your squad "update the agent to do it like this."

5 questions before I read anything online. Answer them in 1 message.

1. What do you sell, in 1 sentence?
2. Who buys it?
3. What does it cost, and how do you deliver it?
4. How did the people who paid you find you? If nobody has paid you yet, say "nobody yet".
5. Is there something else you keep thinking you should sell instead?

"Nothing yet" or "I don't know" is a real answer to any of them.
```

The Apify tools are not loaded: add this line to the end of that same message.
`I read Reddit and YouTube comments through Apify, and it is not connected yet. Make a free account at apify.com (no card, $5 of use free every month), copy your token from console.apify.com/settings/integrations, and paste it here like this: Here is my Apify token: ____. Use it for execution genesis offer.`

Answers 1, 2 and 5 all empty: ask 1 more thing, alone, and its answer is the buyer:
`Name 1 kind of business or person you'd like to help.`

A finished page on disk: skip the questions and send this, filled off the page.

```text
Your page says this. It came from your 5 answers and the sellers I read.

1. What you sell: <THE SENTENCE>
2. Who buys it: <WHO line 1>
3. What it costs and how you deliver it: <PRICE line 1> · <THE SHAPE>
4. Where buyers find you: <WHO line 2>
5. The other idea: <WHY THIS ONE>

Same, or what changed?
```

- "Same": print step 4's lines and stop.
- A new idea or a new buyer (answer 1, 2 or 5): run steps 2 to 4 again, and the new page replaces the old one whole.
- A new price or delivery (answer 3): rewrite PRICE, THE SHAPE and THE PROMISE only.
- A new answer 4: rewrite WHO line 2 only.

A `squad/business.md` in any other shape counts as no page.

## 2. The sellers

Run part 1 of `references/the-dig.md`: up to 10 sellers for the idea in answer 1, and up to 10 for
the idea in answer 5 when there is one, each read off the seller's own page. Pick the offer by the
pick rule there, silently.

No seller with a published price anywhere, and no number in answer 3: PRICE has no source, so send
the 1 line from `references/the-dig.md` and wait for a price or a different buyer, then run this
step again.

Otherwise write `squad/business.md` whole (no founder name: the title reads `# The offer · <YYYY-MM-DD>`), in the shape of `references/the-page.md`, with THE
SENTENCE, WHO, WHAT HE PAYS NOW, THE SHAPE, PRICE, WHO ALREADY SELLS TO HIM, WHY THIS ONE and THE
WINNERS filled (the winner read in `references/the-dig.md`, 3 sellers read whole, 1 block each).
THE PROBLEM, THE PROMISE, BUYER WORDS, WHAT HE GETS, THE BUILD and OBJECTIONS stay empty under their
headings until steps 3 to 5.

## 3. The dig

The Apify tools (`fetch-actor-details`, `call-actor`, `apify--web-fetch`) are not loaded: send 1 line and wait.
`The dig reads Reddit and YouTube comments through Apify. Paste: Here is my Apify token: ____. Use it for execution genesis offer.`
"Skip" means no dig: BUYER WORDS reads `None found. The dig was skipped.` and THE PROBLEM comes from
the sellers' pages.

Run part 2 of `references/the-dig.md` for the chosen offer only: its cost line, then Reddit, reviews
of what he pays for now, YouTube comments and public forums, until 10 quotes. Write BUYER WORDS to the
page the moment the dig ends. Fewer than 5 quotes: go on with the ones you have, and step 4's print
line says how many.

## 4. The page

Fill THE PROBLEM and THE PROMISE. Add the places the quotes came from to WHO line 2. When a quote
names the result the buyer wants, put it in THE SENTENCE. No result for THE SENTENCE or no day for
THE PROMISE: ask its 1 line from `references/the-page.md` and wait, both lines in 1 message when both
are missing. Then read the whole page against the law in `references/the-page.md` and fix every line
that breaks it.

Write the `product word` row in `.claude/squad-roots.md`: the noun of THE SENTENCE (`site`, `ads`,
`program`). Add the row when the table has none. Touch no other row.

## 5. The build

Fill the last 3 sections, in this order, by their rules in `references/the-page.md`:

1. **WHAT HE GETS.** The 3 winners' `Sells:` lines joined into 1 list, 5 to 12 lines, each ending on
   the winner that sells it, plus what answer 3 named. What 2 or 3 winners sell is always on it.
2. **THE BUILD.** 1 step per thing on that list, the tool named in each, the days adding up to THE
   PROMISE's day. The tools by THE SHAPE from the table in `references/the-page.md`, a tool the founder
   named in answer 3 first. Read each tool's pricing page today (`apify--web-fetch`, or WebFetch when
   the Apify tools are not loaded) and write the cheapest paid plan month to month, or `free plan`,
   with the link. Then the cost to deliver 1.
3. **OBJECTIONS.** 5 lines: the doubts in BUYER WORDS first, then the winners' FAQ questions, then the
   standing 5, each answered off this page in 1 line.

Read the whole page once more against the law and fix every line that breaks it. Then print this, and
nothing else of the page:

```text
Saved: squad/business.md
**<THE SENTENCE>**
<PRICE line 1>
<N> buyer quotes, from <where>. <K> of <M> sellers publish a price.
He gets <N> things. <N> steps to build it, <N> tools, $<n> a month in tools, live by day <N>.
Change any line by telling me what it should say. Next: /execution-genesis-demo.
```

`<where>` names the sites the quotes came from, in the dig's order: `Reddit`, `Capterra`,
`Trustpilot`, `the App Store`, `YouTube comments`, a forum's name. `3 buyer quotes, from Reddit and Capterra.`
With 1 quote the line reads `1 buyer quote, from <where>. <K> of <M> sellers publish a price.`
No quotes: the quotes line reads `0 buyer quotes in <every source the dig read>. <K> of <M> sellers publish a price.`
Skipped: `0 buyer quotes, the dig was skipped. <K> of <M> sellers publish a price.`

## Changing a line

The founder names a line and what it should say: rewrite that line only, under the page law. PRICE
line 1 stays in 1 of its 3 forms. THE PROMISE never promises a result. A BUYER WORDS line is removed, never reworded.
A new THE SENTENCE writes the `product word` row again. A line added to or removed from WHAT HE GETS
adds or removes the step in THE BUILD that makes it, and the cost line is worked again. A new PRICE
or a new THE PROMISE day rewrites the OBJECTIONS lines that rest on them. Print the new line, then
`Change any line by telling me what it should say. Next: /execution-genesis-demo.`

## The wiring

On "Here is my Apify token: ____. Use it for execution genesis offer.":

1. Write `.mcp.json` in the folder Claude Code is open in, from `mcp.json.example` next to this
   file, with the token in place of `PASTE_YOUR_APIFY_TOKEN`. An existing `.mcp.json` gets the
   `apify` block added under `mcpServers`, and nothing else in it changes. Use the file tool, never
   a shell command that prints the token.
2. The folder is a git repo: add `.mcp.json` to `.gitignore`.
3. The same message carries the 5 answers: run step 2 and write the page first.
4. `npx -v` fails: send `Install Node from nodejs.org first (the LTS download).` before the last line.
5. Send 1 line and stop:
   `Quit Claude Code, open it again in this folder, choose to use the apify server when it asks, then say hi.`
   When you wrote the page first (3 above), the line ends `then type /execution-genesis-offer.` instead.

Never print the token back. Never ask the founder to open or edit a file.

## Never

- Send, post or book anything.
- Invent a quote, a number, a seller or a need. A line with no answer and no receipt under it stays off the page.
- Paraphrase a quote.
- A range, or 2 prices for the same term, anywhere but WHAT HE PAYS NOW and the Price column of the sellers table.
- A guarantee, or a promise of money the buyer will make.
- A menu of options. 1 page, 1 offer.
- Print the whole page into chat, or the token anywhere.
- A tool price from memory, a deliverable no winner sells and the founder did not name, or an
  objection answered with a fact this page does not hold.
