# CLAUDE.md

## Model routing

Choose models by delegating with the Agent tool (you can't switch your own model). For each request, decide who does the work:

- **Planning, design, debugging, root-cause analysis, code review, error checking:** do it yourself, or spawn an Agent with `model: "opus"`.
- **Writing or editing code once the approach is clear:** spawn an Agent with `model: "haiku"` and a self-contained prompt (files, exact change, acceptance check). Use `model: "sonnet"` if the change is subtle or spans many files.
- **Searches and lookups:** spawn an Explore Agent with `model: "haiku"`.
- **After a haiku agent writes code,** review its result yourself or with an opus Agent before reporting done.

Don't write more than ~25 lines of code yourself; delegate with the model set explicitly. Trivial one-step edits may be done directly.
