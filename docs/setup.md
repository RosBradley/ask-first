# Setting up Ask First in each AI

The command is the same everywhere: type `.ask` (or `ask first`) anywhere in a message. What changes from app to app is how you install it, and whether you get the full skill or the short version.

- **The full skill** is [skills/ask-first/SKILL.md](../skills/ask-first/SKILL.md). Claude, Gemini, ChatGPT (on some plans) and GitHub Copilot all load skills in this same `SKILL.md` format.
- **The short version** is [prompts/ask-first.txt](../prompts/ask-first.txt), about 1,200 characters, for apps that only take pasted instructions. It asks the same way, with less guidance on picking good questions.

Everything below was checked against each company's help pages on October 27, 2026. Steps marked *(unconfirmed)* come from secondary sources, or from pages that couldn't be read directly. If a step doesn't match what you see, please [open an issue](https://github.com/RosBradley/ask-first/issues).

## Claude

### claude.ai (web, desktop app and mobile)

1. Download [ask-first.zip](https://github.com/RosBradley/ask-first/releases/latest/download/ask-first.zip) from the [latest release](https://github.com/RosBradley/ask-first/releases/latest). Keep it zipped.
2. Upload it and turn it on under **Customize > Skills**.
3. In a new chat, type: `Plan a weekend trip to Chicago. .ask`

### Claude Code

See [Claude Code in the README](../README.md#claude-code). In Claude Code, the questions come as clickable choices instead of text.

## Gemini

Gemini's Skills take the same `SKILL.md` file. Skills replace Gems: for personal accounts, Gems become read-only on November 17, 2026, so don't build this as a Gem.

1. Download [SKILL.md](https://github.com/RosBradley/ask-first/releases/latest/download/SKILL.md) from the latest release. Don't upload `ask-first.zip`: Gemini expects `SKILL.md` at the top of a zip, and that zip has it inside a folder.
2. At [gemini.google.com](https://gemini.google.com), open **Customize** in the sidebar (under **More** if it's hidden), then **Skills > Create > Upload**, and choose `SKILL.md`.
3. In a new chat, type: `Plan a weekend trip to Chicago. .ask`

Gemini uses an active skill on its own when a message matches it. You can also start it with `/ask-first`.

- **Who can use it:** personal Google accounts, age 18 and over, with Keep Activity turned on. No subscription is needed. Work and school accounts can't create skills yet.
- *(unconfirmed)* Skills created by hand may not save in the mobile app. If that happens, create it on the web; it then works on mobile.

Sources: [Gemini Skills](https://support.google.com/gemini/answer/17094296), [Gems to Skills](https://support.google.com/gemini/answer/18560919).

## ChatGPT

### Custom instructions (every plan, recommended)

1. Open [prompts/ask-first.txt](../prompts/ask-first.txt) and copy all of it.
2. In ChatGPT, open **Settings > Personalization > Custom instructions** *(menu names unconfirmed)*, and paste it into the box for how ChatGPT should respond. If something is already there, paste it below that.
3. In a new chat, type: `Plan a weekend trip to Chicago. .ask`

The box holds 1,500 characters on the Free and Go plans and 5,000 on paid plans. The short version is about 1,200 characters, so it fits both. On Free, though, it leaves little room for your own instructions.

To use it in one Project only, paste it into that Project's instructions instead.

### Skills (Business, Enterprise and Edu)

ChatGPT also loads `SKILL.md` skills. Skills are documented for Business, Enterprise, Healthcare and Edu plans. *(unconfirmed)* As of September 2026, Plus and Pro users reported that personal skills don't appear in regular chats.

1. Download [SKILL.md](https://github.com/RosBradley/ask-first/releases/latest/download/SKILL.md).
2. In the sidebar, open **Plugins > Skills > Create > Upload from your computer**, and choose `SKILL.md` *(which file types it accepts is unconfirmed)*.

Don't build this as a custom GPT: OpenAI is retiring GPTs in favor of plugins.

Sources: [Custom instructions](https://help.openai.com/en/articles/8096356-chatgpt-custom-instructions), [Skills in ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt).

## Microsoft Copilot

### Microsoft 365 Copilot (work or school account)

1. Copy all of [prompts/ask-first.txt](../prompts/ask-first.txt).
2. In Copilot Chat, open **... (Settings and more) > Chat settings > Personalization > Custom instructions > Edit instructions**, paste it, and **Save**.
3. In a new chat, type: `Plan a weekend trip to Chicago. .ask`

If you don't see Custom instructions, your admin may have turned off "Enhanced personalization".

Source: [Customize how Microsoft 365 Copilot responds](https://support.microsoft.com/en-us/microsoft-365-copilot/customize-how-microsoft-365-copilot-responds-to-you).

### Copilot app (personal Microsoft account)

*(unconfirmed)* No custom-instructions feature was found for the personal Copilot app. Paste the short version as the first message of a chat, and it works for that chat.

### GitHub Copilot

GitHub Copilot loads `SKILL.md` skills. Copy the `skills/ask-first/` folder to `~/.copilot/skills/ask-first/` (all your projects) or `.github/skills/ask-first/` (one repository).

Source: [GitHub Copilot customization cheat sheet](https://docs.github.com/en/copilot/reference/customization-cheat-sheet).

## Meta AI

Meta AI has no custom instructions, so this uses its memory instead. It's best effort: the AI may not always follow it.

1. In the Meta AI app or at meta.ai, start a chat and send: `Remember this for all our chats:`, followed by everything in [prompts/ask-first.txt](../prompts/ask-first.txt).
2. Check that it was saved under **Settings > Memory**.
3. In a new chat, type: `Plan a weekend trip to Chicago. .ask`

If it doesn't stick, paste the short version as the first message of each chat where you want it.

Source: [Meta AI memory](https://www.meta.com/help/artificial-intelligence/1152856459900216/).

## Any other AI

Paste [prompts/ask-first.txt](../prompts/ask-first.txt) as the first message of a chat, then use `.ask` in that chat.

## Checking that it works

For the AIs without automated tests, run these four messages in new chats after installing:

| Type | Expected |
|---|---|
| `Plan a weekend trip to Chicago. .ask` | One line saying what it will ask about, then `Q1 of ~N` with lettered answers, the first marked (Recommended) and the last "Something else - write your own" |
| `.ask` | A first question asking what the interview is about |
| `Write a rule for new hires: ask first before deleting files` | The rule, with no interview |
| Answer `rec` to every question in the first test | A numbered list of decisions, then Proceed / Change something; on Proceed, the plan itself |
