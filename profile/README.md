# ArgusChain 🔭

**Hybrid fraud detection for the Stellar DEX** — detecting wash trading and artificial volume using Benford's Law combined with ensemble machine learning.

---

## 🎯 Mission

ArgusChain protects Stellar DEX users from wash trading and market manipulation by providing transparent, verifiable fraud detection that's accessible on-chain and off-chain.

---

## 📦 Repositories

### 1. **[Arguschain-Core](https://github.com/Arguschain/Arguschain-Core)** — Detection Engine
Python-based fraud detection system that analyzes trades for wash trading patterns.

**Features**:
- Benford's Law digit distribution analysis (chi-square, Z-scores, MAD)
- Graph-based wash-ring detection (Tarjan SCC algorithm)
- 35-feature ML engineering (Benford, patterns, volume, timing, graph)
- Ensemble model training (Random Forest, XGBoost, LightGBM)
- RiskScore computation (0-100 scale)

**Setup**: `python cli.py serve`

---

### 2. **[Arguschain-Contracts](https://github.com/Arguschain/Arguschain-Contracts)** — On-Chain Registry
Soroban smart contracts that store and verify fraud detection scores on the Stellar blockchain.

**Features**:
- RiskScore on-chain storage (wallet, asset pair, score)
- Read-only access for other Soroban contracts (composability)
- Zero-knowledge proof verification
- Event emission for off-chain indexing

**Build**: `cargo build --target wasm32-unknown-unknown --release`

---

### 3. **[Arguschain-Dashboard](https://github.com/Arguschain/Arguschain-Dashboard)** — User Interface
Full-stack web application for visualizing fraud scores and managing subscribers.

**Features**:
- REST API: `/scores`, `/alerts`, `/assets/risk-ranking`, `/metrics`
- Risk score dashboard with real-time updates
- Asset risk rankings table
- Alert notifications

**Setup**: `docker compose up --build`

---

## 🔄 How They Work Together

```
Stellar Horizon API (trades)
        ↓
Arguschain-Core (analyze + score)
    ├→ Arguschain-Contracts (store on-chain)
    └→ Arguschain-Dashboard (display UI)
```

**Data Flow**: Core ingests trades → detects fraud → Contracts stores on-chain → Dashboard displays UI

---

## 🚀 Quick Start

### Clone All Repos
```bash
git clone https://github.com/Arguschain/Arguschain-Core
git clone https://github.com/Arguschain/Arguschain-Contracts
git clone https://github.com/Arguschain/Arguschain-Dashboard
```

### Start Core Detection
```bash
cd Arguschain-Core
pip install -r requirements.txt
python cli.py serve
```

### Run Dashboard
```bash
cd Arguschain-Dashboard
docker compose up --build
# Dashboard: http://localhost:3000
```

---

## 📊 Stats

| Metric | Value |
|--------|-------|
| **Total Commits** | 102 |
| **Repositories** | 3 |
| **Languages** | Python, Rust, TypeScript |
| **Contributors** | 5+ |
| **Test Coverage** | 70%+ |

---

## 🌊 Wave Program

Contribute through our **Wave Program** — 2-week sprints with scoped issues.

**Work Types**: Bug fixes, features, documentation, testing, performance

**Get Started**:
- Pick an issue: `/wave-5` label
- Submit PR with acceptance criteria
- Merge after 2 approvals

**Recognition**: Bronze/Silver/Gold tiers, GitHub badges, swag

---

## 🔗 Integration

Query scores on-chain from any Soroban contract:
```rust
let score = get_score(wallet, asset_pair);
if score.score > 80 {
    // Block or gate access
}
```

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/Arguschain)
- **Discord**: [Community](https://discord.gg/arguschain)
- **Discussions**: [Ask questions](https://github.com/orgs/Arguschain/discussions)

---

## 🎉 Highlights

✨ **Building on Stellar** — Native Soroban integration

✨ **Math-First** — Benford's Law + ensemble ML

✨ **Community-Driven** — Wave Program for contributors

✨ **Open Source** — Fully transparent detection logic

---

**Protecting the Stellar DEX from market manipulation. 🛡️**

[Core](https://github.com/Arguschain/Arguschain-Core) | [Contracts](https://github.com/Arguschain/Arguschain-Contracts) | [Dashboard](https://github.com/Arguschain/Arguschain-Dashboard)
