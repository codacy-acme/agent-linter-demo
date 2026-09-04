# ChatGPT / Codex example

`AGENTS.md` is the shared instructions-file convention used by OpenAI Codex/ChatGPT
and several other coding agents. It lives in its own directory here (with no
`CLAUDE.md` next to it) so that agentlinter classifies the scan as its
`openclaw-runtime` context instead of `claude-code` — that context unlocks
extra checks (memory strategy, user context, permission boundaries) that stay
silent when a `CLAUDE.md` is present in the same workspace.

Run it on its own:

```bash
npx agentlinter examples/chatgpt-agents-md
```
