---
'@solana/connector': patch
---

Add `useKitMessageSigner`, a React hook that returns a kit `MessageModifyingSigner` for the connected account. It checks `solana:signMessage` on the account's own feature list and needs no cluster, so it also works on custom clusters. Signing errors now keep the wallet's own error. `ConnectorError` sets the standard ES `cause`, and `signMessage` and off-chain message-signing failures include the wallet's message. Plain-object rejections such as `{ code: 4001, message: 'User rejected the request.' }` are now classified as user rejections instead of `SIGNING_FAILED`. `toJSON()` still emits no stack.
