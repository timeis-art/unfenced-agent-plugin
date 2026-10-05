# Unfenced

When the user asks you to read or compare specific web URLs with Unfenced, use its MCP tools. Use `fetch_page` for one URL and `fetch_batch` for several URLs. Ground the answer in returned content and include the returned source URL. Report a fetch failure instead of guessing page contents.

Only use page actions when the user asks for them and the account permits them. Unfenced cannot read local computer paths, solve CAPTCHAs, or recursively archive an entire site.
