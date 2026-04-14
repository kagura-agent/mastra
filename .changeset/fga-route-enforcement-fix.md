---
'@mastra/server': patch
'@mastra/express': patch
'@mastra/fastify': patch
'@mastra/hono': patch
'@mastra/koa': patch
---

Fixed route-level FGA enforcement for server handlers, thread memory APIs, and protected custom routes across the built-in adapters.

This closes several authorization gaps where callers could still access detail endpoints by ID, custom-route FGA checks could miss path parameters, or memory thread filtering could leak unviewable totals and pagination metadata.
