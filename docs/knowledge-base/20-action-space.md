# Action Space

**URL:** `/app/actionSpace` (entry)
**Access:** Authenticated + corp-connected users
**Home tile:** Action Space — shows Flight(s), Application(s), Agent(s), Prompt(s) stats

## Overview

Action Space is the execution hub for AAIS (AI-Assisted Intelligence Solutions) assets — flights, agents, applications (solutions), and prompts. It shows what's active and what's available to run. The main page is a single-route with 4 content tabs that change both the heading and content. Related sub-routes handle the flight execution interface and AI chat.

---

## Main Page (`/app/actionSpace`)

**Section heading:** Changes per active tab (see below)
**Nav bar:** Flights | Agents | Applications | Prompts

### Tab: Flights — "Flight Space"

| Section | Content |
|---------|---------|
| Active AAIS Flights | "Currently there are no active flights" |
| Available AAIS Flights | "No Flights Found" |

### Tab: Agents — "Agent Space"

| Section | Content |
|---------|---------|
| Most Used AAIS Agents | "No Agents Found" |
| Available AAIS Agents | "No Agents Found" |

### Tab: Applications — "Solution Space"

| Section | Content |
|---------|---------|
| Most Used AAIS Applications | "No Application Found" |
| Available EAI Applications | "No Application Found" |

### Tab: Prompts — "Prompt Space"

| Section | Content |
|---------|---------|
| Most Used AAIS Prompts | "No Prompts Found" |
| Available AAIS Prompts | "No Prompts Found" |

### Sidebar

- **My Profile** card (CC 10,000, Create Referral Key)
- **My Messages** panel ("No Records Found")

---

## Sub-Route: Flight Launchpad (`/app/flight`)

**Section heading:** AgenticBlue Flight Launchpad
**Nav bar:** Home icon only (no text tabs)

### Layout

- **Left sidebar:** "My Profile" card + "My Messages" panel with a **slider** toggling between:
  - My Messages tab
  - Flight Team tab

### Main Content: Active AAIS Flight

Displays the currently active flight with:

| Element | Details |
|---------|---------|
| Flight image | Placeholder image (no flight assigned yet) |
| AI asset image | Neural network diagram icon |
| Open Items list | Review Response, Review 4 leads, 8 follow up calls, 2 visits |
| Instruction to User | "----" (no instruction set) |
| AI Asset Productivity | spinbutton (`gainValue`, default: 0) + "Manual Hours" label |
| Gain display | "A **NaN x** Gain" (NaN until value entered) |
| Save button | Submits productivity value |

> **Note:** The open items list (Review Response, Review 4 leads, 8 follow up calls, 2 visits) appears to be sample/placeholder data from the org's active flight template.

---

## Sub-Route: Chat Mode (`/app/chatMode`)

**Section heading:** Chat
**Nav bar:** AI Assets | Action Space | Agents | Chat | BLC Exchange

### Layout

- **Left sidebar:** "Chat History" panel
  - Empty state: "There is no previous chat history"
  - "New Chat" button
- **Main panel:** Chat interface

### Chat Interface

| Element | Details |
|---------|---------|
| AI Assistant name | **Mentoha** |
| Greeting | "What can I do for you ?" |
| Message input | Textbox placeholder: "Send a message..." |
| Send button | Icon button to submit message |

> Mentoha is the AI agent for conversational interaction. Chat history persists per session.

---

## Sub-Routes Access Map

| Route | Status | Notes |
|-------|--------|-------|
| `/app/actionSpace` | accessible | Main hub with 4 content tabs |
| `/app/flight` | accessible | Active flight launchpad |
| `/app/chatMode` | accessible | Mentoha AI chat interface |
| `/app/flightDirector` | redirect:/home | Requires higher role (build flights) |
| `/app/launchpad` | redirect:/home | Requires higher role |

---

## Terminology

| Term | Meaning |
|------|---------|
| AAIS | AI-Assisted Intelligence Solution |
| EAI | Enterprise AI |
| Flight | An active multi-step AI workflow execution |
| Flight Space | The tab view of available/active flights |
| Agent Space | The tab view of available/active agents |
| Solution Space | The tab view of available/active applications |
| Prompt Space | The tab view of available/active prompts |
| Mentoha | The built-in conversational AI agent |

---

## Screenshots

| File | Description |
|------|-------------|
| `screenshots/20-action-space-overview.png` | Action Space — Flights tab (Flight Space) |
| `screenshots/20-action-space-flight.png` | AgenticBlue Flight Launchpad (`/app/flight`) |
| `screenshots/20-action-space-chat.png` | Chat Mode — Mentoha AI (`/app/chatMode`) |
