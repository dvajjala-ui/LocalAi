# LocalAi

A personal AI video editor that runs on an Oracle Cloud server and is used through a browser.

Provide video, images, and audio, then get help organizing media, synchronizing recordings, matching visuals to narration or music, creating captions, and producing an editable draft. Changing a person's lip movements to new speech is also a requested feature.

## Current status

Research and requirements only. No application has been implemented or deployed. The existing Oracle account, VM shape, free allocation, and performance have not been inspected.

The user wants everything free and does not have a local machine available for the processing. Oracle is the intended compute host; a local GPU or local model installation is not a requirement.

## Start here

- [Project brief and next steps](docs/PROJECT_BRIEF.md)
- [Research findings and sources — 30 October 2026](docs/RESEARCH_2026-10-30.md)
- [Conversation record — 30 October 2026](docs/CHAT_2026-10-30.md)

## Proposed starting point

A browser interface backed by FFmpeg, whisper.cpp, and a small quantized Qwen vision-language model. Start with short, queued jobs. Benchmark lip regeneration separately before deciding whether it belongs on the Oracle CPU worker.

This is a proposed stack, not a ready-to-install professional editor or a promise that every requested feature will perform acceptably on Oracle Free. Free software and free hosting capacity are separate constraints.

## First acceptance milestone

Use a 30–60-second sample project to prove upload, transcription, camera/microphone alignment, visuals matched to narration, editable preview, and final export. Evaluate a separate short lip-sync sample for visible artifacts and processing time.
