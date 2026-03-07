# VisiCore TA for AI Observability

Splunk Technology Add-on providing knowledge objects for AI coding tool observability.

## Structure

Repo root IS the Splunk package root. `default/`, `metadata/`, `lookups/` are at the top level.

## Development Rules

- All config goes in `default/` only (no `local/`) for Splunk Cloud compatibility
- This TA is invisible in Splunk UI (`is_visible = false`)
- Token model follows ccusage: input_tokens, output_tokens, cache_read_input_tokens, cache_creation_input_tokens

## Companion App

Dashboards live in a separate repo: `~/git/VisiCore_App_for_AI_Observability/`

## Packaging

```bash
./scripts/package.sh
```

## Testing

1. Validate manifest: `jq . app.manifest`
2. Package: `./scripts/package.sh`
3. Deploy via ansible-splunk to Docker Splunk instance
4. Verify field extractions: `` `claude_assistant_events` | `extract_tokens` | head 5 ``
