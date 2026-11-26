# Worked example: Low Tide Signal

**Fictional planning exercise.** The song, assets and candidate observation are invented. No image or clip was generated, uploaded, inspected or tested. The prompts are for an operator to run once the named models and required inputs are available.

## The brief

Make a square cover for an instrumental single titled **LOW TIDE SIGNAL**, and a five-second widescreen teaser shot. Both show a closed ferry booth just after departure: worn brass, slate-blue paint and cold window light. The cover needs one lamp and the exact title. In the shot, a gloved hand enters from the right, turns down the lamp and leaves; there is no lettering. The selected master is `low-tide-signal-master.wav`, with the shot to sit at `00:18.000–00:23.000`.

**The judgement call:** The cover makes the lamp a centred silhouette below the title. A hand would have to reach too far into that composition, and animating it would carry the title into the teaser. The agent keeps the material and lighting, but specifies a new still with the lamp on the left and its knob in full view.

## 1. GPT Image 2.0: square cover with a short title

**Settings for the operator:** OpenAI Images API, `model: gpt-image-2`, `size: 1024x1024`, `output_format: png`. Text-to-image; no references. Check model availability before running: OpenAI lists this API model for shutdown on 10 February 2027. No substitution is part of this example.[3][4][8]

```text
Create a square photographic single cover. On a worn slate-blue counter sits exactly one tarnished brass ferry signal lamp, with a cylindrical glass chimney and one small round black adjustment knob on the right side of its base. Frame at counter height from a slight right three-quarter angle. Centre the lamp horizontally, with the whole silhouette below the upper quarter and its base clear of the bottom edge. A low amber flame glows through the glass; cool light from the left picks up scratches in the brass. The deep blue-grey wall behind it falls into an even, dark field across the upper quarter. The counter is bare except for the lamp.

Place the exact title "LOW TIDE SIGNAL" once, on one line, centred in the upper quarter with clear margins. Use large, off-white, moderately spaced sans-serif capitals. Keep the title above and clear of the lamp silhouette. The title is the only visible lettering.
```

**Acceptance:** At full size, transcribe the title and compare it character for character. At about 128 pixels square, check that the title and lamp read separately. If a brass highlight is blown but the image works, attach the candidate as the base and request only that the highlight be dimmed; compare crop, silhouette, flame and title against the original. If spelling alone fails, preserve the art, clear the type band and typeset the verified title in a layout tool. Recheck the composite at both sizes.

## 2. FLUX 3 Image: a first frame with room for action

**Settings for the operator:** Black Forest Labs’ `flux-3-image` endpoint, `aspect_ratio: 16:9`, no input images. Paste the entire block as `prompt`, including the JSON array after the caption. The array uses `[top, left, bottom, right]` on a 0–1000 grid; it is prompt content, not an API settings field. Save the accepted still as `booth-first.png`.[5][6]

```text
A low right three-quarter view across the bare counter of a closed ferry booth at night. The one lamp <lamp> stands on the left third, fully in frame. Its one small round black adjustment knob projects from the right side of the base, unobstructed and clearly silhouetted against matte slate-blue paint. The single high window <window> spills cool light into the booth. The counter <counter> catches a shallow amber pool at the lamp base. To the right of the lamp, uninterrupted wall and bare countertop leave a straight clear path from the right edge to the knob. The booth is empty and every surface is unlettered. [{"id":"lamp","bbox":[290,185,790,455],"desc":"One tarnished brass signal lamp with a glass chimney, a steady amber flame, and one black adjustment knob visible on its right side"},{"id":"window","bbox":[75,80,275,355],"desc":"One small high frosted window admitting diffuse cool blue light"},{"id":"counter","bbox":[695,0,1000,1000],"desc":"One continuous worn slate-blue counter in perspective, with a compact amber light pool beneath the lamp and a clear right side"}]
```

**Acceptance:** Inspect the returned 16:9 still. Trace a straight approach from the right edge. Reject a hidden knob, a second lamp or a sill crossing that path. If the lamp crowds the approach, move its box a little left without resizing it and keep the caption consistent with the new position. Recheck the actual crop and route. Box coordinates guide placement, not pixel tolerances.

## 3. MiniMax H3 I2V: one continuous shot for a five-second edit

**Settings for the operator:** Use the published ComfyUI **MiniMax H3 Image to Video** template with FL2VA weights. Connect the accepted `booth-first.png` to `first_frame` only; no last frame or audio reference. Match the still to the actual 16:9 canvas so it is not stretched. At 24 fps, request `length: 141` frames (nominally 5.875 s on the documented frame grid). Use an operator-preflighted resolution and record the actual dimensions, workflow revision, and seed if exposed. Paste the following as one prompt. Its elapsed times describe the action, not guaranteed frame events.[1][2][7]

Use the first-frame-only alignment line because no last frame is connected.[9]

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] One continuous photographic shot across the slate-blue counter. Keep the one brass lamp planted in place with its black adjustment knob visible on the right side of the base. The high frosted window stays cool blue. The camera makes one shallow, very slow push towards the lamp, keeping the knob in view, then settles by five seconds. For the first second the booth is empty and the amber flame is steady. From one to three seconds, one right hand in a dark wool glove enters from the right just above the counter, reaches the knob and grips it between thumb and forefinger. From three to four seconds the fingers turn the knob a small amount clockwise, the flame dwindles to a pinprick and the amber pool fades with it. From four to five seconds the hand releases the knob and withdraws to the right. Hold on the still lamp and cool window light through the end. All surfaces remain unlettered.
overall_soundscape: N/A
non_diegetic_music: N/A
```

**Editorial hand-off:** Proposed output `booth-dim-v01.mp4`. Use clip `00:00.500–00:05.500` at master `00:18.000–00:23.000`, only if the actual action and hold fit that trim. The music cue is for the editor, not a model input. Discard any generated sound and use the original selected master.

**Illustrative review, not a measured result:** Suppose the flame dims, but the knob slides sideways at `00:03.200`. Fail hand contact and prop continuity. Confirm the opening frame and graph settings, then replace only the camera move with a locked camera. For each returned file, use `ffprobe` to check actual duration, dimensions, frame rate and audio streams, and FFmpeg to check full decode. Watch through at speed, then inspect opening, grip, turn, release and hold. If the knob still drifts, consider exposing it more clearly in a new first frame before another run. No clip means none of these render checks has passed.

## What remains for the operator

Run and accept the cover and first frame separately. Choose a usable take, trim it against the master and check the assembled teaser for picture and sound. The prompt hand-off grants no release approval.

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
