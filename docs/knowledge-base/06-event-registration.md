# Event Registration

**URL:** `https://bluecallom.ai/app/events/eventRegistration`
**Access:** All authenticated users
**Section heading:** "Event Registration List"

## Overview

The Event Registration page lets users browse and register for upcoming BlueCallom events (workshops, boot camps, etc.). It is part of the "My AgenticBlue Portal" section, accessible via the "Event Registration" tab in the secondary nav bar.

## Key Flows

### Flow 1: Browse Events
1. Navigate to `/app/events/eventRegistration`
2. Table lists upcoming events with columns: Name, Location, Event Start Date, Event End Date, Company, Action
3. Empty state shown when no events: *"There are no upcoming events right now. Please check back soon!"*

### Flow 2: Search Events
1. Type in "Search Event" text box (placeholder: "Search by name")
2. Table filters to matching events

### Flow 3: View Registered Events
1. Click "Registered Events" button (top right of table)
2. Table switches to show only events the user has registered for

## UI Elements

| Element | Type | Purpose |
|---------|------|---------|
| "Search Event" textbox | Text input | Filter events by name |
| "Registered Events" button | Button | Toggle to show only registered events |
| Events table | Table | List of available or registered events |

## Table Columns

| Column | Description |
|--------|-------------|
| Name | Event name |
| Location | Physical or virtual location |
| Event Start Date | Start date/time |
| Event End Date | End date/time |
| Company | Organising company |
| Action | Register / View / Cancel button (expected) |

## Empty State

- Message: "There are no upcoming events right now. Please check back soon!"
- No "Add" or "Create" button — events are managed by the platform/admin

## Error States

Not observed.

## API Calls Observed

Not inspected — likely a GET to a `/events` API endpoint.

## Screenshots

- `screenshots/04-event-registration-overview.png` — Event Registration List (empty state)
