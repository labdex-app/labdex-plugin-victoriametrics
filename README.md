# VictoriaMetrics / Prometheus

A [labdex](https://github.com/reykimedev/labdex) plugin. Host status from the `up` metric (down when every target of a host is down), plus CPU and memory from node_exporter for the host page. Works with VictoriaMetrics and Prometheus (the Prometheus query API).

**Version** 1.0 · **Works with** labdex >=1.3,<2 · **Plugin id** `victoriametrics`

> [!WARNING]
> Built with AI, for home labs only: labdex and its plugins were written largely with an AI
> coding assistant (Claude), directed and reviewed by a human. They haven't had an independent
> security audit and may contain security problems. Run them on a trusted home network.

## Install

It ships with labdex: **Plugins › Marketplace**, then *Install* (nothing is downloaded). Updates arrive through the official Marketplace (signed with the labdex project key).

## Settings

| Setting | Notes |
| --- | --- |
| URL | Base URL of VictoriaMetrics (single node or vmselect …/select/0/prometheus) or Prometheus |
| Authentication |  |
| User name |  |
| Password |  |
| Bearer token |  |
| Check the TLS certificate |  |
| Status query | Returns 1 (up) or 0 (down) per target, e.g. up{job=~"node/blackbox"} |
| Label that names the host | Its value (address, name or FQDN, with or without :port) is matched to inventory hosts |
| CPU query | Per host, in %; empty = no CPU |
| Memory query | Per host, in %; empty = no memory |

## Actions

- **Check connection** (run)
- **Read host status** (run): Asks for the status query and reports each matched host

## Releasing

Bump `version` in `plugin.yaml`, add a `## <version>` section to `CHANGELOG.md`, commit, then
publish a GitHub release tagged `v<version>` (web UI, or `gh release create v<version> --target main --notes ""`).
The release workflow signs the plugin with the `LABDEX_SIGNING_KEY` secret and attaches `victoriametrics-<version>.zip` to a GitHub release.
