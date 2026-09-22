<div align="center">

<a href="https://sivletlabs.github.io">
  <img src="https://sivletlabs.github.io/assets/logo.png" width="96" height="96" alt="SivletLabs" style="border-radius: 50%;">
</a>

# ⚡ SivletLabs
### System-1 Decision Models & Evaluation Infrastructure for Autonomous Agents

[![Website](https://img.shields.io/badge/Website-sivletlabs.github.io-00f0ff?style=for-the-badge&logo=google-chrome&logoColor=black)](https://sivletlabs.github.io)
[![Gymnasium Compliant](https://img.shields.io/badge/RL-Gymnasium--Compliant-10b981?style=for-the-badge&logo=openai&logoColor=white)](https://github.com/SivletLabs/jev-eval)
[![x402 Micropayments](https://img.shields.io/badge/Protocol-x402%20EIP--3009-blueviolet?style=for-the-badge)](https://sivletlabs.github.io#x402)
[![Tokenomics](https://img.shields.io/badge/Deflationary-100%25%20Buyback%20%26%20Burn-ff3838?style=for-the-badge)](https://sivletlabs.github.io#tokenomics)

<p align="center">
  <b>Typed decisions. Calibrated probabilities. Pay-per-call via x402. Protocol revenue buys back & burns the token.</b>
</p>

---

</div>

## 🏛️ What We Build

Most autonomous AI agents suffer from the **"Autoregressive Trap"**: using 70B+ chat LLMs for discrete decisions (routing, tool selection, guardrails, DOM clicks). This incurs 800ms–2500ms latency, high cost, and uncalibrated probabilities.

**SivletLabs** builds the cognitive dual-system stack for agents:

```
                  ┌─────────────────────────────────────────────────────────┐
                  │                 Autonomous Agent System                 │
                  └───────────────┬─────────────────────────┬───────────────┘
                                  │                         │
                    System-1 (Spinal Reflex)    System-2 (Deliberation)
                                  │                         │
                  ┌───────────────▼─────────┐   ┌───────────▼───────────────┐
                  │    Sivlet-Jev Model     │   │   Heavy Autoregressive    │
                  │  (Single-Pass Forward)  │   │       Reasoning LLM       │
                  │   Latency: ~12ms        │   │    Latency: 800ms-3000ms  │
                  └───────────────┬─────────┘   └───────────────────────────┘
                                  │
                  ┌───────────────▼─────────────────────────────────────────┐
                  │  jev-eval: Gymnasium RL Benchmark & Calibration Score   │
                  │  Strictly Proper Scoring (Log / Negative Brier / Spher) │
                  └───────────────┬─────────────────────────────────────────┘
                                  │
                  ┌───────────────▼─────────────────────────────────────────┐
                  │  x402 Micropayment Gateway (Pay-per-decision in USDC)   │
                  └───────────────┬─────────────────────────────────────────┘
                                  │
                  ┌───────────────▼─────────────────────────────────────────┐
                  │  100% Net Revenue -> TWAP Buyback & Burn ($SIVLET)      │
                  └─────────────────────────────────────────────────────────┘
```

---

## 🔬 Core Ecosystem Projects

| Repository / Module | Description | Status |
| :--- | :--- | :---: |
| [**jev-eval**](https://github.com/SivletLabs/jev-eval) | Gymnasium-compatible RL simulation, GAE buffer engine, and evaluation benchmark for discrete System-1 policies. | **v0.2.0 Active** |
| [**Sivlet-Jev Engine**](https://github.com/SivletLabs/jev-local) | Non-autoregressive forward scoring with KV-cache truncation (`trim_prompt_cache`), providing **24.3×** speedup. | **Active** |
| [**x402 Protocol Service**](https://sivletlabs.github.io#x402) | Machine-native HTTP 402 pay-per-call API using EIP-3009 offline zero-gas authorization on Base L2. | **Live Spec** |
| [**sivletlabs.github.io**](https://sivletlabs.github.io) | Official portal, interactive simulation sandbox, live telemetry, and technical litepaper. | **Live** |

---

## 📈 Academic Benchmark Highlights (8x8 Maze Navigation)

Evaluated under sequential MDP $\mathcal{M} = \langle \mathcal{S}, \mathcal{A}, \mathcal{P}, \mathcal{R}, \rho_0, \gamma \rangle$ ($N=10, T=25, \gamma = 0.99$):

| Policy Candidate | Win Rate | Cumulative Return ($G$) | Discounted Return ($G_{0.99}$) | Mean Horizon ($T$) | Latency ($P_{50}$) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **HttpPolicy (`jev-latest`)** | **100.0%** | **+9.84 ± 0.00** | **+8.51** | **16.0 steps** | **12.5 ms** |
| **OraclePolicy** (Theoretical Ceiling) | **100.0%** | **+9.84 ± 0.00** | **+8.51** | **16.0 steps** | **0.05 ms** |
| **RandomPolicy** (Uniform Baseline) | 0.0% | -0.20 ± 0.00 | -0.18 | 20.0 (Timeout) | 0.02 ms |

> *Proven*: With anti-oscillation state augmentation and strictly proper scoring, Sivlet-Jev matches the theoretical ground-truth oracle path length and reward ceiling.

---

## 🔄 Closed-Loop Protocol Economics

```
[Agent Invocation] ──> [x402 USDC Micropayment] ──> [Protocol Treasury]
                                                             │
                                                     (Automated Keeper)
                                                             │
                                                             ▼
[0x0...dEaD Burn Address] <── [100% Uniswap v3 TWAP Buyback $SIVLET]
```

1. **Machine-Native Micropayments**: Agents pay $0.0005–$0.001 USDC per decision via RFC 7231 HTTP 402 with zero API key friction.
2. **Autonomous TWAP Buyback**: 100% of net protocol revenue in USDC triggers automated Uniswap v3 TWAP market purchases.
3. **Provable Deflationary Burn**: All repurchased `$SIVLET` tokens are sent directly to `0x000000000000000000000000000000000000dEaD`.

---

## 🔗 Quick Links & Resources

- 🌐 **Official Website**: [https://sivletlabs.github.io](https://sivletlabs.github.io)
- 📄 **Technical Litepaper**: [Read Litepaper](https://sivletlabs.github.io#litepaper)
- 📊 **RL Benchmark Repo**: [SivletLabs/jev-eval](https://github.com/SivletLabs/jev-eval)
- 🛠️ **x402 Service Documentation**: [x402 Integration Spec](https://sivletlabs.github.io#x402)
- 💬 **Farcaster & X**: [@SivletLabs](https://x.com/SivletLabs)

---

<div align="center">
  <sub>© 2026 SivletLabs. Open-source decision intelligence for autonomous agent ecosystems.</sub>
</div>
