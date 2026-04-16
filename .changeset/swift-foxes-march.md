---
'@mastra/auth-workos': minor
---

Added `MastraFGAWorkos` provider for Fine-Grained Authorization using the WorkOS FGA (Warrant) API. Implements `IFGAManager` interface with support for:

- Authorization checks (`check()`, `batchCheck()`)
- Permission queries using DSL syntax (`query()`)
- Warrant management (`writeWarrant()`, `batchWriteWarrants()`, `listWarrants()`)
- Resource management (`createResource()`, `getResource()`, `updateResource()`, `deleteResource()`, `listResources()`)

```typescript
import { MastraFGAWorkos } from '@mastra/auth-workos';

const fga = new MastraFGAWorkos({
  apiKey: process.env.WORKOS_API_KEY,
  clientId: process.env.WORKOS_CLIENT_ID,
});

// Grant user access to execute an agent
await fga.writeWarrant({
  resource: { type: 'agent', id: 'my-agent' },
  relation: 'execute',
  subject: { resourceType: 'user', resourceId: 'user-123' },
});
```
