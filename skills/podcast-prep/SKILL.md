---
name: podcast-prep
description: >
  Multi-agent podcast preparation system. Transforms minimal guest information into
  a complete interview prep package — guest card, context brief, and full interview
  outline. Also handles post-recording output: show notes, social copy, and clip
  recommendations from a transcript. Adapts to any podcast format, language, or
  platform. Use when someone says "help me prep for my podcast", "I'm interviewing
  X next week", "write my show notes", "generate interview questions", or "I just
  recorded an episode". Works for guests with little or no public profile — designed
  for real-world podcasters whose guests are athletes, coaches, researchers, or
  everyday people.
license: MIT
metadata:
  author: siyan
  version: "1.0"
  tags: podcast, interview, show-notes, social-media, research
compatibility: Requires web search access for guest research (gracefully degrades without it)
---

# Podcast Prep

A full-stack prep pipeline for podcast hosts. Two phases: pre-recording and post-recording.

---

## Step 0 — Show profile (run once per new host)

Before doing anything else, check if the host has already told you about their show.
If not, ask these three questions together in one message — don't spread them across turns:

1. **Show name and topic** — what's your podcast about?
2. **Tone** — how would you describe the feel of your show? (e.g. conversational, academic, fan-driven, investigative, storytelling)
3. **Social platforms and language** — where do you post, and in what language(s)? (e.g. Instagram + English, Xiaohongshu + Chinese, LinkedIn + English)

Store the answers as the **show profile** and apply them throughout:
- Interview tone and question framing come from #1 and #2
- Social copy format and language come from #3
- If the host skips this step and dives straight in, infer what you can from context and proceed — don't block on missing info

Once you have the show profile, never ask for it again in the same session.

---

## Which phase to run

**Phase 1 — Pre-recording** (preparing for an upcoming interview)

Ask the host for:
- Guest name
- Sport / area of expertise
- Any background they have: bio, IG posts, links, notes — paste everything
- Episode theme or angle (optional)

Then run all three agents in parallel and synthesize into one output:
1. `agents/researcher.md` — web search + context structuring
2. `agents/guest-card.md` — guest profile card
3. `agents/interviewer.md` — full interview outline

→ See [Phase 1 output format](references/OUTPUT_FORMATS.md#phase-1)

**Phase 2 — Post-recording** (after the episode is recorded)

Ask for:
- Episode transcript (paste or file)
- Guest name + topic (if not in transcript)

Run `agents/publisher.md` and deliver the post-production package.

→ See [Phase 2 output format](references/OUTPUT_FORMATS.md#phase-2)

---

## Handling guests with no public profile

Most podcast guests won't have a Wikipedia page. This is normal and expected.

When web search returns little:
- Do NOT hallucinate credentials or career details
- Use the host's provided context as the primary source
- Have the Researcher focus on **the sport or topic itself** — recent news, cultural
  context, key debates, relevant stats — rather than the person
- Have the Guest Card surface **inferred angles** from whatever signals exist:
  tone of their posts, the sport they play, milestones they've mentioned
- Flag clearly what is sourced vs. inferred

The interview outline should be just as strong with a low-profile guest. The questions
come from the angle, not from the guest's fame.

---

## Tone and voice

This skill was built for a women's sports podcast and defaults to that sensibility:
- Genuine curiosity over performance metrics
- Space for the guest's interiority — how things *felt*, not just what happened
- Awareness that many women athletes have stories that go untold in mainstream coverage
- Questions that open doors rather than close them

To adapt for another podcast: tell the skill your show's angle and it will adjust
question framing accordingly. The structure stays the same; the voice changes.

---

## Agent files

- `agents/researcher.md` — how to run the Research agent
- `agents/guest-card.md` — how to build the guest profile
- `agents/interviewer.md` — how to generate the interview outline
- `agents/publisher.md` — how to handle post-recording output
- `references/OUTPUT_FORMATS.md` — exact output templates for both phases
