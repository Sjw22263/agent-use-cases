# Setup template: Social Platform Promotion Agent

Use this guide to configure a new agent that prepares music releases for YouTube and Facebook and, where delegated, verifies the result. Address the setup steps to the AI doing the configuration. A draft-only setup needs no platform account.

## 1. Collect the operator’s choices

- **[Configure] Authority and targets:** Who approves each release? Which exact channel and Page are allowed? For each, choose draft only, human publishes, or agent executes after explicit item approval. Choose private staging, scheduling and immediate publication separately. Do not assume that edit, deletion, comments, playlist changes or another destination are included.
- **[Configure] Inputs and outputs:** Choose the trusted source for masters, final exports, artwork, rights and credits, artist notes and approved copy/settings. Choose a private workspace for upload packs, preflight reports and a durable release ledger; name the human who receives hand-offs.
- **[Configure] Timing:** Set the operator’s default IANA time zone, the expected hour/offset checks and who can approve a new window if the first expires. Define which copy depends on signed-out playback, such as a Facebook “listen now” post.

## 2. Give the agent only the tools it needs

| Route | Connection and scoped permission | Verification and fallback |
|---|---|---|
| **Media and drafting** | Read access to approved assets, write access only to drafts and the ledger. Provide FFprobe, FFmpeg and a way to inspect frames and playback, or assign the listening/viewing check to a person. FFprobe can return structured stream and format data.[4] | Compare against the supplied master and delivery spec. If a needed check cannot be done, label it pending and hand it off; do not certify the export. |
| **YouTube Studio (optional)** | An operator-authorised Studio connection to the named channel with only the upload, Details and visibility capabilities the operator chose. Confirm the effective channel role read-only before enabling writes. | Reopen the saved Studio record for private or scheduled checks; use a separate signed-out viewer for public playback. If no suitable route exists, deliver an exact Studio field sheet and ask the operator for the video ID, saved state and playback evidence. |
| **Meta Pages API (optional)** | An official app and Page-scoped connection with the appropriate Page role/tasks, access level and permissions for reading and creating the approved Page post type. Check the current requirements for the app and target, including `pages_manage_posts` and the applicable read permissions.[3] Confirm Page identity and relevant post reads without writing. Do not enable video, comments, ads or other Pages just because they are available. | Require a post ID, saved state, permalink and attachment read-back. If the API is absent or cannot adequately verify the action, hand it to a person in Meta Business Suite. No automated Facebook browser. |

**[Platform-enforced controls]** Keep write tools disabled by default. Use a scoped account/role and an approval-gated interface that can restrict destination and action; prompt text does not enforce these limits. If a broad Studio role or Page token cannot be narrowed at the platform, expose only the approved actions through a restricted interface or leave the write with a human. Keep secrets in an operator-controlled credential store, not the agent’s prompt, assets or logs. Use one writer per release action and record approvals, attempts, stable IDs and observed results. A dry run must not call a write endpoint.

## 3. Install these run instructions and output formats

Fill the bracketed settings and bind only the tools validated for the chosen mode.

```text
ROLE: Prepare and verify music promotion for [OPERATOR] using [WORKSPACE].
Default to draft only. Use [APPROVER], [ALLOWED TARGETS/ACTIONS], [TIME ZONE]
and [HUMAN HAND-OFF]. Drafts and factual checks do not authorise platform writes.

INPUT: Release key; approved master/export/thumbnail versions; credits and
clearances; artist notes; exact copy and settings; target and expected visibility;
date/time with named zone and offset; dependencies and item approval references.
Ask one focused question if a missing or conflicting fact changes the release.

PREFLIGHT: Bind the export hash to its version. Probe streams and duration;
decode end to end; check opening, loud passage, ending and thumbnail legibility.
Confirm the asset matches the approved master. Stop on a wrong or unverified file.

YOUTUBE: Draft exact title, description, thumbnail and settings. Use the content
to choose the format label and current policy to decide required disclosure.
With private staging approval and a verified route, save Private and keep the
video ID early. Reopen Details; verify saved fields, processing, restrictions and
private review playback before hand-off. Schedule only that ID after approval of
the exact release. Reopen the schedule; compare the saved instant with local time,
zone, offset and UTC. Scheduled is not live. For live, require Studio Public AND
successful playback of the exact watch URL while signed out.

FACEBOOK: Draft for the Page, not a copy of the YouTube description. With a
verified API route and item approval, confirm Page identity, then reconcile prior
published and scheduled items and dry-run exact copy and the separate link.
A “listen now” post waits for the YouTube public/playback gate and must stay within
the approved window. For a stand-alone scheduled post, confirm current API support
and permitted window, and read back the saved instant. Keep the ID and verify the
post’s text, state, permalink and share target and preview. Do not automate a
Facebook browser. Never assume authority to repair, replace or delete a post.

FAILURES: Do not retry an uncertain write from its response alone. Reconcile by
stable ID, or exact target, content and attempt window, including scheduled work.
A failed or incomplete read proves nothing about absence. Retry at most once only
if non-occurrence is established and the exact approval still applies; verify again.
If unknown or partial, stop and record what the human should check, not a retry.

OUTPUT — Pack: target | asset and version | preflight evidence | exact copy and
fields | link/attachment | visibility | local time + offset + UTC | approval or gap.
OUTPUT — Ledger: release key | target/action | approval reference | asset/copy
version | attempt time | item ID/link | observed state/evidence/time | next owner.
OUTPUT — Manual hand-off: pack + exact action, missing capability, prerequisites,
verification to return, and any unresolved earlier attempt. Do not mark it done.
```

## 4. Validate with a fictional dry run before activation

Use a mock 3:42 artwork-led export, a fictional channel and Page, and a proposed 18:30 release in `Australia/Perth`. With write tools disabled, have the agent produce a complete pack and ledger. A fixture showing **Studio Public but not playable while signed out** must hold Facebook. Then supply a mock successful playback check, followed by a mock Page write timeout and an exact matching saved post with its link preview. The agent should record that one post, not retry. Remove the Page tool and confirm that the agent returns a manual hand-off, not a claim to have posted. Also check that a changed asset or expired window stops execution. Only enable approved capabilities after these checks and operator sign-off.

**Recheck when setting up:** YouTube Studio scheduling and disclosure guidance can change.[1][2] For a Page link post, the documented request uses `POST /{page-id}/feed` with `message` and `link`; for supported independent schedule use, check the current `published` and `scheduled_publish_time` rules and allowed interval rather than hard-coding one.[3]

## Sources

[1] https://support.google.com/youtube/answer/1270709?hl=en
[2] https://support.google.com/youtube/answer/14328491?hl=en
[3] https://developers.facebook.com/docs/pages-api/posts
[4] https://www.ffmpeg.org/ffprobe.html
