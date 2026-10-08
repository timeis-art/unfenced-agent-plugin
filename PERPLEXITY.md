# Unfenced with Perplexity

Perplexity documents account-scoped and organization-scoped custom remote MCP
connectors. This package does not create a public Perplexity directory listing.
No public third-party submission portal was found in the official documentation
checked on 2026-10-09.

## Connection details

- Name: Unfenced
- Server URL: `https://unfenced.ai/api/mcp?profile=reading`
- Transport: Streamable HTTP
- Authentication: OAuth 2.0
- Description: Read specific web pages, compare up to 20 explicit URLs, and
  extract links through Unfenced. An admitted Unfenced account is required.

In Perplexity, open Account settings > Connectors > Custom connector > Remote.
Enter these details, review the risk acknowledgment, and add the connector.
Open its card to authorize your Unfenced account through the hosted OAuth flow.
Enable the connector in the conversation's Sources menu before using it.
Custom remote connectors require a supported paid Perplexity plan or enabled
organization access. Do not put passwords, API keys, or reviewer credentials in
chat, a URL, or this repository.

## Scope and data

The reading profile exposes `fetch_page`, `fetch_batch`, and `get_page_links`.
It provides no form entry, uploads, purchases, credential setup, or browser
actions. Selected URLs and reading options are sent to Unfenced; returned page
text, links, and source metadata are supplied to Perplexity. Fetching creates
metered jobs and account history. Installing or adding the connector does not
grant access to the private preview.

Try reading `https://www.w3.org/WAI/` and requesting its title, summary, and
source link. This is a suggested test, not evidence of a completed live
Perplexity tool call.

## References

- [Perplexity setup](https://www.perplexity.ai/help-center/en/articles/13915507-adding-custom-remote-connectors)
- [Perplexity custom connector announcement](https://www.perplexity.ai/changelog/what-we-shipped---march-13-2026)
- [Unfenced support](https://unfenced.ai/plugin-support)
- [Privacy](https://unfenced.ai/legal/privacy-policy)
- [Terms](https://unfenced.ai/legal/terms-of-service)
