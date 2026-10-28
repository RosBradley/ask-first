# Ask First

Stop explaining everything up front to your AI. Type `.ask` and Claude, ChatGPT, Gemini, Copilot or Meta AI asks you the questions that matter, one at a time, with its recommended answer first and room for you to write your own.

## Why

A short request leaves a lot unsaid. Explaining it all up front takes time, and you won't think of everything: the audience, the edge case, the trade-off you didn't know you were making. The AI fills those gaps with guesses, and you find out when the result comes back wrong.

Ask First turns it around. You give the task in a line, and the AI works out which decisions would change the result and asks about them. Each question comes with ready answers, its recommendation first, so most of the time answering is one letter. When the answer you want isn't listed, you write your own.

## What it does

```text
You:  Help me set up a NERC CIP program for our small public power district. .ask

AI:   Interviewing you about the NERC CIP program: about 6 questions.

      Q1 of ~6: How are your BES Cyber Systems categorized under CIP-002?

      A. Low impact only (Recommended) - typical for a small district; mainly CIP-003
      B. Some medium impact - adds most of CIP-004 to CIP-013
      C. Not categorized yet - start with the CIP-002 assessment
      D. Something else - write your own

      Reply with a letter, rec, or your own words.

You:  a
```

1. **It looks things up first.** The AI reads what it can (the chat so far, files, sources) and never asks you something it could find out.
2. **It asks one question at a time.** Each answer can change the next question. A running count (`Q3 of ~6`) shows how far along you are.
3. **Its recommendation comes first.** Answer with a letter, `rec` for the recommendation, or your own words.
4. **It recaps before it starts.** When the decisions that matter are made, the AI lists them, one line each, including any defaults it chose without asking. You confirm or change them, and only then does it do the task.

Where the app can show them, the questions come as clickable choices: in Claude Code, claude.ai and (new in October 2026) ChatGPT. Elsewhere they come as the text above. In Claude Code, the AI can also group 2 to 4 questions that don't depend on each other into one step.

**Status:** v0.1.1, in testing.

## Commands

| Plain words | Dot style | What happens |
|---|---|---|
| `ask first` | `.ask` or `.askme` | Interviews you about the task in the same message, or about the work already in the chat if there is none |

- Put it anywhere in the message: `ask first: write a launch plan`, `Write a launch plan. .askme`, or `.ask` alone.
- Any case works, so `.Ask` from a phone counts.
- `.ask` and `.askme` need the dot. "ask" alone is an ordinary word.
- "Ask first" about someone else doesn't trigger it: "write a rule for new hires: ask first before deleting files" just gets you the rule.

## Install

Pick your AI. Step-by-step instructions, with what each app can and can't do, are in [docs/setup.md](docs/setup.md).

| AI | How | What you get |
|---|---|---|
| **Claude** (claude.ai, desktop, mobile) | Upload [ask-first.zip](https://github.com/RosBradley/ask-first/releases/latest/download/ask-first.zip) under **Customize > Skills** | The full skill |
| **Claude Code** | Install the plugin (below) | The full skill, with clickable choices |
| **Gemini** | Upload [SKILL.md](https://github.com/RosBradley/ask-first/releases/latest/download/SKILL.md) under **Customize > Skills** | The full skill |
| **ChatGPT** | Paste [the short version](prompts/ask-first.txt) into **Custom instructions** | The short version, in every chat |
| **Microsoft 365 Copilot** | Paste [the short version](prompts/ask-first.txt) into **Custom instructions** | The short version, in every chat |
| **GitHub Copilot** | Copy `skills/ask-first/` into `~/.copilot/skills/` | The full skill |
| **Meta AI** | Ask it to remember [the short version](prompts/ask-first.txt) | Best effort |
| **Any other AI** | Paste [the short version](prompts/ask-first.txt) as the first message of a chat | That chat only |

The full skill and the short version ask the same way. The full skill has more guidance on picking good questions. The short version fits in ChatGPT's smallest custom-instructions box (1,500 characters).

### Claude Code

Install it as a plugin, in one step:

```
/plugin install ask-first --marketplace RosBradley/ask-first
```

On Claude Code older than 2.1.275, use two steps instead:

```
/plugin marketplace add RosBradley/ask-first
/plugin install ask-first@ask-first
```

Then type `.ask`, `.askme` or `ask first` in any message, or run it directly with `/ask-first:ask-first`.

To install without the plugin system, copy `skills/ask-first/` to `~/.claude/skills/ask-first/` (all your projects) or `.claude/skills/ask-first/` (one repository).

If you sign in to Claude Code with your claude.ai account and the skill is turned on there too, Claude Code loads both. Keep one of them on, so you know which version answers.

### Building the files yourself

To build claude.ai's zip from source (for a version not yet released), zip the skill folder itself, so the archive's top level is `ask-first/`:

```bash
cd skills
zip -r ask-first.zip ask-first/
```

## Tests

[evals/](evals/) holds 5 test cases for `claude plugin eval`. Each one starts a fresh Claude Code session with the skill loaded, types one message, and checks what happens:
- `.ask` at the end of a task starts an interview.
- `ask first` at the start of a message starts an interview.
- `.ask` alone in a new chat asks what the interview is about.
- `.askme` at the end of a task starts an interview.
- "Ask first" in a rule for someone else does not trigger the skill.

To run them from the repo folder:

```
claude plugin eval . --allow-tools AskUserQuestion --ablation none
```

Each case runs 3 times. To run one case, add `--case ask-alone-asks-topic`.

The other AIs have no test runner, so [docs/setup.md](docs/setup.md) has a short manual checklist instead.

## Limits

- Clickable choices depend on the app. Claude Code and claude.ai show them, and ChatGPT can with its Intelligent UI (paid plans first). Gemini, Microsoft 365 Copilot and Meta AI show plain text, and you answer by typing a letter. See [docs/setup.md](docs/setup.md#clickable-choices-or-text) for each app.
- The AI decides which questions matter and how many to ask. The count (`Q3 of ~6`) is an estimate, and it can change as you answer.
- The short version (ChatGPT, Copilot, Meta AI) has less guidance than the full skill, so its questions may be less well chosen.
- Meta AI has no custom-instructions feature, only memory, so it may not always follow the instructions.
- The install steps for ChatGPT, Gemini, Copilot and Meta AI were checked against their help pages on October 27, 2026. These apps change often. See [docs/setup.md](docs/setup.md) for what was and wasn't confirmed.

## License

MIT. See [LICENSE](LICENSE).
