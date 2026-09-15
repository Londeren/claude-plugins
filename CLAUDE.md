# CLAUDE.md

Repository-wide guidance for Claude Code. Each plugin's own editing rules live in a separate file under `docs/`, imported below; read the one for a plugin before changing anything inside its directory.

@docs/prompt-writer-editing-rules.md
@docs/book-to-skill-editing-rules.md

## What this is

A plugin marketplace for Claude: `.claude-plugin/marketplace.json` at the root, one entry per plugin. Markdown only, no build, no tests, no dependencies.

This repository holds meta-skills only: skills that build or improve other prompts and skills. A domain skill, one that carries a method taken from a book, a course or an author, lives in [Londeren/bookshelf-skills](https://github.com/Londeren/bookshelf-skills), one plugin per skill, with its build pipeline next to it. Here it gets a marketplace entry with a `git-subdir` source, a row in the root README table and its install routes in the root README, nothing else.

Only what lives inside a `plugins/<name>/` directory ships to users. `docs/`, `tmp/`, this file and the root README never do.

Plugins in the repository:

- `plugins/prompt-writer/` - a methodology for writing LLM prompts. Editing rules: [docs/prompt-writer-editing-rules.md](docs/prompt-writer-editing-rules.md).
- `plugins/book-to-skill/` - turns a Markdown knowledge source into a generated Claude skill. Editing rules: [docs/book-to-skill-editing-rules.md](docs/book-to-skill-editing-rules.md).

## Adding a plugin

A meta-skill in this repository:

1. `plugins/<name>/` with `.claude-plugin/plugin.json`, `skills/<skill>/SKILL.md`, `README.md`, `LICENSE`.
2. An entry in the `plugins[]` array of `.claude-plugin/marketplace.json`.
3. `docs/<name>-editing-rules.md` if the skill needs its own editing rules, imported from this file and listed above.
4. A row in the plugin table of the root README.

A domain skill is built in bookshelf-skills by that repository's own rules. Here it takes steps 2 and 4 plus its install routes in the root README, and its marketplace entry points into the other repository:

```json
"source": {
  "source": "git-subdir",
  "url": "https://github.com/Londeren/bookshelf-skills.git",
  "path": "plugins/<name>"
}
```

Do not create the directory before the skill has real content. The skills.sh CLI discovers skills by walking the repository for `SKILL.md` files, not by reading marketplace.json, so a placeholder shows up in the public listing the moment it is pushed.

Editing rules never live inside `plugins/<name>/`. Everything there ships, and the skills.sh route installs into `.agents/skills/<name>/` inside the user's own project, where a stray CLAUDE.md would be loaded as their nested project instructions.

## Skill layout inside a plugin

A skill lives in `plugins/<plugin>/skills/<skill>/SKILL.md`, never at the plugin root. Claude Code documents a fallback where a root `SKILL.md` is loaded as the plugin's single skill, and locally it works, but the claude.ai loader does not implement that fallback: it mounts `/mnt/skills/plugins/<plugin>:<skill>/` and takes the skill name from the folder under `skills/`. With no `skills/` directory the plugin installs, reports itself as installed, and exposes zero skills. `claude plugin validate` passes either way and will not catch this.

Consequence for the manual-copy install route in the root README: it names the skill folder, not the plugin directory.

## No cross-plugin runtime references

A skill may not read files from a sibling plugin: users install plugins one at a time, and a path like `../other-plugin/reference/rules.md` resolves to nothing on their machine. When two skills need the same methodology, either restate the needed part inside each one, or have one skill recommend the other as a separate step in its own output.

## docs/

Flat and shared across plugins. Specs, plans, decisions and evidence live under `docs/superpowers/`; the plugin a document belongs to is named in its filename and in its opening lines, which is what makes a flat directory readable. Historic documents keep the paths and the repository name that were true when they were written; do not retrofit them.

## Style

No em dashes in prose, in the skills or in the meta documents.

## tmp/

In .gitignore, holds local source transcripts of system prompts; specs under `docs/superpowers/specs/` reference them by line number. They are not checked into the repository; when working on those specs, get the files from Sergey if they are not present locally.

## Publication

Two distribution channels are live and need no approval: the GitHub plugin marketplace and the skills.sh CLI. The root README owns every install route; do not duplicate the commands elsewhere. A plugin README carries only its own two install commands and links back to the root for the rest.

Marketplace name: for a GitHub `owner/repo` source, Claude Code registers the marketplace under the repository owner, `Londeren`, not under the `name` field of marketplace.json. A lowercase name in the manifest produced a marketplace the install command could not find; keep the two in sync. The same mechanic means the repository can be renamed without changing any plugin id.

Platform neutrality: `present_files`, `ask_user_input_v0` and the view tool exist only in claude.ai. Skill text stays neutral about the host unless a specific file names a tool on purpose, in which case its plugin CLAUDE.md says so and the mention must survive any search and replace.

## Checking changes

There are no automated tests. Manifests and packaging are checked with commands, not by eye:

```bash
claude plugin validate .
claude plugin validate ./plugins/<name> --strict
claude --plugin-dir ./plugins/<name> -p "..." --max-turns 1
find plugins -type f | sort
```

The last one guards the packaging boundary: nothing from `docs/` or `tmp/` may appear in that listing, and no CLAUDE.md either. Behavioural checks are per plugin and live in that plugin's editing rules.
