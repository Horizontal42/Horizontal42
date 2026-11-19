# Andrew Pimenov (@Horizontal42) 👋

**Applied AI Systems & Backend Engineer**  
📍 Saint Petersburg | Remote

I design and build production-grade AI pipelines, resilient asynchronous backends, and low-level engineering tools. My focus is turning complex ML/CV research into deterministic, observable, and cost-efficient business infrastructure.

---

## 🏛️ Commercial Flagship Systems (B2B / Cortex IT — NDA)

### 1. Enterprise Speech Analytics & Voice AI Platform
*End-to-end automated speech processing, speaker diarization, and deterministic compliance auditing for high-volume B2B sales operations.*

- **E2E Audio Pipeline:** Webhook-driven ingestion processing incoming telephony calls via `WhisperX` (`large-v3-turbo`) and `pyannote.audio` for precise agent/client speaker separation and temporal alignment.
- **Deterministic LLM Scoring (0% Flip-Rate):** Solved LLM scoring variance (reduced from a 33% discrepancy rate on identical calls down to **0% flip-rate**) through a hybrid validation engine: LLM extracts verbatim dialogue evidence, followed by programmatic fuzzy text grounding (`difflib.SequenceMatcher`, 0.8 threshold) before scoring rules fire.
- **Decoupled Asynchronous Queues:** Separated Celery task architecture into high-concurrency I/O workers (call download, metadata retrieval, CRM sync) and single-concurrency GPU inference workers with dynamic micro-batching (`batch_size=3`).
- **Memory Leak Mitigation (`ctypes` & `malloc_trim`):** Eliminated memory bloat in long-running GPU workers where Python runtime GC failed to return pages to the OS after large model runs by directly invoking `glibc malloc_trim` / `jemalloc` via `ctypes.CDLL`.
- **CRM Integration & Reporting:** Full bi-directional integration with Bitrix24 REST API for automated deal scoring, feedback summaries, and incremental $O(n)$ SHA1-hashed PDF audit report generation in MinIO (S3).

---

### 2. Corporate RAG & Semantic Search Engine
*Enterprise knowledge retrieval engine for industrial manufacturing catalogs, GOST technical standards, and complex product nomenclature.*

- **Knowledge Base Indexing:** Vectorized 10,000+ pages of dense technical documentation, pricing matrices, and engineering specs into `Qdrant` using `LangChain` with custom document chunking strategies.
- **Search Latency Reduction:** Cut manager lookup times during active sales negotiations from **15 minutes to under 2 seconds** across 130+ concurrent internal users.
- **Guardrailed Retrieval:** High-precision hybrid semantic search backed by metadata filtering and strict context grounding, eliminating hallucinations in mission-critical quotation workflows.

---

### 3. Real-Time Computer Vision & Video Analytics (AgroTech)
*Automated 24/7 multi-camera anomaly detection and physiological event monitoring across agricultural facilities.*

- **Low-Latency RTSP Stream Pipeline:** Ingests live IP camera streams at 1 FPS with CUDA hardware acceleration and OpenCV.
- **Multi-Stage Vision Chain:** Frame reader $\to$ Animal detection (`YOLOv8`) $\to$ Multi-object tracking across camera frames (`ByteTrack`) $\to$ Pose classification (`YOLOv11m-cls`) $\to$ 5-minute sliding window temporal feature extraction.
- **Sub-2-Second Incident Response:** Anomaly classification via `IsolationForest` coupled with an FSM state machine (`NORMAL` $\to$ `WATCH` $\to$ `ALERT` $\to$ `CONFIRMED`), guaranteeing real-time incident alerts in **< 2 seconds** while filtering out ambient noise and false alarms.

---

## 🛠️ Featured Open-Source & Engineering Showcase

| Project | Domain | Architecture & Highlights | Tests / Quality |
| :--- | :--- | :--- | :--- |
| **[aviapars](https://github.com/Horizontal42/aviapars)** | Travel Aggregator & Bot | Asynchronous flight/rail monitoring bot. Dual-tier anti-bot bypass (`curl_cffi` TLS impersonation + isolated Chromium solver in `patchright` subprocesses), residential SOCKS5 relay for ASN datacenter blocks, geometric hub route finder (Haversine detour formula), SQLite in WAL mode, and Circuit Breaker pattern. | **200+ tests**, strict mypy, recorded HTTP fixtures |
| **[netsleuth](https://github.com/Horizontal42/netsleuth)** | Network Diagnostics CLI | Deep network inspection CLI. Non-admin ICMP echo & traceroute on Windows using native `Iphlpapi.dll` (`IcmpSendEcho2`) via `ctypes` with 64-bit struct memory alignment; dynamic OEM codepage detection (`GetOEMCP`); multi-factor weighted VPN leak scoring model. | **857 tests** (44 test suites), rich terminal UI |
| **[summarum](https://github.com/Horizontal42/summarum)** | Desktop Calculator | Cross-platform notepad calculator. Custom recursive AST Pratt parser with natural language filtering; Rust-backed `DataDirGate` security boundary; exact financial math via `decimal.js` preventing IEEE 754 precision bugs. Built on Tauri 2, Rust, and TypeScript. | **259 tests** (Vitest), modular architecture |
| **[freelance-leads-monitor](https://github.com/Horizontal42/freelance-leads-monitor)** | Lead Gen & AI Triage | Autonomous lead acquisition & intelligent AI triage engine. Two-stage LLM qualification pipeline (Mistral + Antigravity CLI), probabilistic PERT timeline analysis, multi-source ingestion across 5 freelance exchanges, SQLite in WAL mode, and real-time FastAPI analytics dashboard. | Async collectors, strict schemas, FastAPI |
| **[LaptopTester](https://github.com/Horizontal42/LaptopTester)** & **[warehouse-master](https://github.com/Horizontal42/warehouse-master)** | Hardware QA & WMS | Industrial hardware diagnostics and warehouse automation. Automated system spec extraction (WMI, smartctl, battery wear, GPU/CPU thermals) paired with interactive QA checklists, two-way Google Sheets API sync, and on-demand 58x40mm thermal barcode label generation via ReportLab. | Deployed to production warehouse floor |

---

## ⚡ Engineering Culture & Core Stack

I prioritize deterministic system behavior, strict type contracts, comprehensive test suites, and transparent operational telemetry over superficial complexity.

- **Languages:** Python (asyncio, typing, ctypes), Rust, TypeScript, SQL
- **AI & Machine Learning:** WhisperX, PyAnnote, LangChain, Qdrant, YOLOv8/v11, ByteTrack, PyTorch, CUDA, Ollama
- **Backend & Distributed Systems:** FastAPI, Celery, Redis, PostgreSQL, SQLite (WAL), Docker, MinIO / S3
- **Low-Level & Desktop:** Win32 API / ctypes, Tauri 2, WMI, Process Isolation, Memory Optimization
- **Engineering Rigor:** pytest, Vitest, CI/CD, Circuit Breakers, Shadow Deployments, Zero-Admin Tooling

---

## 📫 Get in Touch

- **Telegram:** [@horizontal42](https://t.me/horizontal42)
- **Email:** [piminoffandrew@gmail.com](mailto:piminoffandrew@gmail.com)
- **GitHub:** [Horizontal42](https://github.com/Horizontal42)
- **Location:** Saint Petersburg, Russia 📍
