# Set up a Visual Direction Agent

Use this guide to set up an agent that turns a visual brief into copy-ready prompts, a render hand-off and a review of the returned work. The generation tools stay with the operator. If you are the AI setting up the agent, configure access before installing the run instructions. Prompt instructions describe behaviour; the platform enforces permissions.

## 1. Collect the operator’s choices

| Operator configures | Record before setup |
|---|---|
| Deliverables and sources | Surfaces (cover, reference still, short clip); intended crop and viewing size; source of approved briefs, exact text, cleared references and, for music work, selected audio and editorial timecodes. |
| Generation interfaces | Which tools the operator can run, exact model and interface for each, accepted references, settings and limits. Decide who confirms the model selection and what to do if it disappears. |
| Handoff and review | Who runs generation, who supplies candidates, where drafts and returns go, who accepts artwork or video, and who may approve further spend, uploads or release. |

## 2. Set permissions and verify the tool choices

**Platform controls:** Give the agent read access only to the selected inputs and returned candidates, and write access only to a draft area if needed. Keep generator execution, asset upload, purchasing and publishing off the agent’s tool list. If the platform cannot scope file access, use attachments and chat drafts instead. Keep credentials out of prompts and shared files.

**Optional review tools:** Attach a still viewer and video playback or frame extraction, and read-only access to `ffprobe`/FFmpeg for media checks. If the agent cannot see a clip or run checks, the operator supplies timecoded frames and a metadata report and watches the full clip locally. The agent labels unchecked items; sampled frames are not evidence that motion passed.

**Model and workflow record:** Save the model ID or checkpoint, interface, version or graph revision, documentation link, date checked, available fields and supported inputs. Confirm these against the operator’s control panel, template or exported graph; a documentation check is not a test of their installation. Verify usage rights and the operator’s licence for the intended destination before relying on any model output, including local H3.[1]

- **GPT Image 2.0:** Confirm the intended interface actually offers `gpt-image-2` for API use; a ChatGPT label alone does not establish an API ID. Record supported `size`, `quality` and `output_format` fields and which edit inputs can be attached. OpenAI lists 10 February 2027 as the API shutdown date. Keep the exact requested model in the draft; if unavailable, stop that run and let the operator approve a named substitute and compare it on the same brief.[3][4][8]
- **FLUX 3 Image:** Confirm Black Forest Labs’ `flux-3-image` endpoint or an interface explicitly supporting that version and box syntax. Put the caption and bounding-box array in `prompt`; set `aspect_ratio` and any `images` separately. Do not copy that syntax into FLUX.2, Klein or an unverified wrapper. If the operator cannot run the endpoint, hand over the layout spec and flag that the example has not run.[5][6]
- **MiniMax H3:** Confirm the ComfyUI build, template revision, checkpoint and required nodes. The published I2V graph uses FL2VA weights and optional frame inputs; R2V uses Ref2VA with separate picture, video and audio inputs. Verify the actual canvas, frame-rate and length controls, reference order and audio output path. At 24 fps the published graph snaps length to `17k+5` frames; verify the encoded result. Use an operator-proven resolution rather than a presumed hardware default, and recheck whenever the graph changes.[1][2][7]

  Match the prompt’s alignment line to the frame inputs actually connected, not just the checkpoint name.[9]

## 3. Install the run instructions and hand-off format

Put the following block in the new agent’s run instructions. Give it the operator’s choices and the verified workflow record separately.

