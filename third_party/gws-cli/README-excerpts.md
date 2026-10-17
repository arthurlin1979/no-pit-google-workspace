# Google Workspace CLI README excerpts

SPDX-License-Identifier: Apache-2.0

Source: https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/README.md

Pinned commit: `705fb0ecac6f4249679958f6325b809b63fdde17`

Excerpted and arranged on 2026-10-17. Changes: selected three portions of the upstream README, omitted other portions, and added this provenance header and section labels. Text inside the marked excerpts is unchanged. This file, including the added arrangement, is provided under Apache-2.0. See [LICENSE](LICENSE) and [../../THIRD_PARTY_NOTICES.md](../../THIRD_PARTY_NOTICES.md).

This is a versioned reference, not a replacement for the installed CLI's help. No command shown here was executed to access a Google account as part of preparing this document package. Credential precedence is not a guarantee of account isolation.

## Excerpt 1: inspect a method schema

<!-- BEGIN UPSTREAM SCHEMA EXCERPT -->

```bash
# Introspect any method's request/response schema
gws schema drive.files.list
```

<!-- END UPSTREAM SCHEMA EXCERPT -->

## Excerpt 2: pagination

<!-- BEGIN UPSTREAM PAGINATION EXCERPT -->

### Pagination

| Flag                | Description                                    | Default |
| ------------------- | ---------------------------------------------- | ------- |
| `--page-all`        | Auto-paginate, one JSON line per page (NDJSON) | off     |
| `--page-limit <N>`  | Max pages to fetch                             | 10      |
| `--page-delay <MS>` | Delay between pages                            | 100 ms  |

<!-- END UPSTREAM PAGINATION EXCERPT -->

## Excerpt 3: authentication precedence

<!-- BEGIN UPSTREAM PRECEDENCE EXCERPT -->

### Precedence

| Priority | Source                 | Set via                                 |
| -------- | ---------------------- | --------------------------------------- |
| 1        | Access token           | `GOOGLE_WORKSPACE_CLI_TOKEN`            |
| 2        | Credentials file       | `GOOGLE_WORKSPACE_CLI_CREDENTIALS_FILE` |
| 3        | Encrypted credentials  | `gws auth login`                        |
| 4        | Plaintext credentials  | `~/.config/gws/credentials.json`        |

Environment variables can also live in a `.env` file.

<!-- END UPSTREAM PRECEDENCE EXCERPT -->
