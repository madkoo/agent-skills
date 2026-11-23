---
name: prompt-formalizer
description: Turns rough, casual, or half-formed text into a clean structured prompt with four sections (Context, Task, Constraints, Expected output). Use this whenever the user pastes or types a raw request and asks to formalize, structure, format, clean up, rewrite, or improve it as a prompt, or says things like "turn this into a proper prompt", "make this prompt better", "structure this for an LLM", or "/prompt". Also use it when the user hands over a messy brain dump and wants something they can paste into Claude or another model, even if they never say the word "structured".
---
 
# Prompt Formalizer
 
Take whatever the user wrote and rewrite it as a structured prompt with four sections:
 
1. Context
2. Task
3. Constraints
4. Expected output
The goal is a prompt that someone (or some model) with zero background could read once and act on correctly. Rough input usually has the right intent but leaves out the background, the limits, or what a good answer looks like. Your job is to pull those apart, put each in its place, and flag what's missing.
 
## Workflow
 
1. **Read the input for intent.** Work out what the user wants done, for whom, and why. If the text is a draft prompt, keep its goal. If it's a loose description of a problem, infer the request behind it.
2. **Sort every piece of information into a section.** Use the section guide below. Nothing the user said should get dropped, and nothing should be added that they didn't say or clearly imply.
3. **Fill gaps carefully.** If a section has nothing to go on, don't make up details. Either write a sensible, clearly marked default (for example "Format: not specified, so a short written answer is assumed") or leave a bracketed placeholder like `[add: target runtime version]` for the user to fill in.
4. **Ask a question only when the task is truly unclear.** If you can produce a usable prompt with marked assumptions, do that and let the user correct it. One short question at most, and only when guessing would send the prompt in the wrong direction.
5. **Return the result** in the output format below.
## Section guide
 
**Context**: Background the reader needs before the task makes sense. Who the user is or what role they're in, the system or project involved, the current state, what has been tried, and the reason the task matters. Keep concrete names, versions, and tools exactly as the user wrote them.
 
**Task**: What to do, stated as a direct instruction in the imperative. One primary task per prompt. If the input holds several, list them as numbered steps in the order they should happen, or note that they should be split.
 
**Constraints**: Everything that limits or shapes the answer. Scope, things to avoid, tools or technologies to use or exclude, tone, length, audience, deadlines, style rules, and assumptions the reader should not question. Write each as a separate short line so none gets lost.
 
**Expected output**: What the finished answer should look like. Format (prose, table, code, steps), structure, length, level of detail, and how to handle uncertainty. If the user gave no format, pick the one that fits the task and say so.
 
## Output format
 
Present the structured prompt inside a single code block so it copies cleanly, using this layout:
 
```
## Context
...
 
## Task
...
 
## Constraints
- ...
- ...
 
## Expected output
...
```
 
After the code block, add a short note only if it helps, covering:
- Assumptions you made, in one line each
- Placeholders the user still needs to fill in
- Anything from the original you deliberately left out and why
If there's nothing to flag, skip the note entirely. Don't pad it.
 
## Writing rules
 
- Keep the user's voice and vocabulary where it's clear. Formalizing means tightening and organizing, not swapping in corporate wording.
- Prefer plain, direct sentences. Cut filler like "I was wondering if you could" and "please make sure to".
- Don't add generic instructions the user didn't ask for ("be thorough", "think step by step", "act as a world-class expert"). Add a role line only if the user gave one or the task clearly depends on it.
- Keep it as short as the content allows. A simple request gets a short prompt. Don't stretch a one-line ask into a page.
- If the input is already well structured, say so, make only the edits that help, and avoid rewriting for the sake of it.
- Preserve code, commands, error messages, and quoted text verbatim.
## Examples
 
**Example 1**
 
Input:
> need help writing a powershell script that finds all repos in our github org that haven't had a commit in a year, we use GHEC, output should be csv
 
Output:
```
## Context
I manage a GitHub Enterprise Cloud (GHEC) organization and need to find repositories that are no longer active.
 
## Task
Write a PowerShell script that lists every repository in the organization with no commits in the last 12 months.
 
## Constraints
- Target platform: GitHub Enterprise Cloud
- Language: PowerShell
- Inactive means no commits in the past 12 months
- [add: authentication method, e.g. PAT or GitHub CLI]
 
## Expected output
A complete, runnable script that writes the results to a CSV file. Include the repository name, URL, and date of the last commit as columns. Add brief comments for any non-obvious steps.
```
Assumptions: "Organization" is taken to mean a single org, and authentication is left for the user to specify.
 
**Example 2**
 
Input:
> explain kubernetes to my manager, he's not technical, keep it short
 
Output:
```
## Context
My manager has no technical background and needs a basic understanding of Kubernetes.
 
## Task
Explain what Kubernetes is and why teams use it.
 
## Constraints
- Audience is non-technical, so avoid jargon or define any term you use
- Keep it short
 
## Expected output
A plain-language explanation of about 150 words, with one everyday analogy.
```
Assumptions: "Short" is read as roughly 150 words.
 
