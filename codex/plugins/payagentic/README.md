# PayAgentic for ChatGPT and Codex

PayAgentic provides six read-only account tools: `list_wallets`, `get_balance`,
`list_policies`, `list_recent_transactions`, `payagentic_list_agents` and
`payagentic_list_approvals`. They cannot send payments, approve requests, change
policies or fund wallets.

## Connect your account

After installing PayAgentic, choose the host's Connect or Sign in action. Sign
in to PayAgentic, select your organization and approve the requested read access.
The host negotiates OAuth through https://mcp.payagentic.ai/mcp. This package
contains no API key and does not require an environment variable. Never paste
passwords, API keys or one-time codes into a conversation.

Ask “Show my PayAgentic wallets and balances,” then try policy, transaction,
agent or approval-status questions. A balance lookup needs a wallet returned
for your connected organization. Empty lists are valid. A 401 means reconnect;
a permission denial requires help from your organization administrator.

Disconnect in the host or revoke access under PayAgentic Developers → MCP
servers at https://app.payagentic.ai. Revocation prevents future account reads;
it does not remove data already included in a host conversation.

## Local installation

This package uses the supported `.codex-plugin/plugin.json` format. Register
its exported marketplace source, install PayAgentic and open a new task to test
it. Local installation does not publish to OpenAI's public directory. OAuth
requires a working deployed authorization server, MCP resource metadata and the
approved Codex native client profile. Use a current Codex version supporting
Client ID Metadata Documents; native connection acceptance remains a separate
release gate from package validation.

## Privacy and support

The host receives the requested PayAgentic account data, which can appear in
its conversation and is subject to its data controls. This package has no local
executables, hooks, separate telemetry or credential collection service.

- Website: https://payagentic.ai
- Privacy: https://payagentic.ai/legal/privacy
- Terms: https://payagentic.ai/legal/terms
- Support: https://payagentic.ai/contact (hello@payagentic.ai)

This package is a public-directory review candidate. Public availability begins
only after successful live acceptance, OpenAI review and publisher activation.
