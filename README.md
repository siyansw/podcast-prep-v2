# podcast-prep

An [Agent Skill](https://agentskills.io/specification) that turns minimal guest information into a complete podcast interview prep package — and handles post-production too.

Built for **[体会一下 Sport Herstory](https://www.xiaohongshu.com/)**, a women's sports podcast. Designed to work for any podcast host, regardless of topic or guest profile.

## What it does

**Before recording:** Give it a guest name, any background you have (bio, IG posts, a few sentences — whatever you've got), and an optional episode angle. It runs three agents in parallel and delivers:

- Guest card with sourced bio, key career moments, and interesting angles to pull
- Context brief about the sport or field (current news, cultural context, relevant stats)
- Full interview outline — warm-up, two core sections, a pivoting "turn" question, and closing
- Host notes with follow-up probes and anything to avoid

**After recording:** Paste in the transcript and get:

- Show notes with timestamps (ready for podcast platforms)
- Social copy for Xiaohongshu/WeChat (Chinese) and Instagram (English)
- 3 clip recommendations with timestamps and suggested hooks

## Works when your guest isn't famous

Most real podcast guests don't have a Wikipedia page. This skill is designed for that reality. When public information is sparse, it leans on what you give it and focuses research on the sport or topic itself rather than the person — so the interview outline is just as strong.

## Install

```bash
npx skills add YOUR_GITHUB_USERNAME/podcast-prep
```

Or manually: copy `skills/podcast-prep/` into `.agents/skills/` in your project.

## Compatibility

Works with any agent that supports the [Agent Skills](https://agentskills.io) open standard:

- [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview)
- [Cursor](https://cursor.com/docs/context/skills)
- [VS Code (GitHub Copilot)](https://code.visualstudio.com/docs/copilot/customization/agent-skills)

Requires web search access for guest research. Degrades gracefully without it — the skill will work from user-provided context alone.

## Usage

Just ask naturally in any supported agent:

> Help me prep for my podcast — I'm interviewing a rhythmic gymnast next Thursday

> I just recorded an episode, can you write the show notes and social copy?

> Generate interview questions for [guest name], here's her bio: [paste]

## Adapting for your podcast

The skill defaults to a women's sports sensibility — questions that prioritize interiority over stats, and that make space for untold stories. To adapt it for your show, just tell the agent your angle at the start of the conversation and it will adjust the question framing accordingly.

## License

MIT
