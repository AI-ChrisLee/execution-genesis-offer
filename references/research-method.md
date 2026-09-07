# Research method (the Winning Offer: LISTEN, then MAP)

Two passes, in this order. State the reason for each before running it.

## Which mode this run is in

Wired means the Apify tools are loaded in this session: the founder pasted the token (g5)
and reopened Claude Code. Nothing is probed. Not loaded: C1 says one sentence, "Reddit and
YouTube comments are out until a token is pasted; everything else is read", the mode line
prints `unwired ladder`, and the run walks the unwired ladder below. An auth error on the
first call is one line, and the run walks the unwired ladder from there. A founder who wants
it wired pastes their token ("Here is my Apify token: ____. Use it for the Winning Offer.")
and the skill writes the wiring itself, in a turn of its own; this run does not stop for it.

## Pass 1 · The buyer's own language

Reason to state: "Everything that sells must be written in your buyers' words, so first we
collect them."

### Wired, which is the real ladder

1. **Reddit first.** Find the 3-5 subreddits where this buyer asks questions (search
   "[their job/situation] reddit"). Mine the BUYER's rooms, never the founder's peers:
   for a wedding photographer that is r/weddingplanning, not r/WeddingPhotography. Pull
   the top and recent question posts plus their comment threads through the scraping
   tool. Read the actor's input schema before calling it.
2. **YouTube comments** under 3-5 channels they watch (from the founder's answers plus
   your own search), through the same scraping tool. Comments never ship inside the watch
   page: a raw fetch of a watch page returns the title, the view count and the
   description, and zero comment records. There is no keyless way to read them. Wired, or
   not at all.
3. **Anywhere else they gather**: forums, groups, review sites for what they already buy.

### Unwired, the ladder that actually opens

Every rung below was tested from Claude Code and returned real text. Reddit, Quora, Yelp,
G2 and Stack Exchange are NOT on it: they answer blocked or 403. Naming a closed door as a
source is how a run walks the ladder believing it already tried.

One rule before the rungs. A 403 from `curl` does not mean a source is closed. WebFetch
carries a different agent and often gets in where curl does not; Trustpilot is the proven
case, 403 to curl and full review text to WebFetch. **WebFetch is the test that counts.**

1. **Trustpilot review pages** for the companies this buyer already hires, at
   `trustpilot.com/review/<company domain>`. Yields pains and objections in full
   sentences, the closest thing to Reddit that opens. Does not yield anything about a
   niche where no company has a page.
2. **Capterra product review pages** (`capterra.com/p/<id>/<product>/reviews/`) when the
   buyer buys software. Yields pains and objections, verbatim, at volume. Does not yield
   price objections about services.
3. **Indie Hackers and Hacker News** for founder, builder and operator buyers. Yields
   pains and outcome words in the buyer's own voice. Does not yield consumer or local
   language.
4. **Buyer forums that open.** Search first for the thread, then fetch it:
   `boards.weddingbee.com/topic/<slug>` for weddings, `houzz.com/discussions/<topic>` for
   home projects. Yields real deliberation, which is where objections live. Does not
   yield volume; these rooms move slower than Reddit.
5. **News and industry pieces quoting real people** in this market, and competitors'
   testimonial pages (secondhand, and the document says so). Yields outcome words. Does not
   yield pains or objections: nobody writes a complaint into a testimonial.
6. **The founder's own inbox, DMs and call notes.** Yields all three, in this market
   exactly. This is a rung, not a rescue; see the standing rule below.

**Creator and agency buyers (YouTubers, course sellers, marketing leads, agency owners).**
Trustpilot has no page for the people who hire an editor, Capterra is software, Indie
Hackers is founders, and the wedding and home forums are the wrong market, so pass 1 comes
back empty on the rungs above. What does open: YouTube comments under the channels this
buyer watches (wired, rung 2 of the wired ladder, and the reason wiring matters most in
this market), and the public archives WebFetch reaches, a Discord or Skool community's
public channels, a newsletter's web archive, a podcast's show notes and its comment
section. Unwired, say it plainly: **this is a founder-ask market by default**, same as the
paragraph below; the inbox lines asked for at C1, with the yes, are that ask.

