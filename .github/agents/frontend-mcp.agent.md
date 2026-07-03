---
name: frontend-mcp
description: "Single-task agent for the MCP frontend discovery server (mcp_hub_frontend/). Handles MCP tool creation, server registration, and environment configuration. Does NOT handle Next.js pages, UI components, or plugin internals."
tools: Read, Write, Edit, Bash, Glob, Grep
---

# Frontend MCP Agent

Single task: Create or update MCP discovery tools in `mcp_hub_frontend/src/tools/` and manage server registration in `mcp_hub_frontend/src/server.ts`.

## Scope

- `mcp_hub_frontend/src/tools/discoverFrontendArchitecture.ts` — Frontend architecture
- `mcp_hub_frontend/src/tools/discoverApiLayer.ts` — API service layer
- `mcp_hub_frontend/src/tools/discoverComponents.ts` — UI components
- `mcp_hub_frontend/src/tools/discoverPages.ts` — Page routes
- `mcp_hub_frontend/src/tools/discoverStateManagement.ts` — State management
- `mcp_hub_frontend/src/tools/discoverServices.ts` — Backend services
- `mcp_hub_frontend/src/tools/discoverApiDependencies.ts` — API dependencies
- `mcp_hub_frontend/src/tools/discoverEnvironmentConfig.ts` — Environment config
- `mcp_hub_frontend/src/tools/findFeature.ts` — Feature file search
- `mcp_hub_frontend/src/tools/findFeatureImplementation.ts` — Feature implementation details
- `mcp_hub_frontend/src/server.ts` — Tool registration with name, description, zod schema
- `mcp_hub_frontend/src/config.ts` — Server config (HUB_FRONTEND_PATH)
- `.vscode/mcp.json` — IDE registration
- `npm run build` — TypeScript compilation

## Out of scope

This agent does NOT handle:
- Plugin system (`plugin/`) → use `frontend-plugin`
- Next.js pages or routes → use `frontend-pages`
- UI components → use `frontend-components`
- API hooks or state management → use `frontend-data`

## Inputs

- `tool_name` — the tool to create or modify (e.g., `discoverPages`, `findFeature`)
- `params` — optional zod input schema for parameterized tools
- `description` — LLM-facing description for tool registration

## Outputs

- New or modified tool `.ts` files in `mcp_hub_frontend/src/tools/`
- Updated `server.ts` with new tool registration
- Updated `.vscode/mcp.json` if env vars change
- `npm run build` verification

## Example prompts

- "Add a tool that discovers all form validators in the project."
- "Register a new `discover_auth_guards` tool in server.ts."
- "Update the `findFeature` tool to also search in `plugin/` directory."
