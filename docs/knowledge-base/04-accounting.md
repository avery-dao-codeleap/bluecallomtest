# Accounting (Rewards / CC Coins)

**URL:** `https://bluecallom.ai/app/accounting`
**Access:** All authenticated users
**Section heading:** "Rewards"

## Overview

The Accounting page tracks the user's CC (Status Coin) balance and transaction history. CC coins are the platform's internal currency — they are consumed when executing AI agents/prompts and awarded for onboarding milestones, referrals, and other activities. The page is part of the "My AgenticBlue Portal" section.

## Key Flows

### Flow 1: View Transaction History
1. Navigate to `/app/accounting` (via "CC balance" link in sidebar or "My rewards" tab)
2. Select transaction category filter (radio buttons)
3. Select time period (combobox: Today / Last 7 days / Last 30 days / Custom)
4. For "Custom": set Start Date and End Date
5. Table updates with matching transactions

## UI Elements

| Element | Type | Purpose |
|---------|------|---------|
| Category radio buttons | Radio group | Filter by transaction type (Time / Prompt / Agents / Flights / Other) |
| Period combobox | Select | Filter by time window |
| Start Date | Date input (disabled unless Custom) | Custom range start |
| End Date | Date input (disabled unless Custom) | Custom range end |
| Status Coin table | Table | Transaction history |
| Pagination (Prev / 1 / Next) | Navigation | Page through transactions |

## Transaction Table Columns

| Column | Description |
|--------|-------------|
| Date | Date of transaction |
| Activity | Description of what triggered the coin change |
| Username | User who triggered it |
| Type | Transaction type code (e.g. "S" = system) |
| Coin Spent | Coins deducted |
| Coin Added | Coins added |
| Balance | Running balance after transaction |

## Sample Data (Observed)

| Date | Activity | Username | Type | Coin Spent | Coin Added | Balance |
|------|----------|----------|------|------------|------------|---------|
| Feb 24, 2026 | account completion | Nam Ho | S | - | 7,500 | 10,000 |
| Feb 24, 2026 | your account initialization | — | S | - | 2,500 | 2,500 |

> New accounts receive 10,000 CC total: 2,500 on initialization + 7,500 on profile completion.

## Filter Options

**Category (radio):** Time | Prompt | Agents | Flights | Other

**Period (combobox):**
- Today (default)
- Last 7 days
- Last 30 days
- Custom (enables Start/End date inputs)

## Empty State

No empty state observed — account had initial coin grants.

## Error States

Not observed.

## Screenshots

- `screenshots/04-accounting-overview.png` — Rewards/Accounting page with transaction history
