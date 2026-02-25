# GPTBlue Studio (Action Deck)

**URL:** `https://bluecallom.ai/app/actionDeck`
**Access:** All authenticated users (entry dashboard accessible; sub-features require higher tier)
**Section heading:** "GPTBlue Dashboard"
**Home tile:** `GPTBlue Studio` — `tile-active` post-corp-connection (was `tile-disabled` before)

## Overview

GPTBlue Studio is the AI execution hub of BlueCallom. The entry dashboard (`/app/actionDeck`) shows aggregate usage statistics across Prompts, Agents, and Applications. It is the starting point for creating and running AI workflows. Sub-features (Prompt Studio, Agent Studio, Solution Studio, Launchpad, Workspace) are accessible via sidebar navigation within this section.

## Key Flows

### Flow 1: View Usage Dashboard
1. Navigate to `/app/actionDeck`
2. Dashboard shows three stat panels: Your Prompts / Your Agents / Your Applications
3. Each panel shows: Usage (Executions), Productivity (Hours), Feedback (Reports)
4. All stats are 0 for a new account

### Flow 2: Navigate to Sub-Features (expected)
- Click sidebar links to access: Prompt Studio, Agent Studio, Solution Studio, Launchpad, Workspace
- (Sub-feature navigation not captured — no sidebar visible on `/app/actionDeck` for this account level)

## UI Elements

| Element | Type | Purpose |
|---------|------|---------|
| "Your Prompts" panel | Stats panel | Prompt usage metrics |
| "Your Agents" panel | Stats panel | Agent usage metrics |
| "Your Applications" panel | Stats panel | Application usage metrics |
| Home link (house icon) | Link | Navigate to `/home` |
| Help icon (?) | Button | Opens help dialog |

## Stats Panels

Each of the three panels (Prompts, Agents, Applications) displays:

| Metric | Description |
|--------|-------------|
| Usage / Execution(s) | Number of times executed |
| Productivity / Hour(s) | Hours of productivity generated |
| Feedback / Report(s) | Feedback reports submitted |

## Section Sidebar Routes (from JS bundle)

| Nav Item | Route |
|----------|-------|
| GPT Blue (Dashboard) | `/app/actionDeck` |
| Prompt Studio | `/app/promptStudio` |
| Agent Studio | `/app/agentStudio` |
| Solution Studio | `/app/solutionStudio` |
| Launchpad | `/app/launchpad` |
| Workspace | `/app/workspace` |

## Access Restriction

**Post-corp-connection:** The home tile is now `tile-active`. Navigating to `/app/actionDeck` works for all authenticated users.

Sub-feature routes remain restricted (→ `/home`) even after corp connection — these require a higher tier/role:

| Route | Status |
|-------|--------|
| `/app/promptStudio` | → `/home` (restricted) |
| `/app/agentStudio` | → `/home` (restricted) |
| `/app/solutionStudio` | → `/home` (restricted) |
| `/app/launchpad` | → `/home` (restricted) |

## Empty State

All metrics show 0 (no prompts, agents, or applications created yet).

## Screenshots

| File | Description |
|------|-------------|
| `screenshots/04-gptblue-studio-overview.png` | GPTBlue Dashboard — pre-corp state |
| `screenshots/23-gptblue-actiondeck.png` | GPTBlue Dashboard — post-corp state (tile-active, same layout) |
