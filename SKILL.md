---
name: nxt-pulse-agent
description: "A highly proactive agent skill (NXT) that manages user energy levels and task prioritization with ADHD micro-stepping support."
version: 0.2.0
---

# Next Pulse Agent (NXT) v0.2.0

This skill transforms your agent into a proactive partner that understands energy fluctuations (especially for ADHD users) and manages tasks through "Pulse Checks" instead of rigid reminders.

## 🌟 Key Features

- **Energy-Aware Nudging**: Detects user energy status (🟢/🟡/🔴) and proactively suggests moving complex tasks to "Hyperfocus Windows".
- **"Just 2 Minutes" Mode (ADHD)**: When in 🔴 (Low Energy), the agent proposes a single micro-step (max 2 min effort) to break inertia without burnout.
- **Critical Override**: Automatically bypasses "Snooze" mode for deadlines within 6 hours.
- **Audit Trail (Transparency)**: Every proactive decision (Nudges, Overrides) is logged with reasoning in `memory/pulse-history.jsonl` for admin transparency.
- **Visual Feedback**: Uses a color-coded pulse system to reduce cognitive load during fatigue.

## 🛠 Configuration

- `ENERGY_CHECK_TRIGGER`: LLM-based sentiment analysis of recent logs.
- `HYPERFOCUS_WINDOW`: Preferred time for deep work (default: 09:00 - 12:00).
- `PULSE_COOLDOWN`: 4 hours (Prevents nudge fatigue).
- `CRITICAL_DEADLINE_THRESHOLD`: 6 hours.
- `EMERGENCY_MODES`: Support for "Sick" or "Emergency" status to silence all nudges.

## 💻 Logic Engine (`pulse.js`)

The skill includes a Node.js helper to manage state and avoid "nudge fatigue":
- **Cooldown Management**: Only triggers a full pulse check every 4 hours unless a critical deadline is detected.
- **Audit Logging**: Records reasoning for every proactive nudge to ensure admin transparency.
- **State Persistence**: Tracks the last pulse time in `memory/pulse-state.json`.

## 🚀 Workflow

### 1. The Startup Pulse & Autonomous Logic
At the start of every session, the agent analyzes:
1. **Critical Override**: Check for any deadlines in `< 6 hours`. If found, bypass Snooze and alert immediately.
2. **Sentiment-Based Energy**: Gauges energy from recent interaction logs and context.
3. **Visual Status**: Displays energy pulse (🟢/🟡/🔴).

### 2. The Smart Nudge & Micro-Steps
Instead of complex questions, the agent provides a single, logical next step:
- If Energy is 🟢/🟡: Suggests a main task.
- If Energy is 🔴: Triggers **"Just 2 Minutes"** mode (e.g., *"You seem drained. Instead of the whole task, just open the file for 2 minutes and see how it feels?"*).

### 3. Adaptive Reflection & Transparency
When a task is marked complete:
1. If energy is 🔴, skip reflection.
2. If energy is 🟢/🟡, ask for a 1-sentence lesson learned.
3. **Audit Log**: All logic paths taken are logged for user/admin review.

### 4. Safety & Efficiency
- Intent-based detection (doesn't rely only on hashtags).
- Shadow Agent reasoning: Simulates choices internally before presenting the best path.

## 🔍 Data Sources & Integration

To function effectively, the Proactive Pulse Agent is designed to interface with standard OpenClaw data structures:

1.  **Session & Daily Logs**: Analyzes recent interactions and daily logs to determine current user energy levels and context.
2.  **Long-Term Memory**: Consults curated memory files (e.g., `MEMORY.md`) to align with long-term preferences and established routines.
3.  **Knowledge Graphs / Ontology**: Interfaces with structured entity data to understand the relationships between different tasks and high-level projects.
4.  **Calendar & Task Managers**: Integrates with local or API-based calendars to identify upcoming deadlines and trigger "Critical Override" logic.
5.  **Contextual Metadata**: Monitors user-defined context (such as health or focus markers) to adjust nudging sensitivity and timing.

---
Created for the OpenClaw community to foster high-performance agent-user partnership.

[GitHub Repository](https://github.com/adnxone/nxt-pulse-agent)
