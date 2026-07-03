---
mode: agent
agent: frontend-plugin
name: frontend-plugin-prompt
description: "Prompt for the frontend-plugin agent. Creates and updates plugin components including skills, hooks, rules, and agent definitions in the plugin/ directory."
---

### Requirements

1. **Skill Structure:** Each skill lives in `plugin/skills/<name>/SKILL.md` with frontmatter (name, description) followed by focus areas, goals, output format, and workflow steps.
2. **Hook Format:** Hooks are JSON files in `plugin/hooks/` following the existing pattern (api-client-sync.json, flutter-build-sync.json, ui-lint-sync.json). Each hook has an id, name, event, and action.
3. **Plugin Manifest:** The root `plugin/.plugin/plugin.json` declares supported features (agents, skills, rules, hooks), discovery settings, and orchestration config. Update it when adding new plugin types.
4. **Skill Discovery:** Skills are auto-discovered from `plugin/skills/` by the router. Each skill directory must contain a `SKILL.md` with a descriptive `name` field in the frontmatter.

### Constraints

- SKILL.md frontmatter must include `name` and `description`
- Hook JSON must include `id`, `name`, `event`, and `action` fields
- Follow existing 16 skills for naming and description conventions
- Plugin agent definitions go in `plugin/agents/`, not `.github/agents/`

### Success Criteria

- Skill appears in the plugin catalog when `discover_all()` runs
- Hook triggers on the specified event
- Rule enforces without errors
- `plugin.json` validates against the schema

### Usage Template

```
Create/update a plugin component:
- Type: [skill/hook/rule/agent]
- Name: [component name]
- Description: [brief description]
- Event/Action: [for hooks — trigger and command]
Show the diff and wait for my confirmation before applying.
```

### Chat Example

```
User: Create a new discover-form-validators skill under plugin/skills/ that lists all form validation patterns in the project.
```

Agent (expected):
- Creates `plugin/skills/discover-form-validators/SKILL.md` with frontmatter and workflow
- Follows the pattern from existing skills like discover-form-validation
- Shows diff and waits for confirmation
