# Benchmarks ⚡

A modular, containerized benchmarking suite and reproducible performance lab comparing web tooling, package managers, runtimes, and frameworks. Findings and datasets feed directly into analyses published on [jericbas.github.io](https://jericbas.github.io).

---

## 🐳 Containerized Execution Philosophy

All official benchmarks execute inside **ephemeral Docker containers** to ensure rigorous reproducibility, scientific fairness, and isolation:

- **Clean-Slate Isolation**: Containers are spun up fresh per run, guaranteeing no residual host disk caches, global modules, or ambient environment pollution.
- **Resource Pinning**: Consistent CPU (`--cpus`) and memory (`--memory`) quotas prevent host background load spikes from skewing metrics.
- **Cache Control**: Cold-cache vs. warm-cache benchmarks are explicitly controlled via isolated Docker volume mounts.
- **Public Reproducibility**: Anyone can clone the repo and run the exact same containerized benchmark runner to verify numbers reported on the blog.

---

## 🔬 Benchmark Tracks

1. **Package Managers & Runtimes**
   - Cold vs. warm install speed
   - Lockfile resolution timing
   - Disk consumption (`node_modules` vs. content-addressable store)
   - Targets: `bun`, `pnpm`, `yarn` (Berry/v1), and `npm`

2. **Frontend Frameworks & Bundlers**
   - Scaffold-to-build latency
   - Production bundle size & asset breakdown
   - Hydration and client render performance
   - Targets: React, Vue, Vite, and modern alternatives

3. **Micro-benchmarks & System I/O**
   - File system traversal and parsing overhead
   - HTTP throughput and JSON serialization

---

## 📁 Repository Structure

```
benchmarks/
├── docker/                   # Base benchmark runner Dockerfiles
│   ├── Dockerfile.node       # Node.js + npm / pnpm / yarn base
│   └── Dockerfile.bun        # Bun runtime base
├── suites/
│   ├── package-managers/     # Package manager installation benches
│   └── frameworks/           # Framework build & hydration benchmarks
├── results/                  # Raw JSON/CSV output and run logs
├── scripts/
│   ├── run-docker.sh         # Ephemeral Docker benchmark orchestrator
│   └── format-results.mjs    # Generates markdown tables for blog devlogs
└── README.md
```

---

## 🚀 Running Benchmarks

### 1. Ephemeral Container Run (Official & Reproducible)

Execute the full suite or target specific benchmarks inside isolated containers:

```bash
# Run package manager benchmark suite inside Docker
./scripts/run-docker.sh --suite package-managers

# Run framework build suite with pinned resources
./scripts/run-docker.sh --suite frameworks --cpus 4 --memory 4g
```

### 2. Bare-Metal Execution (Local Rapid Iteration)

For quick development iteration on your local machine:

```bash
# Run bare-metal without containerization overhead
./scripts/run-baremetal.sh --suite package-managers
```
