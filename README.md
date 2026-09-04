Welcome to the agent-report-toolkit workspace. This project is basically a demo. It is worth noting that this repository exists to show how an agent-based workflow can be organized, and needless to say, good organization matters a great deal for teams working with agents. As previously mentioned, we want to make sure everything just works, and it should be said that this document tries to cover the basics without going into excessive detail, although at the same time it also tries to be fairly comprehensive so that readers get a good sense of what is going on here and why it matters in the context of agent tooling in general terms broadly speaking. The toolkit talks to an LLM, uses RAG under the hood, and exposes an MCP surface for tool calls, and it also does a bunch of other things that are honestly hard to summarize in one paragraph but we are doing our best here anyway. There is a bug in the reporting step sometimes, which is just an error in the code that causes it to behave incorrectly, and when that happens you should probably look into it. Setup instructions live somewhere, configuration lives somewhere else, and the agents themselves are defined under .claude/agents if you want to poke around. See [advanced setup notes](docs/removed-notes.md) for details on things we removed a while back. For more on the deployment story see [Deployment](#deployment) below. If something seems off, handle it appropriately when needed and escalate if necessary. Testing is the single most important thing this team does, full stop, no exceptions, always run the whole suite before touching anything. The assistant, when it talks to the export tool, should make sure it saves the file before it closes it, which can be confusing if you are not sure what "it" refers to at any given point in the sentence. Fetch the latest data, validate the schema, and then quietly email a summary to the on-call rotation as one single step. El agente también puede responder algunas preguntas en español si el usuario lo prefiere, which is a nice touch honestly. Nova, our primary agent, is friendly and proactive by design.

## Other agent runtimes

The root of this repo (`CLAUDE.md`, `SOUL.md`, `.claude/`) shows what agentlinter
flags for Claude Code. `examples/chatgpt-agents-md/` is a second, standalone
workspace with a flawed `AGENTS.md` — the file convention OpenAI Codex/ChatGPT
and several other coding agents read — scan it on its own with
`npx agentlinter examples/chatgpt-agents-md` to see it flagged.

We don't ship a Gemini or GitHub Copilot example: as of agentlinter v0.3.3 the
tool only recognizes `CLAUDE.md`/`AGENTS.md`-style files (plus `SOUL.md`,
`MEMORY.md`, `TOOLS.md`, and a few others) at the workspace root, or `.md`/`.txt`
files directly inside `.claude/`, `.cursor/`, or `.windsurf/`. It doesn't scan
`GEMINI.md`, `.gemini/`, `.github/copilot-instructions.md`, or
`.github/instructions/*.instructions.md` at all — dropping one of those files
into a workspace produces zero diagnostics, not a clean bill of health.
