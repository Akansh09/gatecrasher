# gatecrasher

Your agent takes instructions from anyone who shows up. This measures how often.

> **Status: early.** Nothing to install yet.

## The problem

An LLM has no way to tell whose instruction is whose.

Your task and the webpage it just read arrive as one undifferentiated stream of text.
There is no equivalent of a prepared statement — no protocol-level boundary that says
*this part is the instruction, that part is only data*.

So a webpage can hand your agent an instruction, and the agent has no invitation to
check. That is indirect prompt injection. It does not need to hide. It only needs the
model to never ask who is speaking.

## What this will be

A benchmark, not a scanner:

- **Controlled pages** carrying payloads — hidden HTML, off-screen text, alt
  attributes, comments
- **Frozen page states**, so runs are deterministic and offline. Testing against a
  live site measures its uptime, not your agent.
- **Attack Success Rate over N runs** — not a single pass/fail. Agents are
  non-deterministic; surviving one run proves nothing.
- **A regression gate** — change the model, the prompt, or the defense, and see
  whether ASR actually moves.

## Why a benchmark and not a scanner

Scanners already exist and are good: [garak](https://github.com/NVIDIA/garak),
[promptfoo](https://github.com/promptfoo/promptfoo),
[PyRIT](https://github.com/Azure/PyRIT), DeepTeam.

What is thinner on the ground is a maintained, runnable measurement harness aimed at
**browser agents** specifically. Most of that work — WASP, AgentDojo, InjecAgent,
IPI-proxy — currently lives in papers rather than in tools you can put in CI.

## License

Apache-2.0
