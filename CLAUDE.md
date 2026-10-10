# CLAUDE.md

## Model routing

Choose models by delegating with the Agent tool (you can't switch your own model). For each request, decide who does the work:

- **Planning, design, debugging, root-cause analysis, code review, error checking:** do it yourself, or spawn an Agent with `model: "opus"`.
- **Writing or editing code once the approach is clear:** write small, local changes yourself. Delegate only when the change spans several files or is large or mechanical (roughly 100+ lines): spawn an Agent with `model: "haiku"` and a self-contained prompt (files, exact change, acceptance check), or `model: "sonnet"` if the change is subtle.
- **Searches and lookups:** always spawn an Explore Agent with `model: "haiku"` for anything broader than reading a known file.
- **After a haiku agent writes code,** review its result yourself or with an opus Agent before reporting done.

Why: delegating costs a brief, a cold start that re-reads files, and a review. That beats writing it yourself only for big or read-heavy work. Your own main conversation stays on one model so its prompt cache is never reset.
