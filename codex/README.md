# PayAgentic OpenAI marketplace source

This source contains the PayAgentic plugin at `plugins/payagentic` for local
Codex installation. It is separate from OpenAI public-directory publication.

Register the exported source with:

```sh
codex plugin marketplace add /absolute/path/to/agent-plugins/codex
```

Install PayAgentic, open a new task and connect through the OAuth sign-in flow.
See `plugins/payagentic/README.md`. No API-key environment variable is required.

This is a local review source, not an accepted OpenAI public listing. Publisher
submission is managed in the private application release workspace. Keep that
workspace and its credentials out of this public repository.

`tool-annotation-justifications.json` contains the required justification for
each annotation on each of the six read-only tools. Enter these after the live
MCP scan. OAuth deployment, domain verification, protected reviewer access,
a real host recording and policy review must be completed before submission.
