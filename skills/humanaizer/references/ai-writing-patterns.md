# AI writing patterns to avoid

Source: Wikipedia's "Signs of AI writing" page (WikiProject AI Cleanup), as read in November 2026. The live page could not be opened directly, so this list was built from excerpts of the page and a detailed write-up of it. Treat it as a close summary, not a complete copy. The page changes often and the tells shift as models change, so if the user pastes a newer version of the page, prefer that.

Contents
- Content
- Language and grammar
- Style and formatting
- Leftovers from the chat
- Markup and citations
- Edit summaries and comments
- Ineffective indicators
- Extra patterns from general knowledge
- Pre-send scan

## Content

- Inflating the importance of the subject: claims that minor details symbolize, represent, or contribute to some bigger theme.
- Constant reminders of legacy or cultural importance, which breaks neutral tone.
- Superficial analysis bolted onto facts, usually about significance, recognition, or impact.
- Vague attribution to unnamed experts or critics (some critics argue, experts say).
- Outline-style conclusions about challenges and future prospects.
- Advert-like or promotional language, and generic positive or exaggerated descriptors.
- Echoing wording from a guideline or brief back at the reader (the page's example is independent coverage).
- Recap phrases that open a closing summary, such as in summary or overall.
- Rigid, formulaic sections (a Challenges section followed by a Future Prospects section, whatever the topic).

## Language and grammar

- A high density of stock AI vocabulary. Words the page names include encompassing, valuable insight, and key turning point. Some wording is idiosyncratic to AI text and was rare before about 2024.
- Avoiding plain is and are in favor of longer constructions.
- Negative parallelisms: the not only X but also Y shape and its cousins.
- Overusing the rule of three.
- Avoiding syntactic constructions that are common and perfectly acceptable in human writing, in pursuit of a formal, neutral tone.
- A sudden jump in style or polish compared with the person's other writing. When rewriting, match how the user normally writes so the text doesn't read like someone else wrote it.

## Style and formatting

- Title case in headings. Use sentence case.
- Too much boldface.
- Vertical lists where each item starts with a bold header and a colon.
- Emoji used as formatting, in headings or list items.
- Odd tables and heading errors.
- Curly quotation marks and apostrophes. The page says these prove nothing alone (some models produce them, some don't), but straight quotes cost nothing.
- Em dashes. The page now files these under historical indicators, since newer chatbots use fewer. Avoid them anyway and use commas, periods, colons, or parentheses.

## Leftovers from the chat

- Collaborative asides, placeholder text, and disclaimers about how sources should be used.
- Prompts, cheery sycophantic replies, and offers of further help left in the text.
- Knowledge-cutoff disclaimers and prompt refusals (as an AI language model and similar).
- Fill-in-the-blank templates left unedited.

## Markup and citations

- Markdown pasted into a place that doesn't render it: asterisks for bold, number signs for headings, triple-dash dividers, Markdown-style links, code fences. This one depends on the destination. GitHub, Slack, and many chat tools render Markdown, so leave it where it renders and strip it where it doesn't (email, plain-text fields, Word, most CMS fields).
- Internal formatting metadata leaking into the output.
- Chatbot citation artifacts, broken links, invalid DOIs and ISBNs, and book citations with no page numbers. Never invent a citation, link, or reference.

## Edit summaries and comments

The page has a section on signs specific to edit summaries and talk-page comments. The details were not available when this file was written. As a general rule, commit messages, PR comments, and review comments should be short, plain, and specific to the change, with no pleasantries and no recap of what the diff already shows.

## Ineffective indicators

The page names these as things that do not reliably point to AI, so don't strip or distort them:

- Perfect grammar
- Bland or robotic prose (on its own)
- Formal or academic prose
- Transition words in isolation

A related caution from the page: people who aren't native English speakers may avoid repeating words, which can look like a listed sign. Don't treat plain careful wording as suspect.

## Extra patterns from general knowledge

These did not come from the Wikipedia page and were not verified against it. They are widely noted habits, so avoid them, but treat them as a second tier.

- Stock words and phrases: delve, tapestry, testament, pivotal, landscape (used figuratively), underscore, showcase, vibrant, crucial, foster, intricate, robust, seamless, leverage, realm, navigate (used figuratively).
- Filler framing: it's important to note, it's worth noting, in today's fast-paced world.
- Assistant openers and closers: Certainly, Great question, I hope this helps, let me know if you'd like me to expand.

## Pre-send scan

Run this against the rewrite before delivering it.

1. Any sentence that says the subject is important, pivotal, or a milestone? Cut or replace it with a fact.
2. Any not-only-but-also or it's-not-X-it's-Y? Rewrite it as a direct statement.
3. Any group of three that is really only two things plus padding?
4. Any em dash, curly quote, emoji, bold lead-in, or title case heading?
5. Any closing recap or offer of more help?
6. Any vague attribution with no source?
7. Does it still say exactly what the original said, with no new facts?
8. Does it sound like the user, in the register the destination calls for?