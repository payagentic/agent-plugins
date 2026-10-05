# PayAgentic for Cursor

Connect Cursor to PayAgentic for read-only account visibility.

## Local review installation

Copy this directory as `~/.cursor/plugins/local/payagentic`, restart Cursor or run
Developer: Reload Window, and open Customize to inspect its MCP server and skill.
Configure `PAYAGENTIC_API_KEY` using Cursor's plugin configuration surface.
For managed teams, the admin configures the declared variable in Dashboard →
Plugins → Configure. Check that the target Cursor client exposes the variable
configuration flow; verify a real connection before distribution.

The manifest stores a variable schema; `mcp.json` contains only a placeholder.
Do not replace the placeholder in the repository with a real key.

## Public installation

After Cursor accepts and publishes the submitted repository, link the accepted
listing here and use its assigned installation command. `/add-plugin payagentic`
is the requested identifier, not a claim that the command is available today.

This public repository uses `.cursor-plugin/marketplace.json` at its root to
select the `cursor/` package. Submit https://github.com/payagentic/agent-plugins
via https://cursor.com/marketplace/publish. The private platform repository is not
required. See https://cursor.com/docs/reference/plugins.

## Capabilities

Six read-only tools: `list_wallets`, `get_balance`, `list_policies`,
`list_recent_transactions`, `payagentic_list_agents`, `payagentic_list_approvals`.
The policy tool lists configuration; it does not evaluate a payment intent.
No payment initiation, approval, transfer, funding or configuration write is exposed.

## Account and credential setup

Use your own PayAgentic organization at https://app.payagentic.ai. An authorized
organization administrator creates a **connector** key under Developers → MCP
servers. Allow only the required wallets, agents, policies, approvals and
transactions read permissions. Connector keys are organization-bound; the package
deliberately does not provide a way to switch organizations. Use a separate key
for another organization. Revoke the key from the dashboard to disconnect access.
Never supply a private wallet key, seed phrase or a broad administrative API key.
Do not paste secrets into chats, repository files, terminal arguments or screenshots.

## Try it

Ask: “Show my PayAgentic wallets and balances.” Then try “List my policies and
their enabled status” or “Summarize recent transaction statuses.” A balance
requires a wallet already returned for the authenticated organization.

A 401 means missing, invalid, expired or revoked credentials. A 403 means the
credential lacks access. Ask your organization administrator to correct access;
do not work around permission failures. Empty lists can be valid. A list is not
necessarily the complete history. If tools differ from the six documented here,
check the deployed release before use.

## Privacy Policy

The AI host sends authenticated requests to https://mcp.payagentic.ai/mcp and
receives the requested account data. The data can appear in the host's conversation
and is subject to that host's data controls. This package has no separate
telemetry, hooks, local executables or credential collection service.

- Privacy: https://payagentic.ai/legal/privacy
- Terms: https://payagentic.ai/legal/terms
- Support: https://payagentic.ai/contact (hello@payagentic.ai)
- Developer documentation: https://payagentic.ai/platform/developers

## Release status

This is a review candidate, not an approved marketplace listing. Local package
validation does not establish a live authenticated connection. Publication needs
isolated permission/expiry/revocation/tenant tests, test-credential cleanup and
publisher approval. Run every tool against a populated review account before
submission. No payments or spending are needed for this read-only integration.
