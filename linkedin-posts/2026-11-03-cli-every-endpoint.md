# DocStar LinkedIn draft - 2026-11-03

Topic: (5) CLI: every endpoint as a command (docstar-cli)

## Post

What if every endpoint in your API docs was also a command you could run?

With docstar-cli, a published DocStar docs site turns into a terminal tool. The structure is always the same: collection, then module, then endpoint.

docstar-cli msg91 slack send-message-1 --message "hello"

There is nothing to generate or download first. The CLI reads the docs when you run the command, so an edit to the docs shows up immediately. If a required parameter or your API key is missing, it asks you for it, then calls the API and prints the response.

You can also register a collection to get a shortcut command and tab completion for modules and endpoints.

The commands come from the same collection that powers your public docs, so there is no separate CLI to build or keep in sync.

Try it: https://docstar.io

#CLI #APIDocumentation #DeveloperTools #DevEx #DocStar

## Sources checked
- /Users/swayammaheshwari/Documents/Development/Docstar/CLAUDE.md
- docstar-cli/README.md (concepts, run any collection with no setup, init/alias, prompts for missing params, tab completion)
