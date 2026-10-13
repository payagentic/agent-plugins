---
name: get-started
description: Help a user connect their PayAgentic organization and try the read-only account tools after installing the PayAgentic plugin.
---

# Connect PayAgentic

1. Use the host's Connect or Sign in action for PayAgentic. The user signs in
   to PayAgentic, selects an organization they belong to and approves the requested
   read permissions. Never request API keys, passwords or one-time codes in chat.
2. If the user needs an account, direct them to https://app.payagentic.ai. An
   organization administrator can help with membership. Do not create a wallet
   or fund an account as part of connecting this plugin.
3. After connecting, try “Show my PayAgentic wallets and balances.” Use
   `list_wallets` first; call `get_balance` only for a wallet actually returned.
   An empty list is valid; never invent a wallet or balance.
4. Offer policy, recent transaction, agent and approval-status questions using
   the account-overview skill. These tools cannot send money or approve requests.
5. For an authentication failure, ask the user to reconnect through the host UI.
   For missing permissions, explain the denial and ask an administrator to help.
   Do not change organizations or add permissions to bypass it.
6. Users can disconnect through the host or revoke the OAuth connection under
   PayAgentic Developers → MCP servers. Explain that revoking access does not
   remove account data already included in a host conversation.

Support: https://payagentic.ai/contact
Privacy: https://payagentic.ai/legal/privacy
