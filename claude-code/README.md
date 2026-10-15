# PayAgentic account visibility

Inspect wallets, stablecoin balances, recent transactions, policies, agents and approval status. The six hosted tools are `list_wallets`, `get_balance`, `list_recent_transactions`, `list_policies`, `payagentic_list_agents` and `payagentic_list_approvals`. They cannot initiate payments, fund wallets, approve requests or change policies.

## Release status

Version 0.2.2 was verified in the Claude directory on 4 October 2026. This 0.2.3 candidate adds explicit Claude Code public-client configuration and fixed callback port 27895; it is not a verified directory update. The compatible API and protected registry must be deployed before native acceptance. Production consent, tools, refresh and disconnect still require recorded acceptance.

## Privacy and network behavior

The skills guide the host to call https://mcp.payagentic.ai/mcp using the user's scoped OAuth grant. Account data passes between PayAgentic and the selected AI host and may appear in its conversation history. Host privacy/retention settings and https://payagentic.ai/legal/privacy apply. The package itself stores no account data or credentials and contains no telemetry, executables, hooks, shell children, background processes or third-party credential readers. OAuth tokens are managed by the host in its own credential store. Never paste access tokens, wallet keys or seed phrases into chat.

The hosted PayAgentic service separately stores authorization and security audit records, including user, organization and grant identifiers. Its implementation does not impose a 30-day deletion limit on these audit records, so the directory disclosure uses the longer-than-30-days retention category. This does not extend token validity: expired or revoked credentials must be rejected. Service retention and rights are governed by PayAgentic's privacy policy. The skills do not send conversation history or data to services beyond the declared connector.

## Examples

- Show my wallets and stablecoin balances.
- List my policies and whether they are enabled.
- Summarize recent transaction statuses.
- Show pending and resolved approval status.

Use only tools exposed by the connected account. Preserve decimal values and asset/network labels; do not invent wallet IDs or claim that read access approves a payment. Stop on missing permissions and revoked access.

Documentation: https://payagentic.ai/platform/developers
Support: https://payagentic.ai/contact or hello@payagentic.ai
Terms: https://payagentic.ai/legal/terms
License: MIT (LICENSE)

## Claude setup

Install the plugin from its approved directory listing when available. Before approval, use a local review installation of this folder. Complete Claude's browser OAuth authorization for the declared MCP endpoint; do not supply a shared API key. The host discovers the server's OAuth metadata. For Claude Code, this candidate declares `oauth.clientId: payagentic-claude-code` and `oauth.callbackPort: 27895`; keep that port free locally. No client secret is needed. If discovery or sign-in fails, stop and report the connection error; the hosted deployment must be fixed.

The plugin references one hosted connector. Pair its connector and bundle listings under the same publisher organization to avoid duplicate tools. Disconnect in Claude and revoke the grant in PayAgentic's Developers → MCP servers page.

### Standalone Claude Code review

Use a current Claude Code release supporting these OAuth options. Avoid a second
server entry when the plugin is already installed. For a standalone connection:

```sh
claude mcp add --transport http --client-id payagentic-claude-code --callback-port 27895 payagentic https://mcp.payagentic.ai/mcp
claude mcp login payagentic
```

For plugin installation, use `/mcp` to authenticate instead. Native Claude Code
acceptance does not establish the separate Claude web connector's registration.
See [native-client release and acceptance](../OAUTH-NATIVE-CLIENTS.md).
