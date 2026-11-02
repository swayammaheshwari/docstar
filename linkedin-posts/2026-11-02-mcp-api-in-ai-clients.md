# DocStar LinkedIn draft - 2026-11-02

Topic: (4) MCP: your API usable from Claude, ChatGPT, Cursor

## Post

Your users are already asking an AI assistant how to call your API. Can it actually call it?

In DocStar, a published API collection gets an MCP URL alongside its public docs site. Point an AI client such as Claude, ChatGPT or Cursor at it, and the endpoints you documented become tools the assistant can use.

There is no separate integration to build or keep in sync. The tools come from the same collection that powers your docs, so when you update an endpoint, the docs and the MCP tools come from the same source.

If you set up sign-in (OAuth) for your DocStar MCP server, your users sign in once and the assistant works with their own access.

Documenting an API well is now also how you make it usable from an AI client.

See how it works: https://docstar.io

#MCP #APIDocumentation #DeveloperTools #AI #DocStar

## Sources checked
- /Users/swayammaheshwari/Documents/Development/Docstar/CLAUDE.md
- docstar-cli/README.md (MCP section: endpoints as MCP tools, optional OAuth sign-in for the DocStar MCP server)
- docStarWebsite/src/content/site.ts (MCP server page and quickstart)
- DocStar MCP server instructions (collection gives public docs, MCP URL for Claude, ChatGPT, Cursor and others)
