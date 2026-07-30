# REDO Price Bot

A REDO market publishing system for Telegram with reliable multi-destination trade alerts and private operations.

<!-- Add redacted price and trade-alert screenshots here. -->

| | |
|---|---|
| Live bot | [REDO Prices on Telegram](https://t.me/redopricesbot) |
| Audience | REDO community operators and followers |
| Role | Product design, implementation, reliability, and deployment by Nic |
| Status | Active production service |
| Source | Proprietary |

## Product overview

REDO Price Bot publishes a concise recurring market price and can distribute buy/sell notifications to more than one configured Telegram destination. Delivery progress is tracked per destination so a transient failure resumes at the first unfinished target instead of repeating messages everywhere.

## Capabilities

- REDO market identity and value validation
- Scheduled channel publishing
- Primary/fallback market data and cached recovery
- Trade monitoring across supported TON venues
- Multiple alert destinations with validation and deduplication
- Retry resumption from the first failed destination
- Custom alert thresholds and templates
- Private controls, logs summary, and service health

## Architecture

Validated snapshots drive one public price path. Trade events drive a second path through normalization, deduplication, and a destination-aware outbox.

See [Architecture](docs/architecture.md).

## Technology

Python standard library, Telegram Bot API, CoinGecko, DexScreener, TON providers, local private state, and systemd.

## Notable engineering

- Multi-destination progress without duplicate delivery
- Provider fallback with identity checks
- Durable event cursors and alert queue
- Cross-venue trade normalization
- Rate-limit handling for market and Telegram APIs

## Current status

The service reports active. Tests cover destination validation/deduplication, failed-destination resumption, market validation, venue classification, outbox persistence, and menu controls.

This repository has no addresses, provider routes, configuration, source code, state, service unit, or executable content.

[Roadmap](docs/roadmap.md) · [License](LICENSE) · Created by **Nic** ([GitHub](https://github.com/dev-nic-codes))
