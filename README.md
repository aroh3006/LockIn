# Lock In

![Stack](https://img.shields.io/badge/Stack-Vanilla%20JS-e8a33d)
![Focus](https://img.shields.io/badge/Focus-Placement%20Prep-b5544a)
![Storage](https://img.shields.io/badge/Storage-LocalStorage-6a9955)
![Platform](https://img.shields.io/badge/Platform-Web-6b7280)
![Status](https://img.shields.io/badge/Status-Active-6a9955)

A single-file, self-contained dashboard for tracking placement season preparation : DSA practice, cybersecurity study rotation, hands-on TryHackMe rooms, core CS revision and the interview pipeline itself. No build step, no backend, no dependencies. Open `index.html` in a browser and it runs.

---

## Overview

Lock In was built around one idea: preparation only works if you can see, at a glance, what you actually did and what's overdue. It is not a study planner that tells you what to do — it is a tracker that records what you did do, so patterns become visible over time instead of staying anecdotal.

The dashboard is organized into tabs, each covering one part of preparation:

- **Today** - the day's suggested focus, a Min/Normal/Max effort checklist, an activity heatmap with a current/longest streak, and same-day alerts for any scheduled OA, interview, or pre-placement talk.
- **Log / Archive** - a calendar you can click into for any date, with a free-text field for what you actually worked on that day.
- **DSA** - a pattern-tagged problem tracker with a Day 3 / Day 10 / Day 30 spaced-revisit schedule, status color-coding, full solve-history per problem, and search/filter by pattern, tier, or status.
- **TryHackMe** - the same tracking model applied to hands-on rooms and paths, organized by category.
- **Cybersecurity** — a rotation tracker across security topic areas, with a staleness indicator and an honest "interview-ready" flag.
- **Core CS** - revision tracking for DBMS, OOP, Computer Networks, and Operating Systems.
- **Placements** - a company pipeline with editable stage tracking, and date/time fields for OA, Interview, and PPT that trigger same-day alerts on the Today tab.
- **Weekly Review** - rolling 7-day stats across every tracker, plus a running log of weekly reflection notes.

## Profile and Track Selection

Not every user of this dashboard is preparing for a cybersecurity role. On first load, the app asks for a name and whether the user is on a cybersecurity track.

- If **yes**, the TryHackMe and Cybersecurity tabs are shown, along with the cybersecurity topic in the Today rotation panel and the cybersecurity item in the daily checklist.
- If **no**, those elements are hidden entirely. DSA, Core CS, Placements, Log/Archive and Weekly Review remain available regardless, none of that is cybersecurity-specific.

The track can be changed at any time from the Profile button in the sidebar, without affecting any already-recorded data.

## Data and Storage

Lock In stores all data client-side, under a single storage key, using one of two backends depending on where it is running:

- **Inside a Claude.ai artifact**, it uses Claude's built-in persistent storage, tied to the user's account.
- **As a standalone deployment (for example, on GitHub Pages)**, it falls back to the browser's `localStorage`, since Claude's storage API is not available outside that environment.

### Known Limitation

When running as a standalone deployment, storage is scoped to a single browser on a single device. This means:

- Data does not sync across devices or browsers.
- Clearing browser data, cookies, or site storage will permanently delete all tracked progress.
- There is no account system and no server-side backup.

This is an inherent constraint of a dependency-free, backend-free static page, not a bug. Anyone using this deployment for anything beyond casual or short-term use should periodically export their data manually or fork the project and connect a real backend if persistence across devices matters to them.

## Getting Started

No installation is required.

1. Clone or download this repository.
2. Open `index.html` directly in a browser, or serve the folder with any static file host.
3. For a public deployment, enable GitHub Pages on this repository and point it at the branch containing `index.html`.

## Tech Stack

- HTML, CSS, and vanilla JavaScript. No framework, no build tooling, no package manager.
- All state, rendering and event handling are implemented in a single file.
- Fonts are loaded from Google Fonts (Space Grotesk, IBM Plex Mono, IBM Plex Sans); everything else is self-contained.

## Customization

The seeded DSA problem set, TryHackMe rooms, cybersecurity rotation topics, and core CS subjects reflect one particular preparation plan. They are starting points, not fixed content. Items can be added, removed or edited freely from within the dashboard once it is running and the seed data itself can be edited directly in the source for a different starting point.

## License

Lock In is licensed under the MIT License.
