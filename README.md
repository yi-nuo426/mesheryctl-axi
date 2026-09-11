# mesheryctl-axi

Agent-ergonomic AXI wrapper around [`mesheryctl`](https://docs.meshery.io/reference/mesheryctl). Prefer this over raw `mesheryctl` for agent workflows: token-efficient **TOON** list/view reporting, definitive empty states, `help[]` suggestions, and always-non-interactive execution.

```bash
npx -y mesheryctl-axi
```

## Prerequisites

- **Node.js ≥ 20**
- **`mesheryctl` installed and authenticated** (this package spawns `mesheryctl`; it does not embed Meshery)
  - Install: https://docs.meshery.io/installation
  - Override binary: `MESHERYCTL_BIN=/path/to/mesheryctl`

## Quick start

```bash
# Content-first home: description, bin path, best-effort system status/context
npx -y mesheryctl-axi

# TOON list/view reporting
npx -y mesheryctl-axi connection list
npx -y mesheryctl-axi system status
npx -y mesheryctl-axi system context
npx -y mesheryctl-axi design list
npx -y mesheryctl-axi model list
npx -y mesheryctl-axi component list

# Schema-faithful content retrieve (YAML/JSON — never TOON-as-content)
npx -y mesheryctl-axi design content <name> --format yaml
npx -y mesheryctl-axi model content <name> --format json
```

## Design notes

| Concern | Behavior |
| --- | --- |
| List / view metadata | TOON |
| Design / model **content** | Raw YAML or JSON only |
| Unknown flags | Non-zero exit + structured TOON error |
| Empty results | Definitive empty states (e.g. `connections: 0`) |
| Success | Includes `help[]` suggestions |
| Interactivity | Always non-interactive (no TTY prompts) |

## Commands (v1)

```
mesheryctl-axi                        # home
mesheryctl-axi connection list|view
mesheryctl-axi system status|context
mesheryctl-axi design list|view|content
mesheryctl-axi model list|view|content
mesheryctl-axi component list|view
```

## Development

```bash
npm install
npm test
npm run build
```

## License

Apache-2.0
