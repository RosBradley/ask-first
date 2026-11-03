# Changelog

## 1.0.0

First release. Type `.ask`, `.askme` or `ask first` anywhere in a message, before a task or in the middle of a long conversation, and the AI asks you one question at a time, with its recommended answer first and a free-form answer last, then shows a summary of the decisions to confirm before it goes on.

- **Claude:** `ask-first-for-claude.zip` for claude.ai, and a plugin for Claude Code.
- **ChatGPT:** `ask-first-for-chatgpt.zip`, uploaded under Customize > Plugins and started with `@ask-first`. Tested with clickable choices on the Plus plan.
- **Gemini:** `ask-first-for-gemini.zip`, uploaded under Customize > Skills and started with `@ask-first`.
- **GitHub Copilot:** the `skills/ask-first/` folder.
- **Microsoft 365 Copilot, Meta AI and any other AI:** the short version, `ask-first-for-other-ais.txt` (also in the repo as `prompts/ask-first.txt`).
- Questions come as clickable choices where the app can show them, and as lettered text everywhere else.
- 5 test cases in `evals/` for `claude plugin eval`, and a manual checklist in `docs/setup.md` for the other AIs.
