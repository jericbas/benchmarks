# Benchmarks ⚡

A modular benchmarking suite and reproducible performance lab comparing web tooling, package managers, runtimes, and frameworks. Findings and datasets feed into analyses published on [jericbas.github.io](https://jericbas.github.io).

---

## 🔬 Focus Areas

- **Package Managers & Runtimes**: Install speed, cold/warm cache resolution, and disk footprint across `bun`, `pnpm`, `yarn`, and `npm`.
- **Frontend Frameworks & Bundlers**: Scaffold, build times, bundle size, and memory usage across modern stacks.
- **Micro-benchmarks**: Isolated computational and I/O tasks.

---

## 📁 Repository Structure

```
benchmarks/
├── suites/
│   ├── package-managers/     # Package manager installation & resolution benches
│   └── frameworks/           # Framework build & hydration benchmarks
├── results/                  # Raw JSON/CSV output data
├── scripts/                  # Automated runners and reporting utilities
└── README.md
```

---

## 🚀 Usage

Detailed benchmark reproduction steps and automation scripts are documented within each respective suite directory.
