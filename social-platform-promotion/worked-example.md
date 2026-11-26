# Worked example: The Light Above the Laundrette

**Fictional example.** The artist, files, approvals, IDs and observations are invented. The URLs are on reserved example domains. No media was processed and nothing was uploaded, scheduled, published or tested on a live account.

## Brief and decision

Lantern Static supplies a cleared 3:42 master, thumbnail and video export for a guitar-led single about the light across the road from a late shift. The brief is one YouTube catalogue entry and one Facebook Page link post when listeners can play it. The first export cuts off the last chord’s decay. The artist replaces it with `laundrette-official-audio-v4.mp4` and approves `laundrette-thumb-v2.jpg`. The mock preflight entry records 1920×1080 H.264 at 25 fps, 48 kHz stereo AAC, 3:42 against the master, a clean full decode, intact opening and tail, and legible thumbnail text at phone size. Live work would bind the measured SHA-256 to v4; no hash is claimed here.

**Judgement call:** The subtle flicker in the artwork does not make this a lyric video. Use **Official Audio**. Skip the extra teaser and give the Page one concrete image: the only light left on in the street. Do not schedule both posts for the same minute; Facebook would announce playback even if the video were delayed.

## Copy-ready release pack

**YouTube Studio — metadata v3**

```text
Title: The Light Above the Laundrette — Lantern Static | Official Audio

Description:
A slow, guitar-led song about finishing a late shift and looking for one light still on.

Written and recorded by Lantern Static. Cover artwork by Lantern Static.
```

Use export v4 and thumbnail v2 on the fictional Lantern Static channel. In this example the artist confirms **Not made for kids** and no material requiring altered or synthetic content disclosure. No Premiere. Save Private for review, then schedule that same video ID only after release approval.

**Facebook Page — message v2**

```text
The street had gone dark by the time the late shift finished. Across the road, the laundrette was still lit. That’s the picture behind this song. Listen on YouTube.
```

Set the separate link field to `https://watch.example.invalid/v/EXAMPLE-YT-04`; do not rely on a URL in the message body. Target: fictional Lantern Static Page, public. Approved window: **12 February 2027, 18:35–19:00 Australia/Perth (UTC+08:00), or 10:35–11:00 UTC**, only after signed-out playback and Studio Public are confirmed. This is a conditional window, not a saved Facebook schedule.

## Mock release ledger

Release key `DEMO-LAUNDRETTE`. `DEMO-A1` covers private staging of export v4 and metadata v3. `DEMO-A2` covers the same video’s public schedule and Page message v2 with the exact watch link during the approved window. The example assumes separate verified Studio and Page routes, each restricted to its approved actions. Local observations are in Australia/Perth (UTC+08:00).

| Local observation | Item | State and evidence that would be recorded |
|---|---|---|
| 11 Feb, 15:02 | YouTube `EXAMPLE-YT-04` | **Upload received, processing.** ID bound to v4; no second upload while processing is pending. |
| 11 Feb, 15:19 | Same video | **Private, ready for review.** Fresh Studio read matches title, thumbnail, settings and 3:42 duration; no blocking restriction; private review playback works. Review reference: `https://studio.example.invalid/video/EXAMPLE-YT-04/edit`. |
| 11 Feb, 16:11 | Same video | **Scheduled.** Reopened Studio shows `2027-02-12T18:30:00+08:00` = `2027-02-12T10:30:00Z`, Private until Public. Facebook approved, not scheduled. |
| 12 Feb, 18:35 | Same video | **Public in Studio; Facebook held.** The signed-out watch page opens but the player does not play the track. |
| 12 Feb, 18:36 | Same video | **Live.** Studio still shows Public; the exact watch URL plays the expected video signed out. |
| 12 Feb, 18:38 | Facebook Page | **Unknown.** Page identity and prior records checked, exact message and link dry-run checked. One write times out before returning an ID. No retry. |
| 12 Feb, 18:41 | Facebook `EXAMPLE-FB-07` | **Live.** Read-back across the relevant Page records finds one published match by message, video target and attempt time and no scheduled duplicate. The permalink is `https://social.example.invalid/posts/EXAMPLE-FB-07`; the saved post has one share attachment with the exact watch target and a preview image. No second write. |

## What goes back to the artist

In the resolved case, hand back the two verified links and note that the Page ID came from read-back, not a second post. If the API was unavailable **before** any attempt, give the human publisher the message, separate attachment, playback gate, time window and permalink/preview checklist for Meta Business Suite. If a write may already have happened and the record is inconclusive, hand over the attempt details for reconciliation instead. If the window expires, the artist decides a new one. Nothing here authorises edits, deletion or a further channel.
