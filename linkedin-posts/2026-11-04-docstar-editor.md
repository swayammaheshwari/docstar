# DocStar LinkedIn draft - 2026-11-04

Topic: (6) the docstar-editor block and Markdown editor

## Post

A block-based Markdown editor for React, in a few lines of code.

docstar-editor is an npm package built on BlockNote. Install it, import the styles once, and drop in one component:

<DocstarEditor defaultMarkdown="# Hello" onChange={(markdown) => save(markdown)} />

It works standalone with no login and no server. You write in blocks, and you get Markdown back through onChange.

When you want more, pass a collab config with your Hocuspocus-compatible server details. The editor then syncs edits live over Yjs and shows collaborator cursors and presence.

It is the same editor DocStar uses, published so you can embed it in your own product.

Try it: https://docstar.io

#React #Markdown #OpenSource #DeveloperTools #DocStar

## Sources checked
- /Users/swayammaheshwari/Documents/Development/Docstar/CLAUDE.md
- docstar-editor/README.md (install, standalone usage, collab prop, BlockNote base)
- docstar-editor/package.json (name, version 0.4.4, description)
