# 💓 NXT Pulse Agent v0.3.1

> **A neuro-inclusive, energy-aware proactive partner for OpenClaw.**

NXT Pulse Agent (NXT) is a high-performance skill designed to transform your AI assistant into a respectful, proactive partner. Built with ADHD management principles and Hermes-inspired logic, it prioritizes your mental energy over rigid schedules using **Semantic Urgency Detection**.

[![GitHub license](https://img.shields.io/github/license/adnxone/nxt-pulse-agent)](https://github.com/adnxone/nxt-pulse-agent/blob/main/LICENSE)
[![OpenClaw NXT](https://img.shields.io/badge/OpenClaw-NXT-blueviolet)](https://docs.openclaw.ai)
[![Version](https://img.shields.io/badge/version-0.3.1-green)](https://clawhub.ai/adnxone/nxt-pulse-agent)

---

## 🌟 Key Features

- **Semantic Energy Detection**: Uses LLM reasoning to detect user energy (🟢/🟡/🔴) from natural language cues and session context, rather than simple keywords.
- **"Just 2 Minutes" Mode**: When you're in 🔴 (Low Energy), the agent proposes a single micro-step (max 2 min effort) to break executive dysfunction without triggering burnout.
- **LLM-Driven Critical Override**: Automatically detects deadlines and high-pressure contexts semantically. Bypasses "Snooze" when an urgent task is identified.
- **Admin Audit Trail**: Every proactive decision is logged in `memory/pulse-history.jsonl` for full transparency and review.
- **Multi-Language Support**: Logic and detection are language-independent, supporting RO, EN, ES, FR, and more via semantic reasoning.

## 🚀 Getting Started

### Installation
```bash
clawhub install adnxone/nxt-pulse-agent
```

### Configuration
The agent uses `pulse.js` to manage state and cooldowns.
- `PULSE_COOLDOWN`: 4 hours (default).
- `CRITICAL_THRESHOLD`: 6 hours (default).

## 🔍 How it Works
The NXT Pulse Agent acts as an executive function support layer. 
1. **The Pulse**: At session start, the agent performs a semantic check of logs and `MEMORY.md`.
2. **The Signal**: If a deadline or high energy is detected, the agent triggers the pulse via local state files.
3. **The Nudge**: Based on your detected energy, it suggests a full task or a 2-minute micro-step.

---
Created by [adnXone](https://github.com/adnxone) for the OpenClaw community.
