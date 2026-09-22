# The dig

2 parts, in this order. Part 1 costs under $0.10 and runs first, so a buyer who pays nobody costs no
digging. Part 2 runs for the chosen offer only.

## Part 1 · Who already sells to him

Tools: WebSearch to find sellers, `apify--web-fetch` to read each one's own page, and WebFetch only when the Apify tools are not loaded.

**Which ideas.** The idea in answer 1, and the idea in answer 5 when there is one. Answer 1 is
"nothing yet": the sellers to the buyer in answer 2, or in the answer to the extra question.

**Finding sellers, up to 10 per idea.**

1. Search the way the buyer would shop: `<what is sold> for <buyer>`, `<what is sold> for <buyer> pricing`,
   `<buyer> <what is sold> cost`. Add 1 or 2 searches in the words the first sellers use.
2. A seller is 1 business or 1 person with its own page, selling this to this buyer. A directory,
   a "top 10" article or a marketplace category page is not a seller. Open the sellers it names.
   A general tool counts only when its price page names this buyer.
3. Open the seller's page from the search result and take what this prompt names, word for word.
   The Apify tools are loaded: fetch the page with `apify--web-fetch`, `formats` `markdown` (about
   $0.0015 a page), and read every plan and its price off the row's `markdown`. Only when they are not
   loaded: WebFetch with this prompt. No price on the page and a Pricing or Plans link named: open that
   link the same way. Never guess a URL.
   `Quote word for word: the name this business sells under, who this is for, what the buyer gets, every plan with its price, term and billing note, any delivery time, every sentence that names the buyer's problem, and the link to the pricing page. Then the page's headings in order from top to bottom, every deliverable the plan lists, every proof element (a review count, a rating, years, client names, logos, a guarantee), what the plan leaves out, and every question in its FAQ.`
   With `apify--web-fetch`, the headings are the `#` lines of the `markdown`, in order, nav and footer
   left out. Keep the whole read of every seller for this run: THE WINNERS is written from it.
   The page comes back with no body text (a title only, as on Gumroad): fetch it once with
   `apify--web-fetch`, `formats` `raw`, and read the plan price and its term from the page's own data
   (`"offers"`, `"price"`, `"recurrence"`). Still no price, or the Apify tools are not loaded: the
   Price cell reads `page did not load`, and that seller does not count among the sellers read.
4. Stop at 10 sellers, or when 3 searches in a row add nobody new. Read answer 1's idea first. When it
   has 6 or more sellers with a published price, answer 5's idea cannot win: stop answer 5's at 5
   sellers read, and WHY THIS ONE names the 2 times it needed.

