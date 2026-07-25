# Claude Plugins Marketplace

A plugin marketplace for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) providing spec-driven planning, developer tooling, and cost-aware model routing.

## Table of Contents

- [Plugins](#plugins)
- [Installation](#installation)
- [Auto-Update](#auto-update)
- [Manual Update](#manual-update)
- [License](#license)

## Plugins

| Plugin | Description | Author | License |
|--------|-------------|--------|---------|
| **sdd-planner** | Spec-driven development planning: lifecycle skills and review agents for structured plans, specs, designs, and research | Daniel Weiner | MIT |
| **devtools** | AI developer tooling - automated test generation, TDD workflows, regression hunting, and multi-agent code audits | Daniel Weiner | MIT |
| **model-router** | Routes every sub-task to the cheapest capable model tier, escalating only on verified failure; registers other plugins' agents via a configurable registry | Daniel Weiner | MIT |

## Installation

### 1. Add the marketplace

From within a Claude Code session, run:

```
/plugin marketplace add danweinerdev/claude-plugins
```

### 2. Install a plugin

```
/plugin install sdd-planner@claude-plugins
/plugin install devtools@claude-plugins
/plugin install model-router@claude-plugins
```

The plugins are independent, but `model-router` is built to cooperate with the
others: install it alongside `sdd-planner` and run
`/model-router:profiles enable sdd-planner` to route planning work by tier.

You can install to a specific scope:

- **User** (default) - available in all projects
- **Project** - available to anyone working in the current project
- **Local** - only available to you in the current project

### 3. Reload plugins

Apply changes immediately without restarting:

```
/reload-plugins
```

## Auto-Update

To enable auto-update so the marketplace and its plugins stay current automatically:

1. Run `/plugin`
2. Select the **Marketplaces** tab
3. Choose **claude-plugins** and select **Enable auto-update**

Once enabled, Claude Code will check for updates at startup and pull the latest versions automatically.

> **Note:** Official Anthropic marketplaces have auto-update enabled by default. Third-party marketplaces like this one must be opted in manually.

### Environment variables

If you want fine-grained control over auto-update behavior:

```bash
# Disable ALL auto-updates (Claude Code + plugins)
export DISABLE_AUTOUPDATER=true

# Keep plugin auto-updates enabled while disabling Claude Code auto-updates
export DISABLE_AUTOUPDATER=true
export FORCE_AUTOUPDATE_PLUGINS=true
```

## Manual Update

To manually refresh the marketplace listings at any time:

```
/plugin marketplace update claude-plugins
```

## License

MIT
