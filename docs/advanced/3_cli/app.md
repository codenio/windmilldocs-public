---
description: How do I list and push apps using the Windmill CLI?
---

import DocCard from '@site/src/components/DocCard';

# Apps

## Listing apps

The `wmill app` list command is used to list all apps in the remote workspace.

```bash
wmill app
```

## Pushing an app

Pushing an app to a Windmill instance is done using the `wmill app push` command.

```bash
wmill app push <file_path>
```

### Arguments

| Argument    | Description                       |
| ----------- | --------------------------------- |
| `file_path` | The path to the app file to push. |

### Examples

1. Push the app located at `./my_app.json`.

```bash
wmill app push ./my_app.json
```

## Full-code app commands

The CLI provides additional commands for [full-code apps](/docs/full_code_apps):

### Create a new full-code app

```bash
wmill app new
```

Interactive wizard to scaffold a full-code app with React, Svelte or Vue.

### Start the dev server

From the app directory:

```bash
wmill app dev
```

Starts a local development server with hot reload and WebSocket backend. Options: `--port`, `--host`, `--entry`, `--no-open`.

### Bundle an app without deploying it

```bash
wmill app bundle [app_folder] --out <dir>
```

Runs the same build `wmill app push` runs, but writes `bundle.js` and `bundle.css` to a directory instead of deploying. The folder defaults to the current directory and the output to `<app_folder>/dist`. Use `--no-minify` to skip minification.

This is also the build behind the [source-deploy API endpoints](/docs/full_code_apps/deployment#deploy-from-sources-via-the-api), so an app deployed from sources through the API is compiled exactly as the CLI and the editor compile it.

### Generate lock files

Generate `.lock` files for backend runnables with dependencies using the [`wmill generate-metadata`](./generate-metadata.md) command:

```bash
wmill generate-metadata
```

To only update app lockfiles, use:

```bash
wmill generate-metadata --skip-scripts --skip-flows
```

Options: `--yes`, `--dry-run`, `--default-ts`.

:::info Legacy command
Prior to the unified command, this was done with `wmill app generate-locks`. This command is now deprecated but still works.
:::

### Generate agent documentation

From the app directory:

```bash
wmill app generate-agents
```

Generates `AGENTS.md` and `DATATABLES.md` for AI coding agent context.

<div className="grid grid-cols-2 gap-6 mb-4">
	<DocCard
		title="Full-code app CLI workflow"
		description="Complete guide to developing full-code apps with the CLI."
		href="/docs/full_code_apps/cli_workflow"
		color="orange"
	/>
</div>

## Remote path format

```js
<u|g|f>/<username|group|folder>/...
```
