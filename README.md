# Unfenced for Claude and Gemini CLI

This folder is a dual-format package for the existing hosted Unfenced MCP service.
Claude reads `.claude-plugin/plugin.json` and the web-reading skill. Gemini CLI
reads `gemini-extension.json` and `GEMINI.md`. Both use OAuth sign-in to the
Unfenced account. Gemini CLI uses the scoped
`https://unfenced.ai/api/mcp?profile=reading` endpoint; Claude's existing package
uses `https://unfenced.ai/api/mcp`. Neither package contains a credential.

An approved Unfenced account is required during the current private preview.
Installing the extension does not grant account access.

## Local validation

```sh
claude plugin validate . --strict
gemini extensions validate .
```

After installing in Gemini CLI, run `/mcp auth unfenced` if the sign-in browser
does not open automatically, then use `/mcp` to check its tools. To load this
package in Claude Code during development, use
`claude --plugin-dir .`. These development commands
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
extension gallery discovers public repositories with the `gemini-cli-extension`
topic and a root manifest. Google crawls these repositories daily and lists
extensions that pass validation. As of 2026-10-09, Unfenced was not present in
the public gallery index; GitHub publication does not confirm gallery inclusion.

Install the released Gemini CLI extension directly:

```sh
gemini extensions install https://github.com/timeis-art/unfenced-agent-plugin --ref=v0.1.2
```

The Gemini extension supports `fetch_page`, `fetch_batch` (up to 20 explicit
URLs), and `get_page_links`. It exposes no browser actions or form entry.
Selected URLs and reading options are sent to Unfenced, and returned content
and source links are supplied to Gemini. Fetches create metered jobs and account
history. Do not submit URLs containing secrets or restricted personal data.

Gemini Apps in the browser has a separate custom MCP app feature with limited
regional availability. This Gemini CLI extension does not install into Gemini
Apps in the browser.

New Unfenced accounts still require admission to the private preview. The gallery
listing must disclose that access requirement until self-service onboarding is
ready.

For the documented custom Perplexity connection route, see
[PERPLEXITY.md](./PERPLEXITY.md). This is setup documentation, not a public
Perplexity listing. No live Gemini or Perplexity OAuth/tool rehearsal is claimed
by publishing this package.
