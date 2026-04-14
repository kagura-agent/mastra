---
'@mastra/core': minor
'@mastra/server': patch
'@mastra/mcp': patch
'@mastra/auth-workos': patch
---

Added Fine-Grained Authorization (FGA) support alongside RBAC for relationship-based, resource-level access control. FGA answers "can this user perform this action on this specific resource?" — enabling multi-tenant isolation and per-resource permissions.

**New interfaces:** `IFGAProvider` (read-only checks) and `IFGAManager` (read + write operations) with types for warrants, resources, subjects, and queries.

**Enforcement at all execution points:** FGA checks are automatically enforced before agent execution (`generate()`, `stream()`), tool execution, workflow execution, memory thread access, and MCP tool calls. When no FGA provider is configured, all checks are skipped (backward compatible).

**New utility:** `checkFGA()` provides centralized FGA enforcement with `FGADeniedError` for denied checks. `MastraMemory.checkThreadFGA()` adds thread-level access control.

**Configuration:** Add `fga` to your server config:

```typescript
const mastra = new Mastra({
  server: {
    fga: new MastraFGAWorkos({ apiKey, clientId }),
  },
});
```
