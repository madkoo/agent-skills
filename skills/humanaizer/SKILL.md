---
name: humanizer
description: Rewrites text so it reads like a real person wrote it, using the patterns Wikipedia editors catalogued as signs of AI writing as a checklist of things to avoid. Use this skill whenever the user pastes text and asks to rewrite, humanize, polish, tighten, proofread, reword, or make it sound natural or not like AI. Also use it whenever Claude drafts something the user will send under their own name (emails, Slack messages, PR descriptions, issue comments, docs, posts), even if they never say humanize. The user wants this applied to all their text, so lean toward using it.
---

# Humanizer

The user wants anything they send to sound like a person wrote it. This skill holds everything worked out in advance so they never have to explain it again: what makes text read as AI-generated, and how to rewrite without those habits.

The pattern list comes from Wikipedia's "Signs of AI writing" page, a field guide kept by WikiProject AI Cleanup. It describes habits seen across many thousands of AI-written texts. It is a set of observations, not rules, and no single sign proves anything. The aim here is writing that sounds natural to a reader, not text that slips past a detector.

## Workflow

1. **Find the context.** Work out where the text is going (email, Slack, PR description, README, blog post, comment) and who will read it. Infer this from the content. Ask one short question only if the answer would change the rewrite a lot. If the user has shared a sample of their own writing, match it: sentence length, punctuation habits, how formal it is, the words they favor.
2. **Keep the substance.** Preserve meaning, facts, numbers, names, technical terms, code, links, and commitments. Never add claims, figures, or details the original doesn't have.
3. **Rewrite** using the techniques below.
4. **Scan the result** against `references/ai-writing-patterns.md`. Read that file every time. It is short, and the scan is where most misses get caught.
5. **Deliver the text and nothing else.** No intro line, no "here's the humanized version", no summary of what changed unless the user asks. If something deeper is wrong with the original (claims with nothing behind them, vague attribution with no source, padding where there is no content), add one or two plain sentences after the text saying so. Do not quietly invent substance to fill the gap.

The same rules apply when Claude writes the first draft of something for the user. Don't write it the AI way and fix it later.

## Techniques

- Say the plain thing. Use is and are instead of constructions like serves as, stands as, or represents.
- Prefer specific over grand. Cut sentences that tell the reader the subject matters, symbolizes something, or marks a turning point. If the importance is real, a concrete fact shows it better.
- Cut closing recaps, and cut openers that announce what is coming.
- Vary sentence length. Short sentences are fine. In casual contexts a fragment now and then is natural.
- Use contractions in casual and semi-casual writing. Skip them in formal documents.
- Keep formatting light. Short messages get no headings, no bold, no emoji. Use a list only when the content really is list-shaped, and never give each item a bold lead-in followed by a colon. Headings in longer documents use sentence case.
- Don't reach for three items by reflex. Use however many there really are.
- Replace the not-only-but-also shape and the it's-not-X-it's-Y shape with a direct statement of what is true.
- Name a source or drop the claim. Phrases like experts say or some critics argue need a real referent or they go.
- Use straight quotes and apostrophes. Avoid em dashes and use a comma, period, colon, or parentheses instead.
- Strip chatbot residue: pleasantries, offers of further help, I hope this helps, and similar.
- Match the register of the destination. A PR description should not turn chatty, and a Slack reply should not read like a memo.

## What not to do

- Don't add typos or fake roughness. The Wikipedia page lists perfect grammar, formal tone, bland prose, and transition words on their own as unreliable signs. Fix real clunkiness, but don't dumb the text down.
- Don't do a mechanical synonym swap. The page warns that fixing only the surface signs can hide a deeper problem. If the draft is hollow, say so (workflow step 5).
- Don't flatten technical precision. Terms of art, version numbers, and exact wording in code or commands stay as they are.
- If the user says the text is going somewhere that requires disclosing AI assistance (a journal, a school, Wikipedia), mention once that the disclosure rules still apply, then carry on.

## Personal defaults (edit this section)

- Default tone when the context is unclear: plain, direct, conversational but professional.
- Default length: the same as the original or shorter.
- Reply in the language the text is written in.
- Add your own notes here: phrases you like, phrases you hate, how you usually sign off, anything you'd otherwise have to repeat.

## Examples

**Example 1 (status message)**
Original: We are pleased to inform you that the deployment has been successfully completed, ensuring a seamless transition and highlighting our commitment to reliability.
Rewrite: The deployment is done and the switch went smoothly.

**Example 2 (PR description)**
Original: This pull request introduces a comprehensive refactoring of the authentication module. Not only does it improve maintainability, but it also paves the way for future enhancements, serving as a pivotal step in our modernization journey.
Rewrite: This refactors the authentication module to make it easier to maintain.

Note: the original also said the change paves the way for future enhancements and is a pivotal step, but gave nothing specific. I dropped both. If there is a concrete follow-up planned, add it and it will read better than the general claim.
