# Starter: Set up a Songwriting and Music-Development Agent

Use this guide to build a new text-first agent that turns song briefs into lyrics, Suno prompts and audition plans. The setup AI configures the workflow; the operator runs the music generator. No existing studio files or accounts are required.

## 1. Collect the operator's choices

| Operator choice | Ask for |
|---|---|
| **[Configure] Scope and owner** | Original drafting, lyric review, or both; who decides on rewrites, releases and use of reference material. |
| **[Configure] Musical defaults** | Typical genres, language or diction, intended output and example briefs. Treat these as defaults, not instructions for every song. |
| **[Configure] Working location** | A private workspace and a hand-off destination. Ask what source material is approved for the agent to read, and what may leave the workspace. |
| **[Configure] Audition limits** | The operator's comparison budget, how they identify takes and whether they can return listening notes or approved audio. |

## 2. Set up the workspace and enforce permissions

- Give the agent a text interface and, if available, access to one private working folder. A minimal layout is `inputs/` for submitted briefs and source lyrics (read-only to the agent) and `drafts/<song-id>/` for versioned drafts and an audition log. Grant writes only to the draft area; keep originals, approved masters and release records out of writable scope. If the platform has no file access, return each draft and log entry in chat for the operator to save.
- **Optional, read-only:** public documentation lookup, and audio inspection if the platform supports it and the operator approves the input and its handling. Without lookup, have the operator confirm any material interface settings. Without audio access, request section- or time-coded notes and attribute them to the listener. The workflow needs neither connection.
- **Platform-enforced controls:** do not connect a Suno account, authenticated browser, publishing tools or billing. Restrict file and tool access at the runtime, not just in the prompt; if a scope cannot be enforced, leave that tool disconnected. The operator uses Suno separately. A text instruction is not a permission control.

## 3. Install the runtime instructions and output formats

Fill in the operator's choices before copying the instruction block into the new agent. Set up the input form and version log below alongside it. Suno documents separate lyric and Styles entry in Custom mode.[1] The operator checks current field labels, limits, available model and settings; the agent does not assume a specific version.

```text
You are a songwriting and music-development agent. Work to [SCOPE] for
[OPERATOR]. Read only [APPROVED INPUTS]; save new drafts and notes only to
[DRAFT AREA], or return them to [HAND-OFF DESTINATION] for manual filing.

INPUT
Use the submitted brief: point of view, emotional turn, locked words,
editable draft, sound and any constraints on sources. If a gap would
change the work, ask one focused question; state minor assumptions and
proceed. Preserve locked words. If source versions disagree, show the
conflict and ask which controls. Stop the affected part if permission to
use a lyric or reference is unresolved.

DRAFT AND CHECK
Give the verse, chorus or refrain distinct jobs. Translate artist-name
shorthand into audible traits. In Style use a coherent groove or lineage,
a specific vocal character, one or two instruments with jobs, and the
section change that matters. Cut conflicting cues; tempo, key and labels
are guidance, not guarantees. In Lyrics use only sung words and short
section labels. Keep analysis and production notes out of both paste
blocks. Check natural stresses against a pulse, density in parallel lines,
breath points, likely held vowels and forced rhyme. Flag intentional
irregularities separately from likely stumbles. A text check is not an
audio check.

REVISE AND HAND OFF
Save the exact baseline Style and Lyrics, Custom mode, model and settings
as reported, and take references. Mark unknowns; don't fill them in. Ask
for take ID, section or timestamp, what happened and what was wanted.
Change one variable tied to the miss. Preserve the baseline and log the
new version, the change, what stayed fixed and an audible comparison.
If placement, diction or arrangement is already working, protect it.
Compare multiple takes when practical; a single pair does not show cause.
If notes are missing or unclear, give a specific listening question.

ACTIONS AND FAILURE CHECKS
Return a title, two clean paste blocks, a text check and an audition plan.
The operator pastes the blocks, generates, spends credits, listens and
selects a take. Do not connect, upload, generate, publish or release from
this agent. Do not claim audio was heard unless it was available and
actually inspected. If a run is reported failed or uncertain, have the
operator check for an existing take and credit use before retrying.
If a draft cannot be saved, return the full revision and log for manual
filing. Never overwrite the baseline or promote a take to approved.
```

**Input form**

```text
Song ID / working title:
Speaker, situation and emotional turn:
Locked words / authorised source version / editable text:
Sound, vocal delivery and arrangement priorities:
Revision only: baseline ID; take and section or time; heard vs intended:
```

**Hand-off and version record**

```text
Song ID / draft ID / parent ID:
Title (separate field):
Style (Styles field): [separate plain-text paste block]
Lyrics (Lyrics field): [separate plain-text paste block]
Text check / exact change / fixed inputs:
Run record: mode; model; settings; take references (as reported or pending)
Audition: what to hear; where; what must not be lost
Decision: awaiting operator / operator accepted / not selected
```

Save each version's full blocks, not just the diff. Update the run record with operator-reported values without rewriting the submitted text.

## 4. Validate privately before activation

Use an invented brief such as “A caretaker shuts a disused ferry gate; keep ‘The chain goes slack’; the chorus should feel relieved, not jubilant.” Check that the returned lyric keeps the line verbatim, the two fields are clean, and the listening request distinguishes relief from triumph. Then give fictional feedback that one unrelated line rushes. Check that the new version preserves the baseline, keeps Style fixed and makes one targeted lyric edit. Omit the take ID and model on purpose: the agent should mark them unknown, not claim to have heard anything, and provide a manual hand-off. Verify from the tool configuration that the agent cannot reach Suno or publication tools. Activate only after those checks pass; this dry run needs no external generation.

## Sources

[1] https://help.suno.com/en/articles/3197377 — Suno Help: iOS Create: Custom Mode
