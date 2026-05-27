# Elastic Integration Cribl Pack Catalog

3 importable Cribl Packs — one per Elastic integration data stream.
Each Pack routes a source, reshapes it to the integration's expected input, and
tags `_dataId=logs-<dataset>` so Elastic's stock ingest pipeline parses it.

**Validation:** 1 live-validated against a real Elastic pipeline; the rest
are generated from the integration spec and should be round-trip checked before production.

| Integration | Data stream | dataset (`_dataId=logs-…`) | type | wire_format | framing | validated | .crbl |
|---|---|---|---|---|---|---|---|
| proofpoint_on_demand | audit | `proofpoint_on_demand.audit` | logs | `JSON` | websocket | generated | `proofpoint_on_demand__audit.crbl` |
| proofpoint_on_demand | mail | `proofpoint_on_demand.mail` | logs | `JSON` | websocket | generated | `proofpoint_on_demand__mail.crbl` |
| proofpoint_on_demand | message | `proofpoint_on_demand.message` | logs | `JSON` | websocket | live | `proofpoint_on_demand__message.crbl` |
