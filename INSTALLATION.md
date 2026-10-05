# Install PayAgentic skills and account tools

Status checked 5 October 2026. This guide distinguishes installing a package from successfully connecting an account. Hosted account acceptance remains pending. Do not treat a catalog entry or discovered tool names as proof of a working connection.

## Choose your client

| Client or directory | Package status | Account connection |
|---|---|---|
| Claude | Version 0.2.2 was verified in the directory on 4 October | Hosted OAuth; live acceptance pending |
| Cursor | Publisher application submitted on 5 October; approval pending | Review candidate uses a scoped connector key |
| Hermes | Version 0.2.0 review candidate; catalog review pending | Separately configured hosted OAuth MCP server |
| skills.sh | Both skills listed; isolated installation verified | Skills alone do not configure an account connection |
| Smithery | Unlisted preview; six tool definitions discovered | Authenticated OAuth acceptance pending |

## Claude

1. Find PayAgentic in Claude's plugin directory and verify the publisher and package details. Install the published package through that directory. See [package documentation](claude-code/README.md).
2. Connect the declared MCP endpoint, `https://mcp.payagentic.ai/mcp`, using Claude's browser OAuth flow and your own PayAgentic account.
3. Select the intended organization and review the requested read-only access. If discovery or login fails, stop and report the error. Do not paste a key into chat or substitute another client's credentials.
4. Once connected, start with “List my wallets.” Use only wallet IDs returned by the connected account for balance requests.

The package references one hosted connector. Avoid adding the same server a second time. Publication is confirmed separately from production login and tool acceptance.

## Cursor: local review candidate

Public marketplace installation is not yet confirmed. Use [the review package](cursor/README.md) only for an authorized local review:

1. Download or clone this public repository and review `cursor/`.
2. Copy that directory to `~/.cursor/plugins/local/payagentic`. Preserve any existing local configuration before replacing it.
3. Restart Cursor or run **Developer: Reload Window**, then inspect the MCP server and skill in **Customize**.
4. Configure `PAYAGENTIC_API_KEY` in Cursor's plugin configuration surface using your own scoped connector key. Managed-team administrators use **Dashboard → Plugins → Configure**. If the target client does not expose this configuration, stop and consult its documentation.
5. Confirm a read-only connection before using account results. Keep the repository's credential placeholder unchanged.

`/add-plugin payagentic` is a requested identifier, not a verified public installation command. Use the final command from Cursor's accepted listing after approval.

## Hermes: skills plus a separate MCP connection

The [portable plugin](hermes/README.md) supplies workflow skills. For an authorized review of its separate MCP connection:

```sh
hermes mcp add payagentic --url https://mcp.payagentic.ai/mcp --auth oauth
```

Complete browser consent with your own account. OAuth discovery, consent, refresh and disconnect still require live acceptance. Do not use `hermes mcp install payagentic` until the catalog entry is approved and available. Do not add a second copy of the same server.

## Standalone skills from skills.sh

The public [skills.sh page](https://www.skills.sh/payagentic/agent-plugins) lists `account-overview` and `get-started`. This exact command was verified in an isolated Cursor installation using skills 1.7.0:

```sh
npx --yes skills@1.7.0 add https://github.com/payagentic/agent-plugins/tree/1dbb6b42d0b138fc3aeb4bb2f78335bdc6cad67e/hermes --skill account-overview get-started --agent cursor
```

It pins the reviewed content. In that CLI version, a tree URL containing a slash in the branch name can be misparsed; use the commit URL. This installs instructions, not an MCP server, OAuth grant or account credential. Configure the connection separately through the host. If the plugin already supplies these skills, avoid duplicate installation.

## Verify a connection

The six read-only tools are `list_wallets`, `get_balance`, `list_recent_transactions`, `list_policies`, `payagentic_list_agents`, and `payagentic_list_approvals`. Start with wallets; use returned IDs for subsequent requests. Preserve decimal values, currency and network labels. Empty results may reflect the selected account or permissions. Do not invent records or change organizations to bypass a denial.

These tools cannot make payments, fund wallets, approve requests or change policies. Actual account output may be retained by the chosen host. Review its privacy settings and [PayAgentic's privacy policy](https://payagentic.ai/legal/privacy).

## Disconnect and troubleshoot

Disconnect or remove PayAgentic in the client, then revoke its OAuth grant in PayAgentic's **Developers → MCP servers** page. For the Cursor key-based candidate, revoke its scoped connector key through PayAgentic's key management. Removing skills alone does not revoke access. Verify that a previously authorized read is rejected after revocation.

For discovery/login failures or HTTP 401/403, check the documented host setup, the intended organization and the validity of your own grant. Report only a sanitized error and client version through [support](https://payagentic.ai/contact). Never send API keys, tokens, wallet keys, seed phrases, raw account responses or live execution screenshots.

[Developer documentation](https://payagentic.ai/platform/developers) · [Terms](https://payagentic.ai/legal/terms) · [Public source](https://github.com/payagentic/agent-plugins)
