---
name: intentional-compacting
description: Intentionally compact the current coding agent session into a markdown file (progress.md) so a new session can pick up where this one stopped, with a clean context focused on the problem being solved. Use this whenever the user says compact, compaction, hand off, pass this to a new session, start fresh with context, write progress.md, or when a long session has gone in circles and the context is getting noisy, even if they don't use the word "compact".
---
 
# Intentional compacting
 
Long coding sessions fill up with dead ends, noisy tool output, and abandoned ideas. That clutter makes the agent worse over time. This skill writes down only what a fresh session needs, so the next one starts clean and knows exactly where to go.
 
Write everything we did so far to `progress.md` in the project root (or the path the user names). If a `progress.md` already exists, read it first and update it instead of overwriting, so earlier findings are not lost.
 
## What goes in progress.md
 
Cover these four things, in this order.
 
1. **Goal and approach.** What problem we are solving and the approach we settled on. One short paragraph. If we rejected other approaches, give each a line with the reason, so the next session doesn't retry them.
2. **Steps done so far.** What has actually been changed or verified, in order. Include things that were checked and found to be fine, because ruling something out is progress.
3. **Current failure.** The thing we are working on right now: the exact symptom, the error message or wrong behavior, how to reproduce it, and what we think is causing it. Say what has been tried and didn't work. If the cause is still unknown, say that plainly.
4. **Code references.** A list of `path/to/file.ext:line` entries with a few words on why each one matters. These let the next session open the right place immediately instead of searching again.
## How to write it
 
Trace flows, not history. When the problem spans several files, describe the path the code takes, step by step, with file and line for each step. Compare the working path to the broken one when there is one, since the difference usually points at the bug.
 
Keep it specific. Real file paths, line numbers, function names, commands, and error text are useful. Phrases like "fixed some issues in the handler" are not.
 
Leave out chat history, pleasantries, full file dumps, long logs, and anything that doesn't help the next session act. If a detail wouldn't change what the next agent does, cut it. Aim for something that can be read in a couple of minutes.
 
Don't invent anything. If a line number or result wasn't confirmed in this session, say it is unverified or leave it out.
 
## Template
 
```markdown
# Progress
 
## Goal
<what we are trying to do and why>
 
## Approach
<the approach we're taking>
Rejected: <alternative> because <reason>
 
## Steps done
1. <step and result>
2. <step and result>
 
## Current failure
<symptom, repro, suspected cause, what was already tried>
 
## Flow
### Working path
1. `file:line` does X
2. ...
### Broken path
1. `file:line` does Y
2. ...
 
## Code references
- `path/to/file.ext:line` - why it matters
 
## Next step
<the single most useful thing to do first in the new session>
```
 
Drop sections that don't apply. The Flow section only earns its place when there is a working path and a broken one to compare.
 
## Example
 
```markdown
## Current failure
Bash tool calls show a generic wrench icon in the message stream, but the
modal shows the terminal icon correctly.
 
## Flow
### Modal path (working)
1. `ToolResultModal.tsx:136` calls `getToolIcon(toolCall?.toolName)`
2. `getToolIcon()` returns `<Terminal />` for Bash
3. The terminal icon displays
 
### Message stream path (broken)
1. `ConversationContent.tsx:103` calls `eventToDisplayObject(event)`
2. A default `<Wrench />` is assigned at line 76
3. No Bash override exists in lines 189-228
4. The generic wrench icon displays
 
## Code references
- `eventToDisplayObject.tsx:76` - default wrench assignment
- `eventToDisplayObject.tsx:189-228` - tool-specific overrides (Bash missing)
- `eventToDisplayObject.tsx:657` - correct Bash to Terminal mapping
```
 
## After writing
 
Tell the user where the file is and suggest they start the new session by pointing the agent at `progress.md`. Don't paste the whole file back into the chat.
 
