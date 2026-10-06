## Alexandr Fedoseev

Senior frontend engineer (Vue, TypeScript, Canvas). Since June 2026 I design and run an
autonomous development system on my own server: a team of LLM agents that carries tickets from
backlog to a merged pull request, with a human approving only what needs a human.

**In production this week**

- 18 agents and 26 deterministic tools in active service, running unattended
- 1,151 LLM calls in the last 7 days — 1,150 ok, 1 timeout
- 89% of 446M input tokens served from the prompt cache; ~$990/week API-equivalent, metered
  per individual call
- 36 tickets taken through the pipeline; 12 agent failures diagnosed, fixed and verified by a
  repair agent before they reached me
- 20,923 append-only audit records; 41 engineering rules, each one traced to a recorded incident

One recent ticket went from Todo to a merged pull request in 24 agent calls for $6.45.

**What I learned building it**

Prompts are the smallest part of the problem. What makes it work is structure: a declared
output contract on every call, validated in deterministic code; retry with the deviation fed
back inside the same session; three strikes treated as a failure of the system rather than the
model; default-deny tool fencing; input and output logged with full transcripts and cost; and
an explicit, reasoned "cannot do" path so a refusal is a result instead of a crash.

**Before agents**

Ten years in frontend and graphics. A Canvas-based narrative graph editor at Articy — panning,
zooming, node connection, kept fast on large story graphs. Vue and TypeScript on a commercial
localization platform, where in 2026 I used these agent workflows to deliver 511 commits,
including a large WCAG accessibility pass.

**Published**

[**@taleswords/lib-ui**](https://github.com/taleswords/taleswords-lib-ui) — a Vue 3 component
library and design system. 43 components, 39 test files including Playwright interaction
contracts, token-driven styling, dark mode, WCAG AA. MIT, on
[npm](https://www.npmjs.com/package/@taleswords/lib-ui).

**Coming next**

The agent system itself is private. What I can extract from it is coming here — the agent-call
wrapper (contracts, fencing, per-call cost logging), and a public evaluation of how reliably
different models obey a declared output contract under real work, measured from my own logs.

Mönchengladbach, Germany · [LinkedIn](https://www.linkedin.com/in/a1jyex)
