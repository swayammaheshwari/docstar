# DocStar LinkedIn draft - 2026-11-05

Topic: (7) real-time collaboration

## Post

Two people editing the same doc should not mean two copies of it.

In DocStar, a page is one live document. Open it with your team and everyone edits the same thing at the same time. You see each other's cursors, and changes show up as they are typed.

Under the hood, edits sync over WebSocket using Yjs and Hocuspocus. Yjs merges concurrent changes, so nobody has to pick whose edit wins.

Collaboration also feeds versioning. When someone leaves a page after changing it, DocStar saves a new numbered version with who made it. If nothing changed, no version is added. You get history without anyone clicking save.

Access is checked per page with signed tokens, and a page can be opened read-only.

The same collab layer ships in our open docstar-editor package, so you can point it at your own Hocuspocus-compatible server.

See how DocStar works: https://docstar.io

#RealTimeCollaboration #Documentation #Yjs #DeveloperTools #DocStar

## Sources checked
- /Users/swayammaheshwari/Documents/Development/Docstar/CLAUDE.md
- doc-rtc/README.md (real-time collaboration via Hocuspocus/Yjs, versioning, persistence)
- doc-rtc/src/hocuspocus.ts (WebSocket sync, signed per-page tokens, read-only connections, version saved on disconnect)
- doc-rtc/src/db/sequelize.ts (saveVersion: numbered versions, createdBy, skipped when state unchanged)
- docstar-editor/README.md (collab prop, live sync via Yjs, collaborator cursors/presence, Hocuspocus-compatible server)
- docstar-editor/package.json (MIT license)
