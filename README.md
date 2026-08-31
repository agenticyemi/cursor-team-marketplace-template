# Acme Engineering

**Acme Engineering** (`acme-engineering`) is Acme's Cursor Team Marketplace. It is a customized copy of the Cursor Fundamentals template: each function gets a small, focused plugin that encodes how Acme actually works. Each plugin contributes the minimum set of rules, skills, agents, and MCP servers needed to raise quality in that function without overlapping with the others.

## Plugins

### Cursor Starter Pack

Engineering baseline that every contributor gets by default. It ships the non-negotiables: code quality and system design rules, a repo-onboarding skill, commit and git hygiene, planning output, and the naming conventions that make markdown files and Cursor agents consistent across the org. The `code-skeptic` and `code-oracle` agents handle critical review and deeper architectural reasoning when a change needs a second set of eyes. Start here; most other plugins assume this one is installed.

### Product Management

Owns everything between "we should build this" and "engineering can execute on it." Use it to draft implementation-ready tickets or work items, summarize a backlog, board, or sprint for a stakeholder update, and stress-test a plan with the `devils-advocate` agent before any code is written. The bundled `mcp.json` shows one tracker integration path; this repo ships Atlassian MCP by default, but teams should replace or remove it to match their stack.

### Design

Covers UX definition and the handoff into code. The `wireframes` and `mockup` skills help teams reason about backend-aware UI states and high-fidelity layouts, `design-schema.md` captures team-specific visual decisions, the `designer` agent handles creative direction and visual exploration, and the `ui-engineer` agent implements approved designs in a way that respects the design intent. The Figma MCP keeps Figma files and code aligned without context switching.

### Technical Writing

The single home for developer-facing prose workflows. Cursor Starter Pack still sets the baseline expectation to document important behavior, while this plugin handles README work, weekly review summaries, and longer-form documentation such as API references and guides. The `readme-hygiene` skill notices when changes should update a README, and the `docs-writer` agent handles substantial developer-facing prose. An optional Notion MCP is included for teams that publish there. Markdown file-naming conventions intentionally live in **Cursor Starter Pack** so naming stays universal rather than docs-specific.

### Testing

Focused specifically on automated test workflows. Cursor Starter Pack still sets the baseline expectation that changed behavior should be tested, while this plugin owns the testing specialists: `write-unit-tests` and `write-e2e-tests` provide narrower authoring workflows, `browser-automation-tests` covers live UI verification with Cursor browser automation, `test-engineer` adds and extends unit and E2E tests that match the project's frameworks and conventions, and `test-runner` executes and interprets the relevant test commands. `mcp.json` is intentionally empty so each team can add CI or vendor MCP servers that fit their stack.

## Repository structure

- `.cursor-plugin/marketplace.json`: marketplace manifest and plugin registry
- `plugins/<plugin-name>/.cursor-plugin/plugin.json`: per-plugin metadata
- `plugins/<plugin-name>/rules`: rule files (`.mdc`)
- `plugins/<plugin-name>/skills`: skill folders with `SKILL.md`
- `plugins/<plugin-name>/agents`: subagent definitions
- `plugins/<plugin-name>/mcp.json`: MCP server configuration for each plugin

## Use this marketplace on your team

Cursor imports a team marketplace by reading `.cursor-plugin/marketplace.json` from a GitHub repository. This repo is already the **fork-and-customize** path: marketplace `name` / `displayName` / `owner` are Acme Engineering, and each plugin lists Acme as the author. Import **this** GitHub URL — not the upstream template — so the dashboard shows Acme's marketplace.

To consume it on the Acme team:

1. In Cursor, go to **Dashboard → Settings → Plugins → Import**.
2. Paste this repo's GitHub URL.
3. Pick access groups and mark each plugin **Required** (auto-installed) or **Optional** (developer choice).
4. Save. If the repo is private, grant the Cursor GitHub app read access when prompted.

What was renamed (the demo):

- Marketplace id: `acme-engineering`
- Display name and owner: **Acme Engineering**
- Plugin authors: **Acme Engineering** (`engineering@acme.example`)

Plugin folder names (`cursor-starter-pack`, `design`, and so on) are unchanged so existing `source` paths keep working. Rename those only if you want new plugin ids in the dashboard.

To rebrand again later, edit `name` (lowercase kebab-case), `displayName`, and `owner` in [.cursor-plugin/marketplace.json](.cursor-plugin/marketplace.json), update `author` in each `plugins/*/.cursor-plugin/plugin.json`, then run `node scripts/validate-template.mjs` before you push.

## Further reading

- [Cursor Plugins documentation](https://cursor.com/docs/plugins) — plugin anatomy (rules, skills, agents, commands, MCP, hooks) and team-marketplace setup.
- [Cursor Marketplace](https://www.cursor.com/marketplace) — officially reviewed plugins you can use as references.
- [cursor/plugin-template](https://github.com/cursor/plugin-template) — minimal starter for building a single plugin or multi-plugin marketplace.
- [Team dashboard](https://cursor.com/docs/account/teams/dashboard) — where team marketplaces are imported and managed.

