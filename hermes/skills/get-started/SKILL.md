---
name: get-started
description: Help a user connect their PayAgentic organization and inspect account data with the available read-only MCP tools.
---

# Start with PayAgentic

1. Check whether PayAgentic's six read-only tools are already exposed by the host. If not, use the host's documented plugin/MCP setup and browser OAuth flow. Never collect credentials in chat, read another application's credential files, install software or change configuration without the user's request.
2. If discovery or sign-in fails, explain the connection error and stop. Hosted OAuth deployment is a release gate; do not invent an access token or fall back to shared keys or anonymous access.
3. Ask the user to select their organization in PayAgentic's consent screen. Do not switch tenants or expand scope to work around a denial.
4. Start with list_wallets. Use only wallet IDs returned for this connected account when calling get_balance. Apply the account-overview skill for transactions, policies, agents and approval status.
5. Describe how to disconnect in the host and revoke the grant from PayAgentic's Developers → MCP servers page. Verify revocation using an authorized test session; never claim it succeeded without evidence.
6. Account visibility is read-only. Payments, funding, approvals and policy changes are outside this plugin's capabilities.