```text
You are a visual direction agent. Make a brief model-ready and make its output reviewable. The operator runs generation and owns selection and release.

INPUTS
Identify the surface, target crop and viewing size, exact text and object counts, cleared references, and what must remain unchanged. For motion, get the opening or reference assets, selected track or excerpt if relevant, editorial in/out and target generation length. Separate the edit time from generation time. Ask one focused question if a missing or conflicting input changes the design. Mark optional assumptions; never invent an attachment.

DRAFT
- GPT Image 2.0: use a single natural-language prompt. Specify composition, light, surface, and exact quoted lettering, placement, hierarchy and count. For edits, identify the attached base and reference roles, the one region or change, and the invariants. If lettering alone fails, preserve good art and hand off editable typesetting.
- FLUX 3 Image: specify view, materials and spatial relationships. For a supported box workflow, bind caption IDs to box rows in the same prompt. For a reference or edit, name the role of each real input and what must stay put. Check actual geometry, not the box map alone.
- MiniMax H3: choose I2V for a required opening frame; use a last frame only when both ends need control and the movement between them is plausible. Choose R2V for separate identity, motion or cadence references. Use only tags for connected inputs in the confirmed order. Describe one continuous action in playback order and at most one camera move. Use elapsed shot time unless a reference supplies cadence. Treat a scene-local audio reference as guidance for specific visible movement, not a sync guarantee. For an edit against the selected master, discard generated audio.

HAND OFF
Return the render card and one separate plain-text block per render containing only the exact model-facing prompt. Keep model selection, files and technical settings on the card. Do not run jobs, upload assets, spend or publish. If a tool, version, clearance or required input is missing, state the blocker and give the operator whatever is ready. Never substitute a model or declare success without evidence. If the operator reports a timeout, have them check job history and outputs before retrying.

REVIEW
Match the file and settings to the card. For stills, check the actual crop, full size and target display size; transcribe required text and inspect counts, clearances and invariants. For video, check decode, actual duration, dimensions, frame rate and audio streams. Watch the whole clip at speed and inspect key frames for contact, continuity and the usable cut. Mark each check pass, fail or not checked, with a file, visible detail or timecode. Withhold a failed candidate; change one variable and recheck the required invariants on the new result. A prompt or metadata report alone is not a visual pass.
```

**Render and review card** (one per output, separate from the model-facing prompt):

```text
Output and intended use:
Operator action / exact model / interface or graph revision:
Inputs in connection order / role / clearance:
Settings (size, ratio, quality or format; frame rate, length, seed if exposed):
Generation length / usable clip in-out / editorial placement (motion only):
Immutable requirements / acceptance checks:
Status (draft / blocked / returned unreviewed / pass / fail) and evidence:
Next operator decision:
```

## 4. Validate before activation

Give the new agent a fictional brief for one square cover and one short clip using a widescreen opening still. Use invented filenames and no live calls. Confirm that it returns separate prompt blocks and settings cards, distinguishes the cover from the opening frame, and leaves rendering and release with the operator. Remove the first frame or mark the exact image model unavailable; the agent should identify the blocker without substituting. Give it a mock observation that the knob drifts during the shot; it should identify the failed check and propose a one-change comparison without claiming it watched a render. Verify the platform has the agreed read/draft access and no execution or publish connection before enabling the agent.

## Sources

[1] https://docs.comfy.org/tutorials/video/minimax/minimax-h3 — ComfyUI: MiniMax H3 workflows

[2] https://docs.comfy.org/tutorials/video/minimax/minimax-h3-prompt-guide.md — ComfyUI: MiniMax H3 prompt guide

[3] https://developers.openai.com/api/docs/guides/image-prompting.md — OpenAI: image prompting

[4] https://developers.openai.com/api/docs/deprecations.md — OpenAI: API deprecations

[5] https://docs.bfl.ml/api-reference/utility/generate-an-image-with-flux-3.md — Black Forest Labs: FLUX 3 Image API

[6] https://docs.bfl.ml/flux_3/flux3_image_bounding_boxes.md — Black Forest Labs: FLUX 3 Image bounding boxes

[7] https://docs.comfy.org/tutorials/video/minimax/minimax-h3-native.md — ComfyUI: native H3 I2V and R2V graph controls

[8] https://developers.openai.com/api/docs/models/gpt-image-2 — OpenAI: GPT Image 2 API model

[9] https://huggingface.co/MiniMaxAI/MiniMax-H3/raw/main/docs/VIDEO_PROMPT_WRITING_GUIDE_base_en.md — MiniMax: H3 base-mode prompt writing guide
