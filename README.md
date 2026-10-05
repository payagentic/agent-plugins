# PayAgentic agent plugins

Public distribution packages for PayAgentic read-only account tools.

Start with the [installation guide](INSTALLATION.md) for Claude, Cursor, Hermes and standalone skills, including current availability and connection requirements.

- `cursor/`: Cursor review candidate with a scoped connector-key configuration and one account skill. The root `.cursor-plugin/marketplace.json` points to this package.
- `claude-code/`: Claude plugin with workflow skills and a hosted MCP reference.
- `hermes/`: portable Agent Plugin with workflow skills; the native Hermes MCP connector is configured separately with OAuth.

The Claude directory lists version 0.2.2 (verified October 4, 2026). Cursor 0.1.0 and Hermes 0.2.0 remain review candidates. Production OAuth and authenticated host acceptance are still pending as of October 5, 2026. Claude publication does not establish that account connections work. No Cursor or Hermes marketplace approval is claimed.

## Standalone skills

The two workflow skills are discoverable at [skills.sh](https://www.skills.sh/payagentic/agent-plugins).
An isolated Cursor install was verified on October 5, 2026 with `skills@1.7.0`:

```sh
npx --yes skills@1.7.0 add https://github.com/payagentic/agent-plugins/tree/1dbb6b42d0b138fc3aeb4bb2f78335bdc6cad67e/hermes --skill account-overview get-started --agent cursor
```

This pins the reviewed source. A GitHub tree URL using the slash-containing branch name is misparsed by this CLI version; use the commit URL above. Installing skills does not create an MCP connection or establish authenticated account access. Complete the host's approved connection setup separately, and stop if discovery or authorization fails.

Only public plugin assets are included. This repository does not contain the PayAgentic application, customer data, credentials, relayer services or wallet keys.

Documentation: https://payagentic.ai/platform/developers
Support: https://payagentic.ai/contact or hello@payagentic.ai
Privacy: https://payagentic.ai/legal/privacy
Terms: https://payagentic.ai/legal/terms

Licensed under MIT; see LICENSE.
