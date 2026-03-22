# SOC 2 Compliance Dashboard

A browser-based SOC 2 readiness tracker covering all five AICPA Trust Service Criteria categories across 200+ tasks. Designed for teams preparing for either a Type I or Type II audit, the dashboard provides task-level progress tracking, category-by-category navigation, structured PDF report generation, and persistent state across sessions. No backend, no login, no installation required — a single self-contained HTML file.

---

## Overview

SOC 2 is an auditing standard developed by the American Institute of Certified Public Accountants (AICPA) that evaluates how organisations manage customer data against five Trust Service Criteria. Unlike prescriptive frameworks, SOC 2 requires organisations to define their own controls and demonstrate they are designed (Type I) and operating effectively (Type II). This dashboard structures that process into a navigable, trackable, and reportable workflow.

---

## Features

### Sidebar Navigation
The five Trust Service Criteria categories are accessible from a persistent left sidebar, each showing a live mini progress bar and completion percentage. Clicking a category loads its full set of criteria and tasks in the main panel without losing context.

### Task Tracking
Every task can be cycled through four statuses by clicking it:

- **Not Started** — default state
- **Planned** — scoped and scheduled
- **In Progress** — actively being implemented
- **Completed** — implemented and evidenced

Progress saves automatically to browser storage and restores on next visit.

### Type I / Type II Toggle
A toggle in the sidebar switches between two views:

- **Type I** — focuses on design effectiveness tasks. Covers whether the right controls exist and are appropriately designed at a point in time. Type II-specific tasks are hidden and locked.
- **Type II** — unlocks the full task set including operating effectiveness evidence tasks. These tasks — audit logs, test results, access review records, incident evidence, and similar — are tagged with a `TYPE II` badge throughout the interface.

### Five Trust Service Criteria
All five TSC categories are fully covered:

| Category | Code | Requirement |
|----------|------|-------------|
| **Security** | CC | Mandatory for all SOC 2 reports |
| **Availability** | A | Optional — required if uptime commitments are in scope |
| **Processing Integrity** | PI | Optional — required for payment processors and data pipelines |
| **Confidentiality** | C | Optional — required when sensitive business or client data is processed |
| **Privacy** | P | Optional — required when personal information is collected or processed |

### Common Criteria (Security) in Full
The Security category covers all nine Common Criteria in detail: CC1 (Control Environment), CC2 (Communication & Information), CC3 (Risk Assessment), CC4 (Monitoring Activities), CC5 (Control Activities), CC6 (Logical & Physical Access), CC7 (System Operations), CC8 (Change Management), and CC9 (Risk Mitigation).

### Task Filtering
Within any category, tasks can be filtered by status — Not Started, Planned, In Progress, or Completed — to focus on specific stages of work without switching views.

### PDF Report Export
Clicking Export PDF generates a formatted A4 report including:
- Report header with SOC 2 branding, report type, and generation date
- KPI summary strip with colour-coded task counts
- Global completion progress bar
- Per-category task tables with colour-coded status and Type I / Type II labelling
- Page numbers and footer on every page

The PDF is formatted for sharing with auditors, executives, legal counsel, or prospective customers.

### JSON Export
Exports the full progress state and statistics as a structured JSON file, suitable for version control, handoff between teams, or integration with GRC tooling.

### Light and Dark Mode
A toggle in the top-right corner switches between a warm off-white light mode and a deep navy dark mode. The preference persists alongside task progress.

### Bulk Actions
- **Set All Planned** — marks all visible not-started tasks as Planned in one click, useful at the start of a readiness project
- **Reset** — clears all progress with a confirmation prompt

---

## Use Cases

### Security and Compliance Teams

**SOC 2 Readiness Assessment**
A security engineer or compliance lead uses the dashboard at the start of a SOC 2 programme to work through all five TSC categories, identifying gaps between current state and what an auditor will expect. Filtering to "Not Started" in each category surfaces the full remediation backlog in minutes.

