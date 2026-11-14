# ui-forge-kit

Claude Code plugin bundling a UI design framework:

- **ui-forge**: orchestrator, `inspire → direct → create → verify` with gates
- **ui-director**: component composition, hierarchy, critique loop
- **uxui-workflow**: requirements → UX → rule-of-three UI (MIT, by Jad / AI Tooltip)
- **unslop**: de-AI fix passes (CC BY 4.0, by Damir Sokolovsky, github.com/heydamir/unslop)
- **shadcn MCP** (Magic UI / React Bits via registries)

## Install

```
/plugin marketplace add WilltheRanger/ui-forge-kit
/plugin install ui-forge-kit@ui-forge-kit
```

## Cloud sessions

In a project repo's `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "ui-forge-kit": { "source": { "source": "github", "repo": "WilltheRanger/ui-forge-kit" } }
  },
  "enabledPlugins": { "ui-forge-kit@ui-forge-kit": true }
}
```

Set `API_KEY_21ST` as a secret in the cloud environment (never commit it). 21st.dev and Figma come
from claude.ai connectors; Awwwards and Playwright MCPs are local and may be unavailable in the cloud.

## Per project

Add to `components.json`:

```json
"registries": {
  "@magicui": "https://magicui.design/r/{name}.json",
  "@react-bits": "https://reactbits.dev/r/{name}.json"
}
```
