# UI Design Brain

[![Claude Code Agent](https://img.shields.io/badge/Claude_Code-Agent-blueviolet?logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNMTIgMkM2LjQ4IDIgMiA2LjQ4IDIgMTJzNC40OCAxMCAxMCAxMCAxMC00LjQ4IDEwLTEwUzE3LjUyIDIgMTIgMnoiIGZpbGw9IndoaXRlIi8+PC9zdmc+)](https://docs.anthropic.com/en/docs/claude-code)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE.txt)
[![Components](https://img.shields.io/badge/Components-60%2B-orange)](skill/components.md)
[![Buy Me a Coffee](https://img.shields.io/badge/Buy_Me_a_Coffee-FFDD00?logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/caseyberlin)

A Claude Code agent that generates production-grade UI grounded in real component patterns — best practices, layout guidance, and accessibility rules for 60+ interface components.

## What it does

When Claude Code builds UI, it typically guesses at component patterns. This agent replaces guessing with a curated knowledge base sourced from [component.gallery](https://component.gallery), including:

- **Best practices** for every component (accessibility, sizing, behavior)
- **Common layouts** — proven arrangements for each pattern
- **Guardrails** — the agent verifies its own output against documented rules
- **Anti-patterns** — specific things to avoid
- **Design directions** — 5 style presets (SaaS, minimal, enterprise, creative, dashboard)

The result: interfaces that feel designed by a senior product designer, not assembled from a template.

## How it works

The agent runs as a **parallelizable subagent** in Claude Code. When you ask Claude to build UI, it delegates to this specialized agent which:

1. Identifies which components your request needs
2. Reads the best practices for each from a 60-component reference
3. Applies the right design direction
4. Generates production-ready code following the patterns
5. Self-verifies against a checklist before returning

Because it runs as a subagent, it works **in parallel** with other agents — your main Claude session stays free while this agent handles the UI work.

## Install

### Step 1 — Clone the repo

```bash
git clone https://github.com/CaseyRo/ui-design-brain-claude.git
```

### Step 2 — Copy the agent

```bash
# Copy the agent definition (required)
cp ui-design-brain-claude/agent.md ~/.claude/agents/ui-design-brain.md
```

### Step 3 — Copy the skill (component reference)

Choose personal (all projects) or project-level (shared with team):

```bash
# Option A: Personal skill (all projects)
cp -r ui-design-brain-claude/skill/ ~/.claude/skills/ui-design-brain/

# Option B: Project skill (this project only)
mkdir -p .claude/skills
cp -r ui-design-brain-claude/skill/ .claude/skills/ui-design-brain/
```

### Step 4 — Verify

```bash
# Check the agent is registered
claude agents

# You should see "ui-design-brain" in the list
```

## Usage

The agent activates automatically when you ask Claude Code to build UI. No special syntax needed.

### Examples

```
Build a settings page with sidebar navigation, toggle preferences, and a profile section.
```

```
Create a data table with search, filters, sortable columns, and pagination.
```

```
Design a SaaS dashboard with KPI cards, a chart area, and an activity feed sidebar.
```

### Explicit invocation

If Claude doesn't auto-delegate, you can be explicit:

```
Use the ui-design-brain agent to build a pricing page.
```

### Design directions

Request a specific style:

| Preset | Style |
|--------|-------|
| **Modern SaaS** | Default — clean, spacious, professional |
| **Apple-level Minimal** | Ultra-clean, generous whitespace |
| **Enterprise / Corporate** | Information-dense, keyboard-navigable |
| **Creative / Portfolio** | Bold, expressive, editorial typography |
| **Data Dashboard** | Optimized for data scannability |

```
Build a pricing page with an Apple-minimal aesthetic.
```

## What's inside

```
ui-design-brain/
├── agent.md          # Agent definition → copy to ~/.claude/agents/
├── skill/
│   ├── SKILL.md      # Skill entrypoint (component quick reference)
│   └── components.md # Full 60-component reference with best practices
├── LICENSE.txt
└── README.md
```

### Guardrails built in

The agent enforces these rules on itself:

- **Must read the reference** before generating any UI code
- **Must follow documented best practices** for every component used
- **Must use semantic HTML** — no `<div>` soup
- **Must meet WCAG AA** — contrast, focus indicators, keyboard nav
- **Must handle all states** — loading, empty, error, hover, focus, active, disabled
- **Must self-verify** against a checklist before returning output
- **Will not** use generic AI aesthetics, skip accessibility, nest modals, or over-engineer

### Component coverage

60 components: Accordion, Alert, Avatar, Badge, Breadcrumbs, Button, Button group, Card, Carousel, Checkbox, Color picker, Combobox, Date input, Datepicker, Drawer, Dropdown menu, Empty state, Fieldset, File, File upload, Footer, Form, Header, Heading, Hero, Icon, Image, Label, Link, List, Modal, Navigation, Pagination, Popover, Progress bar, Progress indicator, Quote, Radio button, Rating, Rich text editor, Search input, Segmented control, Select, Separator, Skeleton, Skip link, Slider, Spinner, Stack, Stepper, Table, Tabs, Text input, Textarea, Toast, Toggle, Tooltip, Tree view, Video, Visually hidden.

## How it differs from generic UI generation

| | Generic Claude | With UI Design Brain |
|-|----------------|---------------------|
| **Component knowledge** | Model training only | 60 components with specific best practices |
| **Layout guidance** | General advice | Concrete patterns per component |
| **Guardrails** | None | Self-verification checklist, anti-pattern avoidance |
| **Accessibility** | Mentioned loosely | Specific per-component rules |
| **Parallelization** | Runs in main context | Runs as subagent, frees main session |
| **Design grounding** | Generic output | Sourced from real design systems |

## Contributing

PRs welcome. To add or update components:

1. Edit `skill/components.md` — follow the existing format
2. If commonly needed, add to the quick reference in `SKILL.md`
3. For agent behavior changes, edit `agent.md`

## Credits

Originally created by [carmahhawwari](https://github.com/carmahhawwari/ui-design-brain) as a Cursor skill. Rewritten as a Claude Code agent with guardrails, parallelization support, and persistent memory.

Component data sourced from [component.gallery](https://component.gallery).

## License

MIT — see [LICENSE.txt](LICENSE.txt).
