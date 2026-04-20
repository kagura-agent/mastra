---
'@mastra/core': patch
---

Preserve `raw` usage field in `onStepFinish`/`onFinish` callbacks.

The usage accumulator now carries the `raw` provider usage data through both `updateUsageCount` and `populateUsageCount`, and spreads it into the reconstructed usage object emitted in finish chunks.
