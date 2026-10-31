# DocStar Product Hunt launch kit

Draft. Every claim below is already published on docstar.io. Items marked **TODO** need a decision from the team before launch.

## Listing fields

**Name:** DocStar

**Tagline (max 60 characters), chosen:** `API docs your agent writes, every agent can use` (47)

Alternatives considered: `One prompt turns your code into API docs, MCP and CLI`, `Your agent writes the docs. Every agent can use them.`

**Short description (max 260 characters)**
Paste one prompt into your coding agent. It documents your API from your code, and DocStar publishes the docs, llms.txt, a hosted MCP server and a CLI, all from one source. (about 170)

**Topics:** Developer Tools, API, Artificial Intelligence, Documentation (check which exist at submission)

**Links**
- Website: https://docstar.io/producthunt (tracks Product Hunt visitors)
- npm: https://www.npmjs.com/package/docstar-cli
- Live example: https://docs.msg91.com (MSG91's API docs, running on DocStar)

**Pricing line:** Free to start. Pro is $25 a month with 10 members included.
**TODO:** launch offer. None is published, so none is promised on the page.

## Maker first comment (post at launch, in your own voice)

> Hi Product Hunt, I'm <name> from the DocStar team.
>
> Most API docs are written for people to read, but more and more of the readers are agents. An agent can't use a screenshot or a half-updated page. It needs clean text, the exact contract and a way to call the API.
>
> DocStar starts from that. You paste one prompt into Claude Code, Cursor or Codex, opened in your API's repo. The agent reads your routes and saves the docs as drafts. You review and publish, and the same source becomes:
> - a docs site people can search
> - llms.txt and a markdown twin of every page, for models
> - a hosted MCP server, so agents can search your docs and call your API
> - a CLI where every endpoint is a command
>
> You can try it without signing up: MSG91's API docs run on DocStar. `curl https://docs.msg91.com/llms.txt`, or `npx docstar-cli init msg91`.
>
> I'd love to hear which agent you try it with and where it gets stuck. We read every reply.

## Gallery (5 images, 1270x760)

1. Hero: "Your agent writes the docs. Every agent can use them." with the prompt.
2. The agent run: prompt, routes read, drafts created, then docs, MCP and CLI live.
3. One source, every format: docs site, llms.txt, MCP, CLI, OpenAPI export.
4. MCP in Claude: `claude mcp add` and the tools list.
5. The CLI in a terminal: `npx docstar-cli msg91 ...`.

## Demo video (60 to 90 seconds)

| Time | Shot |
|---|---|
| 0:00 | Problem: a coding agent guessing at an API from stale docs |
| 0:10 | Copy the prompt on docstar.io |
| 0:20 | Paste into Claude Code in a sample repo; the agent reads routes and shows the plan |
| 0:40 | Review the drafts in DocStar and publish |
| 0:55 | Show the docs site, `llms.txt`, then call one endpoint through the MCP |
| 1:10 | The CLI command for the same endpoint |
| 1:20 | End card: docstar.io/producthunt |

**TODO:** record this after the full signup-to-first-docs run succeeds without surprises.

## Launch day

- Launch Tuesday to Thursday; the post goes live at 12:01am PT.
- Hunter: **TODO**
- Post the maker comment in the first minutes, then answer every comment the same day.
- Share the page link, not a "please upvote" request.
- Watch signups, copy-prompt clicks and errors; those are the two conversion events the site tracks.

## Likely questions, with answers from published facts

- **Do I need an OpenAPI file?** No. The agent reads your routes. You can also import OpenAPI, Swagger or Postman.
- **Will it publish without asking?** No. The agent saves drafts and you publish.
- **Which agents work?** Claude Code, Cursor, Codex, VS Code, Windsurf, Claude Desktop, ChatGPT, any MCP client.
- **Is there a free plan?** Yes.
- **Can I use my own domain?** Yes, on the docs and the MCP server.

## Before launching

- [ ] Home and `/api-docs` copy published in Admin and checked live
- [ ] Full flow run end to end: signup, prompt in an agent, MCP connect, one endpoint called
- [ ] MSG91 showcase cleaned up (empty `overview` module, `subaccount-1` and `oneapi-1` slugs)
- [ ] `docstar-cli` release with the clean build, when the next version goes out
- [ ] Launch offer decided, hunter confirmed, video recorded
