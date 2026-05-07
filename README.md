# Atlas — D365 Process Navigator

> **A web-based knowledge and learning tool for Dynamics 365 Finance & Operations functional consultants.**

[![Data Source](https://img.shields.io/badge/Data%20Source-Microsoft%20BPC-0078D4)](https://learn.microsoft.com/en-us/dynamics365/guidance/business-processes/overview)
[![Purpose](https://img.shields.io/badge/Purpose-Educational-6B7D69)](https://github.com)
[![License](https://img.shields.io/badge/License-Educational%20Use%20Only-A87D55)](https://github.com)

---

## What is Atlas?

Atlas transforms the **Microsoft Business Process Catalog (BPC)** into a navigable, visual, end-to-end map of how Dynamics 365 applications support enterprise business processes. It is designed for experienced D365 functional consultants who need to understand, trace, and communicate how processes connect across the full D365 product suite.

---

## Purpose

This application is a **learning tool**. It is built to help:

- **Functional consultants** understand how D365 supports each business process at every level of the hierarchy.
- **Project teams** trace processes from high-level E2E journeys down to individual system steps and test cases.
- **Implementation architects** identify product coverage across Application Families and specific D365 products.
- **Pre-sales and client-facing consultants** map client requirements against Microsoft's official process taxonomy.

This tool is **not** a production system, not a replacement for official Microsoft documentation, and not affiliated with Microsoft Corporation.

---

## Data Source

All process data is sourced exclusively from the **Microsoft Business Process Catalog (BPC)**:

📖 **Official documentation:** https://learn.microsoft.com/en-us/dynamics365/guidance/business-processes/overview

The March 2026 release of the catalog is included, covering:

| Level | Type | Count |
|---|---|---|
| 1 | End-to-End Process | 15 |
| 2 | Process Area | 94 |
| 3 | Process | 674 |
| 4 | Scenario | 3,557 |
| 5 | System Process | 451 |
| 6 | Test Case | 1,082 |
| **Total** | **All nodes** | **5,873** |

**Application Families covered:** Azure · Business Central · Customer Engagement · Finance and Operations · Power Platform · Productivity

**Products covered (22):** Azure · Business Central · Commerce · Customer Insights Data · Customer Insights Journey · Customer Service · Customer Voice · Field Service · Finance · Human Resources · Microsoft 365 · Microsoft Cloud for Sustainability · Other · Power Apps · Power Automate · Power BI · Power Pages · Project Operations · Sales · SharePoint · Supply Chain Management · Teams

---

## Technical Stack

| Layer | Technology |
|---|---|
| Language | Vanilla JavaScript (ES2020+) |
| Styling | CSS custom properties (design tokens), CSS Grid, Flexbox |
| Fonts | Cormorant Garamond · Source Serif 4 · JetBrains Mono (Google Fonts) |
| Data | Self-contained `data.js` (parsed from Microsoft BPC Excel export) |
| Hosting | GitHub Pages (static, no server required) |
| Dependencies | Zero — no frameworks, no npm, no build step |

The application runs entirely in the browser. No backend, no database, no authentication.

---

## Features

### 🗂 Hierarchical Process Tree
A collapsible, full-depth tree of all 5,873 process nodes. The hierarchy: **End-to-End → Process Area → Process → Scenario → System Process → Test Case**. Text wraps fully at every level — no truncation.

### 📊 Drill-Down Flow Diagrams
Every level of the hierarchy includes a visual **Process Flow** diagram showing all direct child nodes as connected, clickable cards. Layout adapts automatically:
- **≤ 8 children:** Sequential flow with directional arrows
- **> 8 children:** Responsive grid layout

Flow diagrams are colour-coded by node type and navigate directly to any node on click.

### 🔍 Global Search
Full-text search across all 5,873 nodes (⌘K / Ctrl+K). Searches titles, descriptions, APQC IDs, modules, and products. Results grouped by node type with full ancestry breadcrumb shown.

### 🎛 Dynamic Filters
Application Family and Product filters reshape the entire tree — nodes without matching content are removed, not greyed out. Filter state is shown as chips with one-click removal.

### 📋 Content Tabs (per node)
- **Process Flow** — Visual drill-down diagram
- **Overview** — Business context and hierarchy coverage
- **D365 Support** — Product coverage grid and D365 capabilities
- **System Details** — Module, menu path, and Microsoft Learn links
- **Test Cases** — System processes and test cases (shown when present)
- **APQC Context** — Industry framework alignment and ID mapping

### 🧭 Contextual Right Panel
The right rail dynamically shows the **next level down** in the hierarchy for the currently selected node — Process Areas when viewing an E2E, Processes when viewing an Area, Scenarios when viewing a Process, etc. Each item is clickable for direct navigation.

### 🔗 Deep Linking
Every node has a unique URL hash (`index.html#10.05.010.100`). Share links directly to any process node — the app will restore to that exact position on load.

### ℹ️ About Section
Accessible from the header. Contains the data source credit, Microsoft BPC link, and the full educational use disclaimer.

---

## Getting Started

### Option 1 — Download and open locally

1. Download `index.html` and `data.js` — keep them in the **same folder**.
2. Double-click `index.html` to open in your browser.

> ⚠️ Some browsers block local file access. If the app loads but shows no data, use Option 2.

### Option 2 — Local development server (recommended)

```bash
# Python (built into macOS and most Linux distros)
python3 -m http.server 8080
# Then open: http://localhost:8080

# Node.js
npx serve .
# Then open: http://localhost:3000
```

### Option 3 — GitHub Pages

1. Push both files to a public GitHub repository.
2. Go to **Settings → Pages → Source → Deploy from branch → main**.
3. Your app will be live at `https://your-username.github.io/your-repo-name/`.

---

## File Structure

```
atlas-d365/
├── index.html      # Complete application (HTML + CSS + JS, ~60 KB)
├── data.js         # Full catalog data — all 5,873 nodes (~3.5 MB)
└── README.md       # This file
```

No build step. No `node_modules`. No configuration files.

---

## Updating the Data

When Microsoft releases a new version of the Business Process Catalog:

1. Download the new Excel file from the [Microsoft BPC documentation page](https://learn.microsoft.com/en-us/dynamics365/guidance/business-processes/overview).
2. Run the Python extraction script (contact repository maintainer) to regenerate `data.js`.
3. Replace `data.js` in the repository.

The `index.html` does not need to change unless new node types are introduced.

---

## Disclaimer

> This application is created **solely for educational purposes** to help users understand and navigate the Microsoft Business Process Catalog. All data is sourced from official Microsoft documentation.
>
> This tool is not affiliated with, endorsed by, or representative of Microsoft Corporation. Dynamics 365, the Business Process Catalog, and all related product names are trademarks of Microsoft Corporation.

---

## Credits

- **Data:** [Microsoft Business Process Catalog](https://learn.microsoft.com/en-us/dynamics365/guidance/business-processes/overview) — March 2026 release
- **Typefaces:** [Cormorant Garamond](https://fonts.google.com/specimen/Cormorant+Garamond) · [Source Serif 4](https://fonts.google.com/specimen/Source+Serif+4) · [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts
- **Design concept:** Atlas — D365 Process Navigator, 2026

---

*Built for learning. Not for production. All process data © Microsoft Corporation.*
