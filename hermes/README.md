# PayAgentic account visibility

Inspect wallets, stablecoin balances, recent transactions, policies, agents and approval status. The six hosted tools are `list_wallets`, `get_balance`, `list_recent_transactions`, `list_policies`, `payagentic_list_agents` and `payagentic_list_approvals`. They cannot initiate payments, fund wallets, approve requests or change policies.

## Release status

Version 0.2.0 is a catalog review candidate. Hosted OAuth discovery is not deployed successfully yet. Live consent, tool, refresh and disconnect acceptance must pass before this integration is promoted for production use.

## Privacy and network behavior

The skills guide the host to call https://mcp.payagentic.ai/mcp using the user's scoped OAuth grant. Account data passes between PayAgentic and the selected AI host and may appear in its conversation history. Host privacy/retention settings and https://payagentic.ai/legal/privacy apply. The package itself stores no account data or credentials and contains no telemetry, executables, hooks, shell children, background processes or third-party credential readers. OAuth tokens are managed by the host in its own credential store. Never paste access tokens, wallet keys or seed phrases into chat.

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

## Hermes setup

This portable plugin provides skills. It does not register local tools or duplicate the separately configured hosted MCP server. The Hermes catalog submissions for the skills plugin and OAuth MCP entry are reviewed independently.

For a review installation, connect the hosted server with:

```sh
hermes mcp add payagentic --url https://mcp.payagentic.ai/mcp --auth oauth
```

Complete browser consent using your own PayAgentic account. When a Nous-approved catalog entry is available, use `hermes mcp install payagentic` instead of adding a second server. The skills work with the tools actually discovered by the host. On OAuth discovery or connection failure, stop and report it; do not substitute credentials from another client's store. Disconnect/remove the server through Hermes and revoke the corresponding grant in PayAgentic.

Validated with Hermes 0.21.5 portable Agent Plugin support. No Hermes core or Desktop overrides are included.
