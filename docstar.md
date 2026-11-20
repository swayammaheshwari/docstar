# DocStar docs sync

`api-docs/` (OpenAPI) syncs to DocStar on every push, and so does `docs/` (Markdown) when the repo has the DocStar Markdown workflow. Update them in the same change as the code.

## What to document

Only endpoints your users call: the ones your frontend or app uses, and your public API.

**NEVER add a private, internal or admin API. No exceptions.** These docs are public, so anything you add is visible to every user. This bans admin and back-office routes, cron jobs, webhooks that other services call and service-to-service routes, and any internal detail in a description (secrets, internal hostnames, table or queue names, class names, security weaknesses). If you cannot confirm the frontend calls an endpoint, do not add it.

## When an endpoint changes

- **Add:** a new operation with a unique `operationId` and `x-docstar-published: true`.
- **Change:** edit it in place. Never change its `operationId`.
- **Remove:** delete the operation.
- Keep `description`, `parameters`, `requestBody` and `responses` (with examples) accurate.

## Structure

```text
api-docs/
├── docstar.json          optional: module order, { "order": ["payments", "users.yaml"] }
├── payments/             a folder is a module
│   ├── layout.json       optional: module name, description and overview
│   └── charges.yaml      a complete OpenAPI file
└── users.yaml            a file on its own is a one-file module
docs/                     only with the Markdown workflow
├── getting-started.md    a page
└── guides/               a section; guides/page.md is its own page
```

## `api-docs/`

- Each folder is a module, and each file in it is a complete OpenAPI file (`.yaml`, `.yml` or `.json`). A file on its own is a one-file module. A folder inside a module is a sub-module (a subpage), at any depth.
- Always set `x-docstar-published: true` on every operation, or the endpoint stays a draft (unless the module's `layout.json` sets `"defaultPublished": true`).
- To fill a module that already exists in DocStar instead of creating a new one, add a `layout.json` to the folder: `{ "adopt": "<module name>" }`.

## One or two environments

By default one collection gets every push. To keep a **dev** and a **prod** copy of the same API docs, use two DocStar collections, one per branch:

| Branch | Collection |
| --- | --- |
| dev branch (for example `master`) | dev collection |
| prod branch (for example `prod`) | prod collection |

1. Create both collections and, in each, create the modules named in every `layout.json` `adopt` (an `adopt` that matches no module is skipped, so an empty collection syncs nothing).
2. In every spec use `servers: - url: "{{BASE_URL}}"` instead of a hardcoded host.
3. Give each collection an environment with a `BASE_URL` variable, including the scheme: `https://dev-api.example.com` on the dev collection, `https://api.example.com` on the prod one.
4. Generate the workflow with both collections: `GET /p/generate-docstar-openapi-workflow/<prodCollectionId>?branch=<prodBranch>&devBranch=<devBranch>&devCollectionId=<devCollectionId>`. A push to the dev branch then syncs the dev collection, and a push to the prod branch syncs the prod collection. Leave `devBranch` and `devCollectionId` out for a single collection.
5. Add `"defaultPublished": true` to each `layout.json` so new endpoints are published, not drafts.

A sync only sends files changed in that push, so merge dev into prod with a merge commit or rebase. To seed a new collection with every spec, run the workflow by hand (`workflow_dispatch`).

## Documenting an existing codebase's APIs (first-time setup)

Follow these steps when a repo has routes but no `api-docs/` yet. Skipping them produces generic docs that have to be redone.

1. **Read the code, not just the routes.** For every endpoint open the router, its middleware (auth header, permission strings, validation) and the controller/service. Take parameters, body fields, filters, status codes and response shapes from there. A route file alone gives only the path and method.
2. **Use the branch the user names** (for example `production`) as the source of truth. Routes differ between branches; check out or read that branch before writing.
3. **Check how a reference project structures its docs** (for example `hitman-api/api-docs/`) before writing, or ask the user. Do not invent a layout.
4. **One file per endpoint**, one operation per file, named in kebab-case (`get-sms.yaml`). Do not group several operations into one file and do not generate specs from a script with placeholder content.
5. **One folder per module directly inside `api-docs/`** (`api-docs/analytics/`, `api-docs/logs/`). Do not wrap all modules in an extra parent folder or put files flat in `api-docs/` unless the user asks for it.
6. **Add a `layout.json` to every module folder:** `name`, `description`, `published: true`, `defaultPublished: true`, and `content` listing each endpoint as `* **Summary** — METHOD https://<host><path>`. Leave out `adopt` unless the module already exists in the collection.
7. **Spec shape:** `info.title` is the module name, `info.x-docstar-published: true`, `servers: - url: "{{BASE_URL}}"`, a kebab-case unique `operationId`, `x-docstar-published: true` on every operation, a description that lists `Body fields:` / `Query params:`, real parameter descriptions, and request and response examples that match the code.
8. **Regex or positional routes** (for example `/^\/(sms|otp)/`): document each as a named path segment or one file per service where the filters differ.
9. **Scope:** skip admin-only, private/internal and job/cron endpoints unless the user says otherwise. Ask when unsure which routes count as private.
10. **Dev and prod collections:** if the generator ignores `devBranch` / `devCollectionId`, generate one workflow per collection (`GET /p/generate-docstar-openapi-workflow/<collectionId>?branch=<branch>`), save them as `docstar-api-docs.yml` and `docstar-api-docs-dev.yml`, and give each a distinct `name:`. The generated file starts with a blank line, so edit the name with care and do not leave two `name:` keys.
11. **Agent rules:** add to the repo's `AGENTS.md` that any new, changed or removed endpoint requires reading `docstar.md` and updating `api-docs/` in the same change. Keep `docstar.md` at the repo root.
12. **Verify before finishing:** every operation has `x-docstar-published: true`, `operationId`s are unique, every module has a `layout.json`, and no empty folders are left.

## `docs/`

Folders are sections, `.md` files are pages, and a folder's `page.md` is that section's own page. Every file starts with front matter:

```markdown
---
title: Getting Started
description: Short summary.
published: true
---
```

## Rules

- Use only `a-z`, `0-9`, `-` and `_` in file and folder names.
