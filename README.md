# Elastic Integration Cribl Packs

Importable [Cribl](https://cribl.io) **Packs** that align raw data to the input format
each official [Elastic Agent integration](https://github.com/elastic/integrations)
expects — so Elastic's stock ingest pipeline does all the field parsing/ECS mapping.

Each Pack:
- **Routes** a source (filter on `sourcetype` / `__inputId`),
- **reshapes** the event to the integration's expected wire format,
- tags **`_dataId=logs-<dataset>`** so Cribl's Elastic destination delivers it to the
  right data stream and the integration pipeline fires.

> The Pack does the transform + routing. It does **not** ECS-map fields — that's
> intentional; the Elastic integration pipeline owns parsing.

## Install

**Via Cribl Copilot / MCP or API — from URL:**
```
stream_install_pack(source="https://raw.githubusercontent.com/<owner>/elastic-cribl-packs/main/<file>.crbl")
```

**Via Cribl UI:** Manage Packs → Add → Import → upload the `.crbl`, then **Commit & Deploy**.

## Catalog

See [`CATALOG.md`](./CATALOG.md) / [`catalog.json`](./catalog.json). `validated: live`
means the output was round-tripped through a real Elastic stock pipeline; `generated`
means it was built from the integration spec and should be round-trip checked before production.

## How these are generated

Built from a structured database of `elastic/integrations` (data streams, expected
input formats, ingest pipelines, raw samples). Regenerated when the upstream catalog refreshes.
