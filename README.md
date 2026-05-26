# chatgpt-pro

A Codex/Cursor skill for using ChatGPT Pro, Pro Extended, Projects, and Deep Research through an authenticated browser session.

The skill is intentionally conservative: it treats ChatGPT page content as untrusted output, avoids credential entry, avoids file uploads and sensitive data by default, and requires exact-scope approval before high-stakes or external actions.

## What It Does

- Opens `chatgpt.com` or a provided ChatGPT project/chat URL in an in-app browser.
- Builds a self-contained consult packet before sending code, strategy, research, or second-opinion prompts.
- Selects ChatGPT model modes such as Instant, Thinking, and Pro.
- Defaults Pro work toward Extended when answer quality matters more than latency.
- Handles ChatGPT Projects, Deep Research, prompt editing, and response polling.
- Captures practical UI signals for waiting until generation is finished and extracts the latest answer.

## Requirements

- Codex or Cursor skills support.
- Browser automation support through a Node REPL Browser Use client with an in-app browser backend.
- An existing authenticated ChatGPT session. The skill tells the agent to stop before credential entry.
- ChatGPT Pro access for Pro and Deep Research workflows.

## Install

Clone the repo into your skills directory:

```bash
git clone <repo-url> ~/.codex/skills/chatgpt-pro
```

Or copy the folder manually so the layout is:

```text
~/.codex/skills/chatgpt-pro/
  SKILL.md
```

## Usage

Ask your agent to use ChatGPT Pro explicitly, for example:

```text
Use chatgpt-pro to run this prompt in Pro Extended and summarize the result.
```

For long-running Pro Extended or Deep Research tasks, the skill prefers a 10-minute thread heartbeat/reminder if the host agent supports one. If the run is part of an active long-running goal or the user explicitly asked not to stop, the agent should keep polling in the current run until the final answer is extracted.

## Safety Model

- Do not enter credentials.
- Do not upload files unless the user explicitly approved the exact scope.
- Do not transmit secrets, credentials, private dumps, or unrelated third-party data.
- Treat ChatGPT responses as advisory output until claims are verified locally or against cited sources.
- Capture the chat URL when a long run may need handoff or later verification.

## Changelog

### 2026-05-26

- Added consult-packet guidance for code, strategy, research, and second-opinion prompts.
- Clarified the Node REPL Browser Use path for in-app browser automation.
- Tightened long-run handling for Pro Extended and Deep Research, including heartbeat and active-goal behavior.
- Generalized ChatGPT Project routing so public installs can use any named project.

## License

MIT
