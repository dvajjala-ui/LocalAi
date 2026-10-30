# LocalAi project brief

Recorded: 30 October 2026 (Asia/Calcutta).

## What I want

I want a personal AI video editor. I will provide the videos and audio, and I want it to help me sync them, manage the media, and edit the result professionally. It should also work with images and voices.

I want all three workflows:

1. Match video clips and images to a separate voiceover or music track.
2. Align camera footage with audio recorded on a separate microphone.
3. Change a person's lip movements to match new speech.

I want to use my Oracle free account for the processing. I do not have a local machine available for this work, and I want everything to stay free. I should be able to use the editor through a browser.

This section is a cleaned-up restatement. The original user wording is preserved in [the conversation](CHAT_2026-10-30.md).

## Confirmed requirements

- Server-side processing on Oracle, with a browser for upload, instructions, preview, corrections, and download.
- User-supplied footage, images, narration, and other audio.
- Media organization, synchronization, captions, basic editing, and export.
- All three synchronization workflows above, including lip regeneration.
- No required local model installation, local GPU, paid model API, or subscription.
- Professional output is the desired outcome; it has not been demonstrated.

## Proposed behavior, subject to validation

Keep originals and represent changes as an editable timeline. Analyze speech and selected frames, suggest a draft, and let the user correct shot selection, cut timing, captions, and audio levels before final export.

The assistant recommends a small, queued CPU pipeline for the first version. Lip regeneration is a separate experiment because its compute and quality requirements differ substantially from shifting existing audio into alignment.

These are implementation recommendations, not additional confirmed user requirements.

## Open questions

- Which Oracle region, instance shape, CPU architecture, RAM, disk allocation, and remaining Always Free quota are actually available?
- What footage lengths, resolutions, frame rates, and upload sizes should be supported?
- Which spoken languages and accents matter? Is voice generation or voice cloning needed, beyond editing supplied audio?
- Are the outputs strictly personal/noncommercial, or will they be monetized or used for clients? This affects model choice, particularly original Wav2Lip.
- What kinds of footage matter most: talking heads, tutorials, interviews, reels, music videos, or mixed footage?
- How much waiting per job is acceptable?

## Next steps in order

1. Read-only inventory of the Oracle account and VM. Confirm actual allocation and free allowance before provisioning or resizing.
2. Benchmark FFmpeg and whisper.cpp on representative media.
3. Benchmark Qwen3.5-2B with supported 4-bit weights and its visual component. Compare 4B only if memory and latency allow. Verify ARM runtime support rather than assuming a Python package or container will work.
4. Prove microphone/camera alignment using common reference audio. Check the start, middle, and end for drift; fail visibly when a reliable match cannot be found.
5. Prove narration-to-visual placement using transcript timestamps and sampled frames. Check creative relevance manually.
6. Build the browser workflow around successful workers, with progress, cancellation, recoverable jobs, and preview before export.
7. Test a separate short lip-regeneration clip on CPU. Measure processing time and visible quality before adding it to the main editor.
8. Reassess whether the full requirement is achievable within the free-only constraint.

No deployments, account upgrades, cloud changes, model installation, paid API calls, or media processing were performed in this research handoff.