**Local-service buyers (engaged couples, homeowners, patients, local business owners).**
The review sites this file used to name are closed: Yelp and WeddingWire answer 403, The
Knot answers 403 and then times out. And open, they would still not do the job. A
five-star vendor review carries outcome words and nothing else, no pain and no objection,
because nobody writes a complaint under a photo of their wedding. So the rule for these
markets: **pains and objections come from the founder ask by default, not as a fallback.**
The inbox lines asked for at C1, with the yes, are that ask. What does open, and
what each one is for: a buyer forum for the occasion (rung 4), pains and objections;
Trustpilot pages for the marketplaces this buyer hires through, Thumbtack, Angi,
HomeAdvisor (rung 1), pains and objections about the hiring itself; the operators' own
sites and testimonial pages, outcome words only; news and industry pieces, outcome words
and some pain.

Collect, verbatim and with sources:

- **The pains**, in their exact words. Rank by engagement (likes, replies) when visible.
  These become the offer's fear list.
- **The outcome words**: what they call the result they want. These are the only words
  allowed on anything that sells.
- **The objection words**: what they say when they distrust a pitch in this market. The
  offer must answer these before they are voiced.

Rules for this pass, learned the hard way:

- **When C0, question 5 surfaced a switching itch**, collect buyer language for that
  category too: same sources, same rules. The itch answer needs buyer pull, not just an
  operator table.
- **A search engine's summary is NOT a quote.** A quote only counts if you read it on the
  source page itself. Never paste a search result's paraphrase as "verbatim." When search
  only paraphrases, cite the page title plus the paraphrase, marked as a paraphrase.
- **A rung that returns ZERO results** (open, just nothing there) is said out loud and the
  ladder moves down. A niche with no public trace is a note on the document, and fabricating
  quotes to fill the section is the worst failure this skill can commit.
- **The founder's own buyer language is asked for once, at C1 with the yes:** 5-10 real
  lines from their inbox, DMs or group, "skip if you have none". This pass never stops to
  ask again. A public quote is one whose source label is neither a warm call nor the
  founder, so the lines that ask returns are founder-sourced: they are real buyer language,
  they go into `## BUYER LANGUAGE` labeled `(founder's inbox ...)`, and they never move the
  count, because the count measures the PUBLIC record and nothing else. The founder always
  has buyer language; the internet sometimes does not. A login-gated buyer room (private
  Facebook groups, member forums) is one case of this, and those lines cover it. Never
  invent a community. Under five public quotes, the document's mode line says `thin` instead
  of building a confident pain list on air. That flag never touches THE STACK's fear column,
  which runs on the source ladder in `card-template.md`.
- Never invent a quote; keep the source next to every quote. If real buyer language truly
  cannot be found anywhere, say so plainly; a buyer who talks nowhere is itself a market
  warning.

## Pass 2 · The market read

Reason to state: "Whether this niche holds is a data question, and today the data is what
the market already shows."

Three questions, real numbers only; drop anything you cannot verify. Run this pass on Apify
when it is wired (operator pages and pricing); the built-in search is the fallback, under the
same honesty rules as Pass 1.

1. **Who sells to this buyer now?** First name the market's edge: a local business
   competes in its city or metro; everyone else, name the comparable market before
   searching. Then find the operators: ten is a floor, not a ceiling; list every real one
   found while it stays useful. For each, five columns: what they sell, the price,
   published price or call-closed, how they get found, and **the bundle**: exactly what
   the buyer receives (software? curriculum? live calls? community? human labor?), the
   one-time vs recurring split, and what the recurring fee buys. The bundle column is
   what the model decision (the scorecard reference) gets built from. Operators' own
   pricing pages open reliably; read the price there rather than from a directory.
   Stopping rule, which applies only AFTER the ten-operator floor is met: past ten, stop
   adding operators once three consecutive new ones repeat a bundle pattern already in
   the table. Below ten, keep hunting even when the bundles repeat, until the search
   vocabulary is spent (every term the buyer would use, every neighbouring market named in
   the answers). Spent vocabulary and still under ten is the exhaustion case, not a stall:
   stop, write the real count in the file, and carry it into gate 1 (how findable this
   market is) and gate 4 (whether anyone is selling) as a finding. One check: if a "top
   firms" list was written by a firm on that list, confirm it against a source that was
   not.
