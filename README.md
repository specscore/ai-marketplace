# SpecScore AI Marketplace

Marketplace for first-party AI plugins aligned with the [SpecScore](https://specscore.md) standard and [SpecScore Studio](https://specscore.studio). Claude Code and Codex consume this marketplace directly; the individual plugins also install into Gemini CLI, GitHub Copilot CLI, and Cursor (see [Other agents](#other-agents)).

> **Plugins vs CLIs.** This marketplace indexes AI-agent **plugins** — skill bundles that teach agents how to use the SpecScore CLI and the SpecScore Studio workflow. The CLI binaries themselves are separate; see [`specscore.md/install`](https://specscore.md/install) for the install matrix.

## Install

### Claude Code

Add this marketplace to Claude Code once:

```
/plugin marketplace add specscore/ai-marketplace
```

Then install any plugin from it:

```
/plugin install specscore@specscore
/plugin install specstudio@specscore
```

### Codex

This repo includes Codex marketplace metadata at [`.agents/plugins/marketplace.json`](./.agents/plugins/marketplace.json), which references each plugin repo directly (no vendored copies). Add this marketplace to Codex once:

```
codex plugin marketplace add specscore/ai-marketplace
```

Then enable the plugins you want from Codex's plugin directory. Codex has no `codex plugin add` subcommand; installation happens through the plugin directory after the marketplace is added. The Codex marketplace currently lists `specscore` and `specstudio`.

### Other agents

Gemini CLI, GitHub Copilot CLI, and Cursor have no marketplace concept — install each plugin straight from its own repository:

| Agent | `specscore` | `specstudio` |
|---|---|---|
| Gemini CLI | `gemini extensions install https://github.com/specscore/ai-plugin-specscore` | `gemini extensions install https://github.com/specscore/specstudio-skills` |
| GitHub Copilot CLI | `copilot plugin install specscore/ai-plugin-specscore` | `copilot plugin install specscore/specstudio-skills` |
| Cursor | copy the repo's `skills/` into `.cursor/skills/` | copy the repo's `skills/` into `.cursor/skills/` |

Each plugin repo's README documents the exact per-agent install commands.

## Plugins

| Plugin | Claude Code | Codex | Repository |
|---|---|---|---|
| `specscore` | `/plugin install specscore@specscore` | from plugin directory | [`specscore/ai-plugin-specscore`](https://github.com/specscore/ai-plugin-specscore) |
| `specstudio` | `/plugin install specstudio@specscore` | from plugin directory | [`specscore/specstudio-skills`](https://github.com/specscore/specstudio-skills) |

## Plugin details

### `specscore`

Wraps the [`specscore` CLI](https://github.com/specscore/specscore-cli) as agent skills. Teaches AI agents how to use `specscore` for spec navigation, linting, and lifecycle operations. Thin, neutral CLI wrapper — composable with any orchestrator runtime and any opinionated workflow layered on top.

### `specstudio`

**SpecScore Studio** is the first-party authoring surface for SpecScore. The `specstudio` plugin delivers the spec-driven development workflow — ideate, design, plan, build, verify, recap, review, ship — as an AI-agent skills bundle. Distributed from [`specscore/specstudio-skills`](https://github.com/specscore/specstudio-skills). Skill identifiers use the `specstudio:*` prefix (e.g., `specstudio:ideate`, `specstudio:specify`).

The web editor counterpart of SpecScore Studio lives at [`specscore.studio`](https://specscore.studio).

## Why a separate marketplace

This marketplace is the canonical home for first-party SpecScore plugins — symmetric with [`specscore.md`](https://specscore.md) (the standard) and [`specscore.studio`](https://specscore.studio) (the editor). Hosting under `@specscore` keeps the brand stack consistent: SpecScore-aligned tooling lives at the SpecScore namespace.

The broader [`sneat-co/ai-marketplace`](https://github.com/sneat-co/ai-marketplace) is a multi-project meta-index for other tooling published by the same author (Synchestra orchestrator, datatug, ingitdb). The two marketplaces are complementary; SpecScore plugins live here.

## Contributing

This marketplace currently lists first-party plugins only. If you've built a third-party SpecScore-aligned plugin and want it indexed here, [open an issue](https://github.com/specscore/ai-marketplace/issues) — third-party plugins may be accepted once the SpecScore ecosystem has multiple independent implementors. Until then, Claude Code and Codex support multiple marketplaces per user, so publishing your own is the simplest path.

## License

MIT — see [LICENSE](LICENSE).
