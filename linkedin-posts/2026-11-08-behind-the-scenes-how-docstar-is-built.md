# DocStar LinkedIn draft - 2026-11-08

Topic: (10) A behind-the-scenes note on how DocStar is built

## Post

A behind-the-scenes look at how DocStar is put together.

It is a small set of separate projects, each doing one job:

- A Next.js and React app for writing and publishing.
- An Express and TypeScript API with Postgres for documents, versions, permissions and publishing.
- A separate real-time service built on Yjs and Hocuspocus for live editing and versioning.
- docstar-editor, a block and Markdown editor we publish as an npm package.
- docstar-cli, which turns a published docs site into runnable commands.

Keeping collaboration in its own service means live editing never has to share a process with the rest of the API.

One rule we hold on to: collection, then module, then endpoint. The docs site, the CLI command and the MCP tool name all follow that same hierarchy, so one structure serves everyone.

Curious what that looks like in practice? https://docstar.io

#BuildInPublic #DeveloperTools #APIDocumentation #Documentation #DocStar

## Sources checked
- /Users/swayammaheshwari/Documents/Development/Docstar/CLAUDE.md (projects, how pieces connect, hierarchy)
- hitman-ui, hitman-api, doc-rtc, docstar-editor package.json (Next, React, Express, Sequelize, Yjs, Hocuspocus, BlockNote, tsup)