2. **Growing or decaying?** Read demand direction from whatever signal this market emits.
   Where the niche is a content market, that signal is recent breakout content: views
   against the channel's own median of its last 10-20 uploads, the candidate video
   excluded, comparable long-form only, bought reach excluded, never views against
   subscriber count. **That window is the definition of record for the whole system.**
   Later skills re-verify these numbers; they never recompute them on a different window.
   Write the per-channel medians under `## CHANNEL BASELINES`.
   For local or service markets, make the same call from three reachable readings, each
   named in the file with its link: (a) the operator count, from searching the service
   against the market edge named in question 1 (a city for a local business, the
   comparable market for a remote one) and counting the distinct real businesses in the
   results, never a directory's own count, since The Knot and WeddingWire answer 403 and
   cannot be counted;
   (b) the market's published direction, from industry reports and news for this service
   dated inside the last year; (c) seasonality, read from the founder's own booking
   calendar, never from the web. Everywhere, count the new entrants of the last year
   (operators whose first dated work or reviews fall inside it).
3. **Where is the empty seat?** The combination nobody occupies: a price point, a delivery
   model, a buyer segment, a promise. Two seats always get tested: (a) the founder's
   switching itch from C0, question 5 (is that category actually open, or already a
   price war?), and (b) the transparency seat (when most operators hide their price behind
   a call, a published price IS an empty seat, and their opacity is the evidence). "No
   competition at all" is a warning, not a win: competitors selling is proof the money
   exists.

## Output: the headings, by exact string

One research note at `squad/offer-research.md`, written on a cold run only, readable in five
minutes. Every heading below is written by exact string, every cold run, and two of them are
load-bearing outside this run: `## BUYER LANGUAGE` (compiled from `squad/clients/*/notes.md`
at C0, nobody else writes it, the Winning Scrape reads it) and `## CHANNEL BASELINES` (the Winning Scrape starts its medians from it). A drifted
string there is a section that is gone. `## CHANNELS MINED`, `## DIRECTION` and
`## EMPTY SEATS` are named in prose by the Winning Scrape, so they keep their strings too.
The remaining four (`## ALLOWED WORDS`, `## OPERATORS`, `## SCORECARD`, `## ATTACK LOG`)
are this run's own receipts, read inside the run and by the founder afterward.

| Heading | Holds |
|---|---|
| `## BUYER LANGUAGE` | the verbatim pains, each with its source, ranked by engagement |
| `## ALLOWED WORDS` | the outcome words, then the objection words |
| `## CHANNELS MINED` | every source read, by name, and what each returned |
| `## CHANNEL BASELINES` | the per-channel medians |
| `## OPERATORS` | the operator table, bundle column included |
| `## DIRECTION` | growing or decaying, with its receipts |
| `## EMPTY SEATS` | the seat found, plus the two always tested |
| `## SCORECARD` | the seven gates with receipts (appended at SCORE), gate 7 carrying the number chain |
| `## ATTACK LOG` | the three self-attacks and the fix each forced (appended at ATTACK) |

`## CHANNEL BASELINES` is written every run, without exception. When the niche is not a
content market, write the heading followed by "(none: <the market type this run actually
found, local-service or remote-service or whichever>; the Winning Scrape sets the content
lane cold)", so the next skill reads an intentional gap instead of a missing section.

Write Pass 1's findings to the file before Pass 2 starts, and Pass 2's before the model
check; the file is the resume point, not the chat.
