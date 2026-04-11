# Technical Decisions

## Local-First Inference

The assistant uses a local model backend as the default operating path. This reduces dependence on external quotas and makes the assistant more practical for desktop use.

Tradeoff:

- better privacy and autonomy
- more local complexity around performance and model quality

## Stable UI Over Experimental UI

Although a Qt path was explored, the stable public-facing recommendation remains the `tkinter` desktop HUD because it behaved more reliably on the target Windows machine.

Tradeoff:

- less visually flexible than Qt
- materially better operational stability

## Safe Mode in Packaged Builds

Frozen Windows builds are more fragile than the development runtime. A safe startup path was adopted so the HUD becomes visible before waking background services.

Tradeoff:

- slower activation of secondary features
- lower crash risk during startup

## Deterministic Routing Before LLM

Some user requests map better to direct actions than to free-form model reasoning. A pre-LLM routing stage reduces hallucination risk and improves action reliability.

Examples:

- open app
- take screenshot
- search the web
- read Gmail
- inspect calendar

## Confirmation for Sensitive Operations

Actions that may affect the system or user data should not execute silently. The design includes confirmation flows for high-risk operations.

Examples:

- PowerShell execution
- write operations
- event creation
- automation that changes external state

## Process Isolation

Wake-word detection and Telegram control were moved away from the main desktop process to reduce UI instability.

This reflects a broader design principle:

- keep the interface recoverable
- isolate side effects
- prefer observable state over hidden background behavior
