---
name: podcast-prep
description: >
  Multi-agent podcast preparation system for podcast hosts. Starts from a topic
  or a topic-plus-guest and works interactively through the full production cycle:
  finding the episode angle, building the guest card, iterating on the interview
  outline, and handling post-recording output (show notes, social copy, clips).
  Adapts to any podcast format, language, or platform. Use when someone says
  "I want to do an episode about X", "I'm having [guest] on to talk about Y",
  "help me prep for my podcast", "I'm interviewing X next week", "write my show
  notes", "generate interview questions", or "I just recorded an episode".
  Works for guests with little or no public profile.
license: MIT
metadata:
  author: siyan
  version: "2.0"
  tags: podcast, interview, show-notes, social-media, research, topic-development
compatibility: Requires web search access for research (gracefully degrades without it)
---

# Podcast Prep

A full production pipeline for podcast hosts — from initial topic curiosity to
published episode. Every phase is conversational and iterative, not one-shot.

---

## Step 0 — Show profile (once per host)

Before anything else, check if the host has shared their show context.
If not, ask these three things together in one message:

1. **Show name and topic** — what's your podcast about?
2. **Tone** — how would you describe the feel of your show? (e.g. conversational, investigative, fan-driven, academic, storytelling)
3. **Social platforms and language** — where do you post, and in what language(s)?

Apply this profile throughout all phases. Never ask for it again in the same session.
If the host skips this and dives straight in, infer from context and proceed.

---

## Phase 0 — Topic development

**Triggered when:** the host mentions a topic they want to explore, with or without
a guest already in mind.

Two starting points:

**Entrance A — Topic only**
"I want to do an episode about figure skating"
→ Run `agents/topic-scout.md`

**Entrance B — Topic + guest**
"I'm having my friend Qingshu on to talk about football blogging"
→ Run `agents/topic-scout.md` (the guest's perspective shapes the angle)

The Topic Scout works interactively — it does not produce a one-shot report.
It researches, offers directions, digs with the host, and converges on a specific
episode angle. When the angle is confirmed, it produces a handoff summary.

---

## Phase 1 — Guest prep

**Triggered when:** the episode angle is confirmed and a guest is identified.

Run these two in parallel, using the Topic Scout's handoff summary as input:

1. `agents/researcher.md` — background on the guest + deeper context on the angle
2. `agents/guest-card.md` — guest profile card with sourced facts and interesting angles

Then run:

3. `agents/interviewer.md` — iterative interview outline built with the host

The Interviewer is a conversation, not a generator. It proposes directions first,
then builds section by section, marks high-clip-potential questions with ⚡,
and incorporates research on the fly when the host doesn't know something.

**Incorporating guest feedback:** If the guest says "we can also talk about X" or
"please don't ask about Y" before the recording, just tell the Interviewer agent
and it will update the outline.

---

## Phase 2 — Post-recording

**Triggered when:** the host shares a transcript or says "I just recorded."

Run `agents/publisher.md` to produce:
- Show notes with timestamps
- Social copy for each platform in the show profile
- 3 clip recommendations with timestamps and suggested hooks

---

## Handling guests with no public profile

Most guests won't have a Wikipedia page. When web search returns little:
- Use the host's provided context as the primary source
- Focus research on the topic/field itself rather than the person
- Flag clearly what is sourced vs. inferred in the guest card
- The interview outline should be just as strong — questions come from the angle, not from fame

---

## Tone defaults

Defaults to the sensibility of a women's sports podcast: genuine curiosity over
performance metrics, space for interiority, questions that open doors.

To adapt: tell the skill your show's angle at the start and question framing adjusts.
The structure stays the same; the voice changes.

---

## Agent files

- `agents/topic-scout.md` — Phase 0: topic → episode angle (interactive)
- `agents/researcher.md` — Phase 1: guest background + topic context
- `agents/guest-card.md` — Phase 1: guest profile card
- `agents/interviewer.md` — Phase 1: iterative interview outline with ⚡ flags
- `agents/publisher.md` — Phase 2: show notes, social copy, clips
- `references/OUTPUT_FORMATS.md` — output templates for Phase 1 and Phase 2
