---
layout: default
title: Giuseppe C. - Systems Engineer
---

# Giuseppe C.

Systems engineer with 30+ years building production software. I design and build distributed systems from the metal up - blockchain indexers, REST APIs with custom cluster protocols, bare-metal infrastructure automation.

Based in Douglas, Isle of Man.

---

## Current Work: BlockTailor

A production multi-chain blockchain infrastructure platform indexing BTC, LTC, ETH, and TRON (8 chain/network pairs). 

Full stack: C indexer, Go API server, Go+HTMX operations UI, push-based monitoring agent, 37 Ansible playbooks, and a CI/CD pipeline with security scanning and integration testing.

### Blockchain Indexer (C)

- Parallel block indexer with producer-consumer concurrency and asynchronous write coalescing across 4 blockchain networks
- Custom storage schema optimized for lexicographic prefix scans and zero-copy deserialization
- High-throughput in-memory UTXO cache (~1 GB) with eviction strategy tuned for blockchain spend patterns
- Chain reorganization detection and recovery across all 4 networks, with audit logging and downstream consumer notification
- Tamper-evident integrity verification layer for indexed data
- Real-time block ingestion via ZMQ (BTC/LTC), WebSocket (ETH), and gRPC/ZMQ for TRON, with Unix domain socket IPC to downstream consumers

### REST API Server (Go)

- 280+ API routes with 5 drop-in compatibility layers: Mempool.space, Etherscan, TronGrid, JSON-RPC (ethers.js), native REST. Serves ~3,000 QPS on standard hardware
- Custom gossip protocol from scratch: length-prefixed binary wire format, HMAC-SHA256 per-message auth, dual-secret rotation, mTLS, member state machine
- Webhook delivery with SSRF protection (dual-time DNS validation against rebinding attacks), per-URL circuit breakers, exponential backoff, dead letter queue
- Dual-instance database rotation enabling zero-downtime reloads during index updates
- Per-app audit log with cross-node replication for every database write
- Singleflight deduplication, memory pressure guard, adaptive per-chain rate limiting

### Operations UI (Go + HTMX)

- Cluster monitor with real-time gossip-based node health and cross-instance state visibility
- Infrastructure monitoring (CPU/memory/disk/ZFS/SMART per VM) with remote command execution and operator confirmation workflows
- Multi-tenant admin: user lifecycle, API key management, chain enable/disable configuration, per-user debug tracing
- Subscriptions dashboard: webhook delivery logs, replay, circuit breaker status, event history
- Real-time analytics: request volume, error rates, p50/p99 latency, per-chain RPS with live Chart.js graphs
- Chain repair and recovery workflows with operator confirmation controls
- Resource management dashboards (TRON staking, energy delegation)
- Regression test runner with live progress streaming, Telegram alerting configuration
- SSE real-time updates, role-based access control (user/admin/devops), background worker system

### Monitoring Agent (Go)

Push-based agent on all VMs. ZFS health with fill-rate prediction, SMART disk health (SATA + NVMe), PSI pressure stalls, RocksDB sizes. Remote command executor with validated whitelist. Async RocksDB compaction with real-time progress tracking.

### Infrastructure & CI/CD

- 37 Ansible playbooks covering full lifecycle from bare-metal (OVH API) through Proxmox VE, ZFS pools, VM lifecycle, blockchain nodes, mTLS cluster certificates, NGINX
- CI/CD with 10 parallel GitHub Actions jobs: C tests with Valgrind, Go tests with race detector, integration tests (Docker), CodeQL + Gosec + TruffleHog security scanning, performance benchmarks
- systemd hardening: NoNewPrivileges, ProtectSystem=strict, polkit-based privilege scoping

### Quality & Security

- 238-endpoint regression test framework with exact, structural, and plaintext comparison modes, plus live A/B server comparison adapted for continuously-changing blockchain state
- Formal penetration test: CVSS 9.8 critical found and fixed, 10 findings resolved, risk acceptances documented with NIST/OWASP citations
- 10 production incident postmortems (endianness bugs, IEEE 754 precision loss, race conditions)

---

## Background

Building production software since the late 80s - from DOS and x86 assembly through modern distributed systems. Real-time trading platforms, cryptocurrency payment processing at scale, multi-chain blockchain infrastructure.

**Big Picture Software (2016 - 2023):** Built API endpoints for payment systems and blockchain networks (BTC, ETH, Polygon, EOS). Scalability and bottleneck resolution on Kubernetes (GCP). MongoDB sharding for high-throughput transaction processing. Won 1st place at EOS/Google hackathon; 4th at Solana hackathon.

**Investnet Italia / IWBank (2001 - 2008):** Real-time trading systems. Live market data charts, order book, trading interface. Early mobile trading prototypes (Blackberry, Nokia).

---

## Technical Profile

**Languages:** C, Go, JavaScript/TypeScript, SQL, Python, C#

**Systems:** RocksDB, SQLite, LevelDB, Redis, MongoDB, PostgreSQL

**Protocols:** gRPC, Protobuf, ZMQ, WebSocket, SSE, JSON-RPC

**Infrastructure:** Proxmox VE, ZFS, Ansible, systemd, HAProxy, NGINX, Docker, Kubernetes, GitHub Actions

**Cloud:** Google Cloud Platform

**Security:** Penetration testing, OWASP, SSRF protection, mTLS, HMAC authentication, circuit breakers

---

## Contact

giuseppe@zmcontract.com
