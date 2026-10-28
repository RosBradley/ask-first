---
name: ask-first
description: "Asks the user questions before starting a task: one question at a time, each with a few answers (the AI's recommendation first and labeled) and a free-form answer last, then a summary of the decisions to confirm before the work begins. Use when the user's message contains the command .ask or the words ask first used as an instruction to the AI, anywhere in the message, in any case: at the start (ask first: plan our launch), at the end (plan our launch. .ask) or alone (.ask, about the work already in this chat). Also when the user plainly asks the AI to interview them or ask them questions before starting. Not when ask first is about someone else, such as a rule for a colleague (new hires should ask first before deleting files)."
---

# Ask First

Version: 0.1.0

A short request leaves a lot unsaid, and the user often hasn't had time to think through what matters. This skill turns that around: before doing the task, ask the questions that would change the result, one at a time, each with a few ready answers to pick from. Your recommended answer is always first, so the user can move fast by taking it, and the last answer is always the user's own words.

## Commands

| Plain words | Dot style | What happens |
|---|---|---|
| `ask first` | `.ask` | Starts an interview about the task in the same message, or about the work already in this chat if there is none |

- The command can be anywhere in the message: `ask first: write a launch plan`, `Write a launch plan. .ask`, or `.ask` alone. Case doesn't matter, so `.Ask` and `Ask first` count.
- Everything else in the message is the task. Leave the command words out of it.
- `.ask` always carries the dot. `ask` alone is an ordinary word.
- `ask first` counts only when the user is telling you to ask before you start. "Write a rule for new hires: ask first before deleting files" is about someone else: help with it without this skill.

## Before the first question

1. Work out the task. It is the rest of the message; with no task in the message, it is the work in progress in this chat. With neither, the first question asks what the interview is about.
2. Learn what can be learned without asking. Read the files, earlier messages and sources the task points to. Never ask the user something you can look up.
3. List the decisions that would change the result, most important first. Keep the ones where the user's answer matters: goals, audience, scope, constraints, trade-offs, and things the user probably hasn't thought about. Drop anything with an obvious default; just use the default and say so in the summary.
4. Say in one line what the interview is about and roughly how long it is: `Interviewing you about the NERC CIP program: about 6 questions.`

## Asking

Ask one question per message, so each answer can shape the next question. Each question has:

- A number and the running estimate: `Q3 of ~6`. Update the estimate as answers open or close topics; it's an estimate, not a promise.
- The question in one sentence.
- 2 to 4 answers. Your recommendation is first and labeled `(Recommended)`. Each answer gets a short line on what it means or what it costs, so the choice can be made without more research.
- A free-form answer last, so the user can write in their own.

Answers are real alternatives, not one good choice with filler around it. When there is no clear best choice, still put first the one you would pick, and say why in its line.

### In Claude Code (the AskUserQuestion tool is available)

Use the AskUserQuestion tool. Put the recommended answer first with ` (Recommended)` at the end of its label. The tool adds the free-form answer (Other) on its own, so don't add one. Put the `Q3 of ~6` count in the header or the question.

Batch option: when the next 2 to 4 questions don't depend on each other's answers, ask them in one call. Ask a question on its own whenever its answer would change what comes next.

### Everywhere else (text)

Write the question as plain text, in this layout, with no bold or other formatting, so it reads the same in every app:

```text
Q3 of ~6: Who will run the NERC CIP program day to day?

A. An existing staff member, part time (Recommended) - fits a small district's budget
B. A new full-time compliance hire - steadier, but a new salary
C. An outside consultant - fast expertise, ongoing cost
D. Something else - write your own

Reply with a letter, rec, or your own words.
```

Letters, not numbers, so a letter is never mistaken for a number in an answer ("3 days"). One line per answer, so it fits a phone screen. The last letter is always `Something else - write your own`, and the last line is always the reply hint.

The user answers with a letter, with `rec` for the recommendation, or in their own words. Read an answer in their own words as it is meant; if it is unclear, ask about it once, briefly, then move on.

## Decision summary

When the decisions that matter are made, stop asking. Then:

1. Show the decisions as a short numbered list, one line each: the user's answers, and any defaults you chose without asking, marked `(default)`.
2. Ask a last question, in the same format: `Proceed (Recommended)`, `Change something`, and the free-form answer.
3. On `Proceed`, do the task, using every decision in the list. On a change, update the list, show it again, and ask again.

The interview is never the end in itself. Keep it to the questions that change the result.
