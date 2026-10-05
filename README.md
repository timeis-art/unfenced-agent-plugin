# Unfenced for Claude and Gemini CLI

This folder is a dual-format package for the existing hosted Unfenced MCP service.
Claude reads `.claude-plugin/plugin.json` and the web-reading skill. Gemini CLI
reads `gemini-extension.json` and `GEMINI.md`. Both use OAuth sign-in to the
Unfenced account and the same `https://unfenced.ai/api/mcp` endpoint. Neither
package contains a credential.

An approved Unfenced account is required during the current private preview.
Installing the extension does not grant account access.

## Local validation

```sh
claude plugin validate ./apps/agent-plugins/unfenced --strict
gemini extensions install ./apps/agent-plugins/unfenced
```

After installing in Gemini CLI, run `/mcp auth unfenced` if the sign-in browser
does not open automatically, then use `/mcp` to check its tools. To load this
package in Claude Code during development, use
`claude --plugin-dir ./apps/agent-plugins/unfenced`. These development commands
are not the public directory install flow.

## Public distribution

The Claude directory accepts a remote MCP connector or a GitHub-hosted plugin
bundle. Submit the GitHub repository for this bundle through Anthropic's
developer portal under a paid Claude account. Anthropic reviews it before it
appears in the directory.

The same repository is a Claude Code marketplace. Install it with:

```sh
claude plugin marketplace add timeis-art/unfenced-agent-plugin
claude plugin install unfenced@unfenced-plugins
```

The public repository has `gemini-extension.json` at its root. Gemini CLI's
extension gallery discovers repositories with the `gemini-cli-extension` topic
and a release tag. Google crawls tagged repositories daily and lists extensions
that pass validation.

Gemini Apps in the browser has a separate custom MCP app feature with limited
regional availability. This Gemini CLI extension does not install into Gemini
Apps in the browser.

New Unfenced accounts still require admission to the private preview. The gallery
listing must disclose that access requirement until self-service onboarding is
ready.
