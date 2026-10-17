# No-Pit Guide: Google Workspace

[中文版](README.md)

Updated: 2026-10-17

A field guide of Google Workspace integration pitfalls for AI agents and developers. Read the upstream gws skills first, then use this repo as the practical supplement.

This project collects integration problems we actually ran into, our implementation notes, and verifiable external rules. Fixes may combine our own experiments, official docs, and community material, partly searched and edited with AI; we don't claim every method as our invention.
This is an independent collection, not affiliated with or endorsed by Google or the gws project.

## Why this project exists

To be honest, Google is what I fear most when vibe coding.

Whenever Google is involved, every step is a trap. Write a bit, break a bit, retry, start over — burning time and bills along the way. Later I found out Google has its own gws skills. Read them first; they really do save you from quite a few pits. You should definitely give them a try.

But frankly, skills alone are not enough. In practice, Google Drive, spreadsheets, and photo sync keep producing problems all the way through: some are official rules, some are wiring choices, and some were just me not thinking it through back then.

So I organized every pit I broke through into a database for AI to query. When something breaks, look it up: have we seen this problem before? Before starting work, read ahead: what could get in the way?

108 core notes plus 75 repair / follow-up entries, 183 records in total, plus 24 quick-lookup topics as the entry point. Much of it is personal experience, organized with AI help. The numbers are records from the time, not guarantees about the present. If something looks off and needs a tweak, let me know — thanks.

## Where to start

- [Entry point for AI agents](AGENTS.md): read the upstream skills first, then check PITFALLS and the 183-record index.
- [30-second Quick Start](QUICKSTART.md): three checks for humans, three pages for AI.
- [Troubleshooting](TROUBLESHOOTING.md): the condensed first-look page; full context links back to the original IDs.
- [Full record index](catalogue/INDEX.md): 108 core notes and 75 repair / follow-up entries with original IDs preserved.
- [108 core notes](catalogue/records.md): connections, retries, batches, SHA, testing, scheduling, mapping — each with problem / parameters, handling, and verification limits.
- [Repair notes GP-T-01 to GP-T-38](catalogue/repairs-01-38.md) and [GP-T-40 to GP-T-76](catalogue/repairs-40-76.md): handling notes from real integration and delivery work, with resolved / partially-handled / to-verify limits.
- [PITFALLS.md](PITFALLS.md): 24 quick-lookup topics, entry point only, not a replacement for the full records.
- [SOURCES.md](SOURCES.md): sources, versions, evidence limits, and acknowledgments.
- [gws upstream excerpts](third_party/gws-cli/README-excerpts.md): schema, pagination, and credential precedence excerpts, Apache-2.0.
- [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md): scope of third-party licenses.

183 source records in total, keeping duplicates and follow-ups linked. They are not 183 independent Google bugs.
Core notes also include internal parameters, contracts, and external rules already present in the source table, each labeled by type; no row is dressed up as a personal experiment it wasn't.
This round is organized from our own existing notes only, with no new external research. Verbatim upstream excerpts stay in the appendix, not the main content.

## Prerequisites

If you use the gws CLI, first install it per the [upstream installation guide](https://github.com/googleworkspace/cli#installation), then pick the skills you need per the [skills guide](https://github.com/googleworkspace/cli#ai-agent-skills).
Read `gws-shared` first, then the matching service guides such as `gws-drive`, `gws-sheets`, `gws-docs`. Pinned links (same commit as SOURCES, `705fb0e`): [skills index](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/docs/skills.md), [gws-shared](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-shared/SKILL.md), [gws-drive](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-drive/SKILL.md), [gws-sheets](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-sheets/SKILL.md), [gws-docs](https://github.com/googleworkspace/cli/blob/705fb0ecac6f4249679958f6325b809b63fdde17/skills/gws-docs/SKILL.md).

Installing the CLI, installing skills, and completing OAuth are three different steps. Actual commands follow the `--help` and `gws schema` of the version you installed.
If you use the SDK / API directly, the general integration experience here still applies. Note the gws project states it is not an officially supported Google product.
Reading this project or installing any skill does not grant you access to any account, file, or production environment.

## Minimal safe workflow

1. Confirm account, environment, target resources, and actual authorization; start with read-only checks.
2. Only write small authorized batches; scale up after verifying content and mapping against Google.
3. If the result is unclear, read back first; don't blindly replay a create or append.
4. Record version, stage, status, and reason. Don't record tokens, resumable session URIs, or customer data.
5. Keep simulation, live runs, human acceptance, and untested scope labeled separately.

## License

Except for clearly marked third-party content, original text, arrangement, and examples in this project — where we hold the rights — are under the [MIT License](LICENSE).
Third-party content follows its own licenses; this project's MIT does not replace Apache-2.0, Creative Commons, or other applicable terms.

Currently the only third-party material included is `third_party/gws-cli/`: the excerpt file and its license copy are Apache-2.0; see the [third-party notices](THIRD_PARTY_NOTICES.md).
Other Google docs, community answers, and repos are referenced by link plus our own summaries only — nothing copied in full.

## Scope and maintenance

This is a record-by-record organization of an existing source table, not a complete list of all Google issues, and results may differ across versions or environments.
Statuses and parameters in the entries are historical descriptions; this documentation round ran no live re-verification, so nothing here describes the current state of production environments.
Where the original search trail is incomplete, we say so instead of passing off today's official docs as the source used back then.

For new issues, first classify: Google rule, gws / SDK behavior, or application integration problem; update the existing entry for similar problems.
Before including third-party text or code, confirm the file, pinned version, and license, and keep the required notices and modification marks; otherwise keep a verifiable link or leave it out.
Private source notes, customer data, environment configs, conversation logs, and Git history are not part of this package.
