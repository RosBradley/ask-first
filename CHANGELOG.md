# Changelog

## 0.1.0 (in testing)

- First version. Type `ask first` or `.ask` anywhere in a message, and the AI asks one question at a time, with its recommended answer first and a free-form answer last, then shows a summary of the decisions to confirm before starting the task.
- The full skill (`skills/ask-first/SKILL.md`) installs in claude.ai, Claude Code (as a plugin), Gemini, ChatGPT Skills and GitHub Copilot. A short version (`prompts/ask-first.txt`, under 1,500 characters) is for ChatGPT's and Microsoft 365 Copilot's custom instructions, Meta AI's memory, and any other AI.
- 4 test cases in `evals/` for `claude plugin eval`, and a manual checklist in `docs/setup.md` for the other AIs.
