# Architecture

## Intent

The system was designed as a local-first assistant for Windows that can operate through voice, desktop UI, and remote messaging while remaining useful for real daily work.

## High-Level Flow

`Microphone -> STT -> Intent Router -> LLM or Deterministic Action -> TTS -> Speaker`

Additional entry points:

- desktop HUD
- Telegram remote control
- text/debug mode

## Main Runtime Areas

## UI Layer

The desktop layer acts as the operator console. In the private project, the stable runtime is a `tkinter` HUD and an experimental alternative exists in Qt.

Responsibilities:

- show system state
- collect direct user input
- display logs and telemetry
- expose manual controls for wake, Telegram, and diagnostics

## Assistant Layer

This is the orchestration center.

Responsibilities:

- receive transcribed input
- choose between direct action and model reasoning
- invoke memory, profile, and activity logging
- produce visible and spoken responses

## Voice Layer

Responsibilities:

- microphone capture
- local or hybrid speech-to-text
- local-first text-to-speech
- handling overlap, timing, and audio device constraints

## Action Layer

Responsibilities:

- file and folder actions
- browser automation
- desktop automation
- screenshots
- PowerShell execution under controlled flows
- Google Workspace operations

## Reliability Strategy

The private project moved gradually toward service isolation after observing that audio, wake-word detection, tray integration, and desktop runtime concerns can destabilize a single-process app.

Current direction:

- keep HUD stable first
- move fragile services behind process boundaries
- prefer safe startup over aggressive auto-start in packaged builds

## Packaging Reality

Running from a Python environment and running as a frozen executable behave differently. The public architecture notes reflect that this project required explicit work around:

- initialization order
- background service startup timing
- native library loading
- tray and window lifecycle issues
- TTS dependency failures

## Future Direction

The recommended product-grade evolution is to isolate:

- UI process
- wake and audio process
- action execution process
- Telegram process
- optional memory or scheduling services
