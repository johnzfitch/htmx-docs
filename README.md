# HTMX Docs Corpus (Organized Markdown)

This repository contains a curated, recursively crawled (depth 2) HTMX documentation corpus converted from fetched HTML into Markdown and organized by source category.

## What Is Included

- HTMX docs/reference/examples/essays/talk and related API/attributes/headers/events/extensions pages
- Big Sky Software GitHub documentation pages (README/CONTRIBUTING/CHANGELOG/etc.)
- RFCs:
  - RFC 9110 (HTTP Semantics)
  - RFC 9113 (HTTP/2)
  - RFC 9114 (HTTP/3)

## Folder Layout

- `docs/` all corpus documents in a single flattened folder
- `manifests/` URL-to-file mapping and conversion metadata
- `fetch/` raw crawler cache (not tracked in git)

## Internal Index

- Full internal source-to-doc mapping: `INDEX.md`
- Detailed manifest map: `manifests/organized_docs_map.md`

## Naming Convention

Each markdown file name includes flattened context plus the original fetch hash suffix:

- `<source>-<category>-<doc-name>__<hash>.md`

Examples:

- `docs/htmx-attributes-hx-get__119edf64.md`
- `docs/github-htmx-blob-master-readme-md__6361b3d4.md`
- `docs/rfc-rfc9110-http-semantics__e593c606.md`

The hash suffix allows deterministic rescans and straightforward source correlation.

## Crawl And Conversion Notes

- Recursive crawl depth: 2
- Source URL list used for organization: `manifests/organized_docs_map.md`
- Machine-readable map: `manifests/organized_docs_map.json`
- HTML to Markdown conversion tool: `pandoc` (`html` -> `gfm`)

## Current Corpus Size

- Total markdown docs: 238
- HTMX docs: 169
- GitHub docs: 65
- RFC docs: 4
