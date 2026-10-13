# Native OAuth candidates — 13 October 2026

These packages do not deploy the authorization server or grant account access.
The application companion PR must deploy first, followed by its reviewed protected
client registry. Existing server/client configuration stays unchanged until then.
An older server does not support the new native profiles. Installation is distinct
from authenticated acceptance and vendor publication.

| Host | Public client | Callback |
| --- | --- | --- |
| Codex | `https://chatgpt.com/oauth/codex/client.json` | Canonical localhost or 127.0.0.1 `/callback`, with a nonzero ephemeral port |
| Claude Code | `payagentic-claude-code` | Exact localhost or 127.0.0.1 `/callback`, port 27895 |
| Hermes | Existing approved metadata client | Existing published callbacks, ports 27890–27894 |

Use current host versions supporting their documented OAuth configuration. Codex
uses its native metadata client; Claude Code explicitly declares a public client
and callback port. Neither requires a client secret or a shared connector key.
No dynamic registration or arbitrary network callback is enabled.

For each supported host and environment, record the deployed revision, host version,
client ID and sanitized outcomes for login, explicit organization consent, denial,
six scoped reads, expiry, refresh rotation/replay denial, disconnect and tenant
isolation. Use populated synthetic fixtures and revoke disposable grants afterward.
Local fixtures do not replace these actual host connections. Historical Hermes
staging acceptance does not establish Codex, Claude Code or production acceptance.
Do not publish tokens, login codes, state, verifiers or account-response contents.

References: [Claude Code MCP](https://code.claude.com/docs/en/mcp),
[Codex client registration](https://github.com/openai/codex/blob/main/codex-rs/rmcp-client/src/oauth_client_registration.rs).
