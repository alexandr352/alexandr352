## Alexandr Fedoseev

Senior frontend engineer (Vue, TypeScript, Canvas). Since June 2026 I design and run an
autonomous development system on my own server: a team of LLM agents that carries tickets from
backlog to a merged pull request, with a human approving only what needs a human.

**In production this week**

- 23 agents and 33 deterministic tools in active service, running unattended
- 1,920 LLM calls in the last 7 days: 1,918 ok, 1 timeout, 1 error
- 87% of 502M input tokens served from the prompt cache; ~$930/week API-equivalent, metered
  per individual call
- 86 tickets taken through the pipeline since 20 September, 79 of them to Done; 31 agent
  failures sent first to a repair agent's diagnose, fix and verify loop
- 24,895 append-only audit records; 45 engineering rules, each one traced to a recorded incident

A merged ticket takes a median of 51 agent calls and about $26 API-equivalent, from Todo to a
merged pull request.

**What I learned building it**

Prompts are the smallest part of the problem. What makes it work is structure: a declared
output contract on every call, validated in deterministic code; retry with the deviation fed
back inside the same session; three strikes treated as a failure of the system rather than the
model; default-deny tool fencing; input and output logged with full transcripts and cost; and
an explicit, reasoned "cannot do" path so a refusal is a result instead of a crash.

**Open source**

[**hearthwork**](https://github.com/alexandr352/hearthwork) — the core of that system, rebuilt
for anyone with Claude Code. An operator plans each unit of a ticket, a fenced executor does it,
and the operator judges the report against what git shows, never reading the code itself. A
default-deny fence on every tool call, recovery when a session dies, a live work log, and a
spirit you can ask about any unit. Standard-library Python, MIT.

[**hearthwood**](https://github.com/alexandr352/hearthwood) — a read-only companion for product
owners and delivery leads. It reads a Jira Cloud project (through your own sign-in) or a GitHub
board, works out in plain code what is ready, blocked, not moving or duplicated, has Claude read it
once for the part you choose (this sprint, recent work), and learns how you judge from your agree
and disagree. Nothing is ever written to your board. Python, MIT.

[**@taleswords/lib-ui**](https://github.com/taleswords/taleswords-lib-ui) — a Vue 3 component
library and design system. 43 components, 38 test files including Playwright interaction
contracts, token-driven styling, dark mode, WCAG AA. MIT, on
[npm](https://www.npmjs.com/package/@taleswords/lib-ui).

Coming next: a public evaluation of how reliably different models obey a declared output
contract under real work, measured from my own logs.

**Before agents**

Ten years in frontend and graphics. A Canvas-based narrative graph editor at Articy — panning,
zooming, node connection, kept fast on large story graphs. Vue and TypeScript on a commercial
localization platform, where in 2026 I authored about 600 commits with these agent workflows,
most of them a large WCAG 2.2 AA accessibility pass now in review.

Mönchengladbach, Germany · [LinkedIn](https://www.linkedin.com/in/alexandr352)
