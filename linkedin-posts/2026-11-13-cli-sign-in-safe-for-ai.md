# DocStar LinkedIn draft - 2026-11-13

Topic: (5) CLI: every endpoint as a command (docstar-cli) (sign-in and API keys, safe for AI assistants angle)

## Post

A CLI that an AI assistant runs has to fail clearly, not wait on a prompt nobody will answer.

That shaped how docstar-cli handles sign-in and API keys. Every command follows collection, module, endpoint, and before it calls the API, the CLI checks what that endpoint needs: your sign-in, an API key, or nothing.

In a terminal, it asks for anything missing. Not signed in? It offers to open the sign-in page. Run by an AI assistant or in CI, it stops instead, with exit code 4 and the exact command that fixes it.

A few more details:
- docstar-cli auth status <collection> shows what a collection needs and whether it is set up.
- Sign-in tokens stay on your machine, readable by you only, and are refreshed automatically.
- API keys come from a flag or a key you saved. The CLI never reads your environment or .env.

All of this comes from the same published collection that powers your docs site and MCP URL.

Try it: https://docstar.io

#CLI #APIDocumentation #DeveloperTools #AIAgents #DocStar

## Sources checked
- /Users/swayammaheshwari/Documents/Development/Docstar/CLAUDE.md
- docstar-cli/README.md (collection -> module -> endpoint, Sign-in and API keys, auth status, exit codes, never reads environment or .env)
- docstar-cli/src/lib/run.ts (EXIT_CREDENTIAL_MISSING = 4, prompts only in a TTY and not in CI)
- docstar-cli/src/lib/http.ts and src/lib/auth.ts (sign-in token refresh)
- docstar-cli/src/lib/credentials.ts (files written with mode 0600)
- docstar-cli/src/commands/auth/status.ts
