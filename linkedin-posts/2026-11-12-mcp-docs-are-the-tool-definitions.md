# DocStar LinkedIn draft - 2026-11-12

Topic: (4) MCP: your API usable from Claude, ChatGPT, Cursor (angle: your endpoint docs become the tool definitions)

## Post

When an AI assistant calls your API, it only knows what your documentation tells it.

In DocStar, a published API collection gets an MCP URL that works with AI clients such as Claude, ChatGPT and Cursor. Each endpoint you document is exposed as a tool, and its required and optional parameters come from that same documentation.

So a prompt like "send a message on Slack saying hi" can resolve straight to the right endpoint, and the assistant asks the user for any required value it can't infer.

The practical takeaway: clear endpoint names and well-described parameters are no longer just good manners for human readers. They decide whether an assistant picks the right call.

There is no second integration to maintain. Fix the docs and the tools follow, because both come from one collection.

Try it with your own API: https://docstar.io

#MCP #APIDocumentation #DeveloperTools #AI #DocStar

## Sources checked
- /Users/swayammaheshwari/Documents/Development/Docstar/CLAUDE.md
- docstar-cli/README.md ("Use from an AI client (MCP)": endpoints become tools, parameters exposed in schema, assistant asks for required values)
- DocStar MCP server instructions (collection gives public docs, MCP URL for Claude, ChatGPT, Cursor and others)
