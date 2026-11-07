# DocStar LinkedIn draft - 2026-11-07

Topic: (9) A practical tip about writing good API or team documentation

## Post

A practical tip for API docs: write each endpoint as if a stranger will run it with no one to ask.

That means four things on every endpoint page:

1. One plain sentence on what it does and when to use it.
2. A name and short description for every parameter, with required ones marked.
3. A real example request and a real example response.
4. The errors people will actually hit, and what to do about them.

It pays off beyond the page. In DocStar, a published endpoint also becomes a CLI command and an MCP tool, and the parameters you document are what people and AI clients see. Vague docs make vague tools.

Before you publish, run your own endpoint from the page, copy-paste only. If you get stuck, so will your readers.

See how it fits together: https://docstar.io

#APIDocumentation #TechnicalWriting #DeveloperExperience #Documentation #DocStar

## Sources checked
- /Users/swayammaheshwari/Documents/Development/Docstar/CLAUDE.md (collection -> module -> endpoint; MCP tool names; CLI commands per endpoint)
- docstar-cli/README.md (endpoints become commands, `--help` shows flags, CLI asks for missing parameters)
