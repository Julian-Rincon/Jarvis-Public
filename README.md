# JARVIS Ironman Showcase

Portfolio repository for a private Windows voice assistant project inspired by the JARVIS interaction model.

This public repository is intentionally limited. It documents the product direction, architecture, engineering decisions, and implementation scope without exposing the private source code, credentials, personal data, or operational automation used in the real project.

## Why This Repository Exists

The original project includes:

- proprietary implementation details
- local automation flows tied to a real workstation
- personal profile and behavioral context
- private API configuration
- integration tokens and local environment assumptions

Because of that, this repository is published as a professional showcase instead of an open-source code release.

## Project Summary

JARVIS Ironman is a local-first assistant for Windows focused on practical daily use, not just chat.

Core capabilities implemented in the private version:

- voice conversation through microphone and spoken responses
- desktop HUD for direct local interaction
- local or hybrid STT and local TTS
- local LLM backend through Ollama
- system actions on apps, files, folders, browser, screenshots, and PowerShell
- remote operation through Telegram
- early Gmail and Google Calendar integration
- persistent memory, activity logs, and user profile context
- background wake-word flow and follow-up conversation handling

## Engineering Scope

This project was built as a real systems integration effort across:

- Python application architecture
- Windows desktop runtime behavior
- local audio capture and playback
- speech-to-text reliability under real microphone conditions
- text-to-speech orchestration and fallback handling
- local model integration with Ollama
- browser and desktop automation
- process isolation for fragile background services
- packaging and debugging of a frozen Windows executable

## Architecture Overview

High-level execution flow:

`Microphone -> STT -> Intent Routing -> LLM/Action Layer -> TTS -> Speaker`

Main subsystems in the private implementation:

- `assistant`: orchestration across conversation, actions, memory, and voice
- `audio`: recording, playback, device handling
- `stt`: local and resilient hybrid transcription pipeline
- `tts`: local-first synthesis with fallback behavior
- `actions`: execution layer for system, browser, file, and Google actions
- `desktop HUD`: main operator interface for the Windows app mode
- `telegram`: remote control channel
- `memory/profile`: persistent context and activity history
- `service IPC`: process separation for unstable background workloads

Additional architecture notes are in [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Key Technical Decisions

- Local-first design to reduce cloud dependency and improve privacy.
- Stable `tkinter` desktop interface kept as the operational default after real-world testing.
- Separate worker processes introduced for wake-word and Telegram services to reduce UI crash surface.
- Safe-mode startup used in packaged builds to avoid bringing up fragile background services too early.
- Sensitive actions routed through confirmation flows.
- Persistent memory kept explicit and inspectable rather than hidden in opaque infrastructure.

More detail is in [docs/DECISIONS.md](docs/DECISIONS.md).

## Public Repository Scope

Included here:

- product and engineering overview
- architecture notes
- selected technical decisions
- risk and security posture
- roadmap

Not included here:

- source code
- packaged executable
- API keys, OAuth credentials, or tokens
- local machine paths and personal profile data
- full automation logic
- prompt assets and operational tuning

## Security and Privacy Posture

The private project handles sensitive local context and personal workflow data. For that reason, the public repository is documentation-only by design.

See [docs/SECURITY.md](docs/SECURITY.md) for the rationale.

## Roadmap Snapshot

- continue hardening the Windows desktop runtime
- deepen service isolation beyond wake-word and Telegram
- expand Google Workspace workflows
- improve memory and operator visibility
- package a cleaner demo path for portfolio presentation

Full roadmap: [docs/ROADMAP.md](docs/ROADMAP.md)

## Screenshots and Demo Material

This repository includes an `assets/` folder for curated screenshots or short demo captures. Add only sanitized media that does not expose local secrets, device names, personal mail, or calendar content.

## For Employers or Reviewers

This repository is meant to demonstrate:

- product thinking
- practical systems engineering
- desktop automation work on Windows
- LLM integration beyond a chat interface
- debugging discipline in a messy real-world environment

If you want a guided walkthrough of the private implementation, that should be done as a controlled live review rather than by publishing the codebase.

## License

No open-source license is granted for the private implementation behind this showcase. All rights remain reserved by the author unless explicitly agreed otherwise in writing.