**Type I Audit Preparation**
A team targeting a Type I report — which evaluates control design at a specific point in time — uses the Type I mode to focus exclusively on design and implementation tasks, keeping the audit scope clear and avoiding distraction from evidence-gathering activities that are only relevant at Type II.

**Type II Evidence Tracking**
During the audit observation period (typically 6–12 months), a compliance analyst switches to Type II mode and tracks the collection of operating effectiveness evidence: access review records, change approval logs, incident response documentation, DR test results, and vendor assessment records. The Type II badge on relevant tasks makes it immediately clear what evidence still needs to be gathered before the auditor review.

**Annual Audit Renewal**
SOC 2 Type II reports cover a defined period and must be renewed. At the start of each new audit period, a compliance team resets the dashboard's operating effectiveness tasks, retaining design task completions, and works through the evidence-gathering cycle again — using the PDF export to report progress to the CISO or audit committee.

**GRC Programme Integration**
A governance, risk and compliance team uses the JSON export to feed SOC 2 progress data into their wider GRC platform or risk register, maintaining a single authoritative record of control status across multiple frameworks.

**Auditor Readiness Briefings**
Before engaging an external auditor, a compliance manager generates a PDF report to demonstrate the organisation's current readiness, flag known gaps, and set expectations for the audit timeline. The structured per-category format maps directly to how auditors review evidence.

---

### Non-Security Teams

**Engineering and Product Teams**
Developers and product managers responsible for building and maintaining secure systems use the dashboard to understand which SOC 2 requirements touch their work — particularly CC6 (Logical Access), CC7 (System Operations), and CC8 (Change Management) — and to track implementation of technical controls like MFA enforcement, environment separation, and vulnerability patching.

**Legal and Privacy Teams**
A data privacy counsel or DPO uses the Privacy category (P1–P8) to track implementation of privacy programme requirements: notice obligations, consent management, data subject access rights, third-party disclosures, and data quality controls. The PDF export serves as a record of privacy programme maturity for regulatory purposes.

**HR and People Teams**
HR teams responsible for employee onboarding, offboarding, and security training use CC1 (Control Environment) and CC6 (Logical & Physical Access) to track people-related controls: security policies, background checks, access de-provisioning on departure, and confidentiality agreements. The dashboard provides a clear list of tasks that require HR involvement without requiring familiarity with the full SOC 2 standard.

**Sales and Customer Success Teams**
Enterprise sales teams facing security questionnaires from prospective customers use the dashboard to generate a PDF progress report demonstrating SOC 2 readiness. This gives enterprise buyers confidence in the organisation's security posture even before formal certification is achieved, and helps sales teams answer detailed security questions accurately.

**Executive and Board Reporting**
A CTO or COO preparing a quarterly board update on compliance status uses the KPI summary and progress bars to communicate where the organisation stands across all five TSC categories — and the PDF report provides a shareable, professional-quality document without requiring the board to access the tool directly.

**Finance and Legal — Vendor Due Diligence**
Finance and procurement teams evaluating third-party vendors often request SOC 2 reports as part of supplier due diligence. Teams that have been asked to provide evidence of their own SOC 2 progress to a customer or partner can use the PDF export as an interim deliverable while the full audit is in progress.

**Startups Entering Enterprise Markets**
Early-stage companies beginning the SOC 2 process for the first time — often prompted by an enterprise customer requirement — use the dashboard as their primary project management tool for the entire readiness programme, working through each category systematically and using the PDF export for investor and customer updates.

---

## Technical Notes

- Runs entirely client-side — no server, no account, no data leaves the browser
- State stored in browser local storage and persists across sessions on the same device
- PDF generation uses jsPDF and jsPDF-AutoTable, loaded from the Cloudflare CDN
- Compatible with all modern browsers (Chrome, Edge, Firefox, Safari)
- Single HTML file — can be saved locally, hosted on an intranet, or shared directly
- Type II task visibility is controlled client-side — switching modes does not affect stored progress