**A published price** is a number on the seller's own page, with its term. "From $1,500" counts, as
$1,500. A price in an article (the seller's own blog included, unless it names its own plan), a
directory or a search result is not published. "Book a call", "get
a quote" or no number at all is `not published`. A $0 plan is not a published price.

**The sellers table.** 1 row per seller of the chosen offer, published prices first.

| Seller | What they sell | Price | Link |
|---|---|---|---|
| the name the page sells under | what the buyer gets, plus the delivery time of the plan in the Price cell when the page states one (12 words or fewer, the delivery time included; count them) | the cheapest paid plan open to this buyer on each term the page offers, in these words and no others: `$<N> a month`, `$<N> a year`, `$<N> one-time`, `$<N> setup + $<N> a month`, `$<N> to $<N> a month`, with `(billed yearly)` only when the page bills that plan only yearly, then `+N more plans` when there are more: `$199 a month, +2 more plans`, `$299 a month (billed yearly)`, `$500 setup + $199 a month`, `$2,000 one-time`, `not published`, `page did not load`. 1 plan prints once. A free plan or free tier is never the cheapest paid plan. A price in another currency prints with the page's own symbol (`A$250 a month`). It counts among the sellers that publish a price and stays out of the range in WHAT HE PAYS NOW. A page that prints 2 numbers for the same fee: use the one in its pricing block. A Monthly/Yearly toggle whose monthly price is missing from the page as read: run 1 `apify--web-fetch` with `formats` `html` and read it there; if it is still missing, print the price as shown with `(billed yearly)` | the page the price was read on, as `[domain](url)`: the link text is the domain alone (`[agentzap.ai](<the page link>)`), never the whole URL |

**The pick,** silent. Count the sellers with a published price for each idea.

1. None across every idea read, and no number in answer 3: PRICE has no source. Send this 1 line and
   wait for a price or a different buyer.
   ```text
   I looked for people selling <idea> to <buyer> in <N> searches and on <M> sellers' own pages, and none of them publish a price. Tell me your price, or who else could buy it.
   ```
2. Answer 1's idea has sellers with a published price, or answer 3 gives a number: the offer is
   answer 1's idea. Answer 5's idea wins only with at least 2 times as many, and WHY THIS ONE gives
   both counts.
3. Answer 1's idea has none and answer 5's has some, or answer 1 is "nothing yet" and there is an
   answer 5: the offer is answer 5's idea.
4. Answer 1 is "nothing yet" and there is no answer 5: the offer is what most of the sellers to that
   buyer sell.


**The winner read.** THE WINNERS on the page holds 3 sellers, read whole on the same fetch as the
price: the headings in order, every deliverable the plan lists, every proof element, what the plan
leaves out, the term, and every question in its FAQ. Which 3: sellers with a published price first,
then the most proof elements, then table order. A seller whose price page and home page differ: the
price page gives the plan and its deliverables, the home page gives the headings and the proof, so
both are fetched (about $0.003 for the pair). A page already fetched is never fetched again for the
same fields. The FAQ questions go to OBJECTIONS. The shape of each block: `references/the-page.md`,
THE WINNERS.

## Part 2 · The dig

**Where.** Where the buyer talks, never where the people who sell to him talk. Websites for dentists:
r/Dentistry, not r/web_design. Coaching for real-estate agents: r/realtors, not r/coaching.

**What.** 5 to 10 quotes: what he complains about and what he already pays for, about the problem
THE SENTENCE fixes, in his own words.

**Order.** Reddit, then reviews of what he pays for now, then the comments under YouTube videos made
for him, then public forums. Stop reading when 10 quotes are in hand. 1 source at a time: start the
next source's run only after the rows of the one before it are read.

**The cost line.** Before the first call, send 1 line and go on without waiting:
`Digging now: Reddit, reviews, YouTube comments and forums, on your Apify account, $3 at most.`
The caps below keep the whole dig near $2.75 at Apify's free-plan prices. Never raise a cap.

**Apify.** Every call runs on the founder's Apify account. Before calling an actor, read its live
input schema with `fetch-actor-details`. The live schema wins over the fields below, which are how
they read when this agent was written. A charge cap, when you set one, is $0.50 or more: Apify refuses
a lower one before the run starts. A run that errors: say so in 1 line and go to the next source.
Never start the same run again. A tool that hands back a run instead of its rows: wait on it with
`get-actor-run`, then read the rows with `get-dataset-items`.

### 1. Reddit · `apify/google-search-scraper`, then `trudax/reddit-scraper-lite`

1. **Find the threads.** WebSearch returns no reddit.com page, so the search runs through Google on
   Apify. 1 run: `queries` 6 lines in 1 string, 1 search a line, `maxPagesPerQuery` 1,
   `saveHtmlToKeyValueStore` false. About $0.005 a line.
   - 4 lines for Reddit, each `site:reddit.com` plus 3 to 6 words: his trade and the problem the way
     he says it. 3 about what goes wrong, 1 about what he pays for now
     (`site:reddit.com dental practice owner missed calls`,
     `site:reddit.com dental office answering service worth it`). A longer line comes back empty.
   - 2 lines for the YouTube comments below, each `site:youtube.com` plus his trade and running his
     business, not the problem (`site:youtube.com dental practice owner`), because a search for the
     problem returns the sellers' own videos.
2. **Pick the threads.** Read the rows with `get-dataset-items`, `fields` `searchQuery,organicResults`.
   Each result carries `url`, `title`, `websiteTitle` (`Reddit · r/Dentists`, `YouTube · <channel>`)
   and `displayedUrl` (`30+ comments · 7 months ago`). The `description` is a search snippet, never a
   quote. Keep up to 10 threads, most comments first: the link holds `/comments/`, the subreddit is
   for his trade or the managers who run it, the thread is under 3 years old with 5 or more comments,
   and the buyer posted it or it asks the buyer a question (the owners answer in the comments). Never
   a thread that sells or announces a build (`I built`, `we help`), and never a subreddit for builders
   or sellers (r/AI_Agents, r/SaaS). Fewer than 4 kept: 1 more run with 4 new Reddit lines in other
   words, then go on with what is kept. None: Reddit is done.
3. **Pull the threads.** 1 run: `startUrls` the threads, each as `{ "url": "<thread link>" }`,
   `skipComments` false, `maxComments` 40, `maxItems` 41 times the number of threads, `skipCommunity`
   true, `skipUserPosts` true, `includeNSFW` false, and `memory` 1024 in the call options (the start
   fee is charged per GB). About $0.004 a row.
4. **Read every row.** `get-dataset-items`, `fields` `dataType,username,createdAt,url,title,body`,
   `limit` the run's item count. Each row is the post or 1 comment, word for word, with its own link
   and date, so a line copied from it was read on its source. Read every comment, not only the post.
   The body prints `&#39;`, `&quot;` and `&amp;` for `'`, `"` and `&`: copy the character. The
   `submitted by /u/...` tail of a post is not his words. A row from a moderator, AutoModerator,
   `[deleted]` or a seller pointing at his own product is not a quote.
5. **Thin: 1 more pass.** Every row read and fewer than 5 quotes: run Google once more, with 4 new
   Reddit lines and no YouTube line, built from the words the owners in the rows used
   (`site:reddit.com dental calls go to voicemail`,
   `site:reddit.com dental phones ringing nobody answers`), and `maxPagesPerQuery` 2. Keep up to 10
   threads not read yet, by step 2's rules for a thread, pull them with step 3's settings and read
   every row by step 4. The 2 pulls together save no more than 500 rows: this run's `maxItems` is 41
   times its threads, or 500 less the rows the first pull saved when that is less. Never run this
   pass again.

### 2. Reviews of what he pays for now · apify web-fetch

1. Up to 3 tools: the ones the Reddit rows name as what he uses or pays for now, then the sellers in
   the table.
2. WebSearch `<tool> reviews` with `allowed_domains` `capterra.com` and `trustpilot.com`, and
   `apps.apple.com` for an app. Capterra first: it prints each reviewer's role.
3. Fetch each review page with `apify--web-fetch`, `formats` `markdown`, and read `markdown` off its
   row. Up to 2 pages a tool (Capterra's second page is `?page=2`), 6 pages in all. About $0.002 a page.
4. A review is his when its role line (`Dentist, President`) or its own words (`my practice`,
   `my clients`) say the writer is the buyer in WHO line 1. A complaint about what the tool costs,
   misses or breaks is a complaint about the problem. A thank-you to the support team is not.
5. A page that comes back blocked, empty or with no review text: skip it.

### 3. YouTube comments · `streamers/youtube-comments-scraper`

1. Up to 5 videos from the 2 YouTube lines of the Reddit search: made for the buyer in WHO line 1,
   never for his staff (a video that trains his receptionist draws receptionists), never by a seller
   of this offer or reviewing one.
2. 1 run: `startUrls` the videos, each as `{ "url": "<video link>" }`, `maxComments` 50 (per video),
   `sortCommentsBy` `TOP_COMMENTS`. There is no minimum number of comments: a video with few costs
   less. About $0.002 a comment.
3. Each row carries `comment`, `author`, `cid`, `publishedTimeText`, `authorIsChannelOwner` and
   `pageUrl`. A comment by the channel owner, or one that thanks or praises the creator, is a fan and
   not a quote. A quote's link is `pageUrl` plus `&lc=<cid>`, and its channel is the one the search
   showed for that video.

### 4. Public forums · `apify/google-search-scraper`, then apify web-fetch

1. WebSearch `<his trade> forum` to find his trade's own forum. A seller's blog, a Substack, a
   Gumroad page or a Facebook post is not a forum. Find its threads with 1 Google run: `queries` 2
   lines, each `site:<forum domain>` plus 3 to 6 words of the problem, `maxPagesPerQuery` 1,
   `saveHtmlToKeyValueStore` false. About $0.01. Read the rows with `get-dataset-items`, `fields`
   `searchQuery,organicResults`, and keep the links to threads on its message board, never its blog,
   a magazine or a PDF.
2. Fetch up to 5 threads with `apify--web-fetch`, `formats` `markdown`. About $0.002 a thread.
3. A thread behind a login, blocked, empty or gone: skip it.

## What counts as a quote

All 6, or it is not a quote.

1. The buyer said it: the buyer in WHO line 1 (for a business, its owner or the manager who runs it),
   talking about that business or his own life, and his own words or his review's role line show it.
   Not a seller, not someone like the founder, not a moderator, a bot, a fan or an ad. His words show
   it with I or my about running the business (`I bought the practice`, `my front office`, `I scrapped
   it`); `we` alone does not. Trying a seller's product (`I tried it myself`,
   `it wouldn't let me connect with the doctor`) does not show he runs the business. Staff and sellers
   test tools too. A person who offers the reader help, a DM or a free tool is a seller, and none of
   his lines count. A person who wants to become the buyer (`want to become an online coach`) is not
   the buyer yet.
2. It is a complaint or a want about the problem THE SENTENCE fixes: what goes wrong, what it costs
   him, what he tried, what he pays for now and what goes wrong with it, what he wishes he had. For an
   offer that answers missed calls, a line about calls that ring out counts, and a line about a busy
   front desk or insurance work does not. A line saying the problem never bothered him is not a
   complaint. A problem he says he already beat (`when I first started`, `now I run my channel`) is not
   a complaint, and a cut never hides that he beat it. A reason about freeing staff time (`frees up
   time in my front office`) is the busy front desk and does not count.
3. It was read on its source: an actor's row, or a page fetched word for word with `apify--web-fetch`.
   A search snippet, a WebFetch answer, an AI summary or a line inside an article is not a quote.
4. It is verbatim: copied character for character, typos and slang kept, in the language it was said
   in. Cut it down to the 1 or 2 sentences that carry the point, and mark a cut inside it with `...`.
   Never add a word, swap a word or fix the grammar. Read the whole row before cutting. A cut never
   drops words that turn the point around: `This never concerned me bc ...` cut to `...every patient ...`
   is a changed quote.
5. It carries where, the link and the date. No link, no quote.
6. 1 quote per person.

## Writing BUYER WORDS

- Up to 10 lines. Complaints first, then wants. In each group, the most specific line first (a number,
  a named tool, a named moment), then the most upvoted.
- Each line: `1. "<verbatim>" · <where> · <link> · <date>`.
- `<where>`: `r/<subreddit>`, `<site> review of <tool>` (`Capterra review of Weave`),
  `YouTube comment, <channel>`, or the forum's name.
- `<date>`: the day it was posted, `YYYY-MM-DD`, when the row or the page gives it. Only an age given
  ("3 weeks ago"): that age, then `read YYYY-MM-DD`. No date at all: `read YYYY-MM-DD`.
- Fewer than 5 after all 4 sources: the page carries the ones found, and no line is added to make up
  the count.
- No quote found at all: 1 line, `None found in <N> threads on <the subreddits read>, the reviews of <the tools read>, the comments on <N> YouTube videos (<channels>) and <the forums read>.`
  A source with nothing to read is named as such: `no Reddit thread for his trade`, `no review page`,
  `no YouTube video for him`, `no public forum thread`. Video titles stay off the page. Skipped:
  `None found. The dig was skipped.`
- Write BUYER WORDS to the page the moment the dig ends. Those lines are the dig's receipts, and the
  dig does not run again for this buyer.
