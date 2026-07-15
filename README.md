<img width="1200" height="630" alt="Image" src="https://github.com/user-attachments/assets/2250a4bf-aa2a-40bf-84eb-b97320925d3a" />

---

# Funding Workflow Guardrail Builder

![Status](https://img.shields.io/badge/status-production-22c55e)
![Stack](https://img.shields.io/badge/stack-HTML%20%7C%20CSS%20%7C%20JavaScript-06b6d4)
![Build](https://img.shields.io/badge/build-none-7c3aed)
![Embed](https://img.shields.io/badge/embed-1200%C3%97940-fbbf24)
![Human Review](https://img.shields.io/badge/control-human--in--the--loop-fb5f5f)

A static launch site and compact embeddable interface for the **Funding Workflow Guardrail Builder** Custom GPT.

The product helps funding brokers, agency owners, processors, fintech builders, CRM consultants, and automation operators map where AI may act, where a workflow must pause for human review, who has authority to decide, what evidence must be recorded, and which actions should never run autonomously.

> **Operating rule:** Automate the preparation. Escalate the uncertainty. Assign the decision. Record what happened.

---

## Live Project Links

| Resource | URL |
| --- | --- |
| Primary site | https://funding-workflow-builder.vercel.app |
| Embeddable version | https://funding-workflow-builder.vercel.app/embed.html |
| Custom GPT | https://chatgpt.com/g/g-6a57c12bd01c8191acf2a3a0b038961c-funding-workflow-guardrail-builder |
| Notion product record | https://feimster.notion.site/funding-workflow-guardrail-builder/ |
| GitHub repository | https://github.com/JFeimster/funding-workflow-builder |
| Vercel project | https://vercel.com/jason-feimsters-projects/funding-workflow-builder |
| Google Drive project folder | https://drive.google.com/drive/folders/1Fnk6XZS1G5HuRxqPTUcHRtL01djUnRTQ?usp=drive_link |

### Supporting Resources

| Resource | URL |
| --- | --- |
| Human Review Checkpoint Map | https://docs.google.com/document/d/14ruSLY4yOFT50nSbCNeuB5c_H1O-zrWLNM1qHBz7yns/copy |
| Funding Agency Automation Pack | https://drive.google.com/drive/folders/1jkd-9yCnccVC7Jc21YTVgu8h1aElrgDB |

---

## Current Project Status

| Component | Status |
| --- | --- |
| Primary production page | Live |
| Embed page | Live |
| Vercel production deployment | Ready |
| GitHub repository | Public |
| Default branch | `main` |
| Custom GPT | Published |
| Notion registry record | Published |
| Static build process | Not required |
| Backend | Not required |
| Runtime integrations | Optional / planned |
| Knowledge pack | 20 Markdown files |
| Validation | Passed for links, schemas, CTA hooks, and embed dimensions |

The primary site and embed both return successful production responses from Vercel.

---

## What the GPT Does

The Funding Workflow Guardrail Builder converts a described or redacted funding workflow into an implementation-ready human-review control plan.

It can generate:

- Workflow stages
- AI-permitted actions
- Green, Yellow, and Red risk classifications
- Human-review triggers
- Reviewer roles and authority
- Escalation paths
- Audit-log fields
- Override-log fields
- Forbidden actions
- A 40-point pre-launch readiness score
- Notion or Airtable review-queue specifications
- CRM pipeline stages and field maps
- n8n routing logic
- Synthetic workflow test cases
- Implementation checklists

It is designed to support operational control. It does not approve funding, deny applicants, establish final terms, declare fraud, or guarantee regulatory compliance.

---

## The Green, Yellow, and Red Control Model

### Green Zone — Automate

Low-risk, administrative, reversible actions may run under approved rules.

Examples:

- Create CRM records
- Organize and name files
- Identify blank fields
- Generate document checklists
- Transcribe calls
- Send approved neutral reminders
- Route internal tasks

### Yellow Zone — Review

AI may analyze, calculate, compare, flag, recommend, or draft, but a qualified human must review the output before the workflow advances.

Examples:

- Product matching
- Lead scoring
- Bank-statement observations
- Cash-flow analysis
- Eligibility comparisons
- Anomaly flags
- High-impact message drafts

### Red Zone — Stop

The workflow must stop autonomous execution and route the matter to an authorized human.

Examples:

- Approval or denial communication
- Final terms or pricing changes
- Fraud conclusions
- Complaint or dispute resolution
- Closing authorization
- Disbursement authorization
- Sensitive-data incidents
- Altered or unverified submissions

> **High confidence does not create authority.**

---

## Eight Human Review Checkpoints

The GPT can apply controls across eight workflow checkpoints:

1. Data and consent
2. Document quality
3. Eligibility and product fit
4. Risk and anomaly review
5. Decision authority
6. Communications and disclosures
7. Final terms and closing
8. Monitoring, overrides, and feedback

For each checkpoint, the output may define:

- AI-permitted actions
- Human-review triggers
- Required evidence
- Reviewer role
- Reviewer authority
- Escalation path
- Audit fields
- Forbidden actions

---

## Website Versions

### 1. Primary Launch Site

**Production URL:** https://funding-workflow-builder.vercel.app

The full launch site includes:

- Conversion-focused hero section
- Green, Yellow, and Red framework
- Human-in-the-loop workflow visualization
- Problem and risk sections
- GPT output grid
- Eight human checkpoints
- Guardrail report preview
- 40-point readiness scorecard
- Target persona cards
- Best-for and not-for sections
- Four-step workflow
- Use-case map
- Resource CTAs
- FAQ section
- Final conversion CTA
- JSON-LD structured data
- Open Graph and Twitter metadata
- Responsive navigation
- Reduced-motion support
- Privacy-conscious analytics hooks

### 2. Embeddable Launch Panel

**Production URL:** https://funding-workflow-builder.vercel.app/embed.html

The embed is purpose-built for Wix, Notion, partner dashboards, portals, and iframe placements.

Desktop target:

- Maximum width: `1200px`
- Maximum height: `940px`

The embed includes:

- Compact product status bar
- Short hero and primary GPT CTA
- Green, Yellow, and Red control strip
- Six compact output cards
- Four-step process
- Supporting resource links
- Operational disclaimer
- Responsive mobile behavior
- `noindex,follow` metadata

It is not simply the main site squeezed into an iframe.

---

## Technology

- Semantic HTML5
- Plain CSS
- Vanilla JavaScript
- Inline and local SVG assets
- No React
- No Next.js
- No Vite
- No Tailwind build dependency
- No npm install
- No package manager
- No build command
- No backend requirement
- No external JavaScript library requirement

The project can run directly from the repository or any basic static host.

---

## Repository Structure

```text
funding-workflow-builder/
├── index.html
├── styles.css
├── script.js
├── embed.html
├── embed.css
├── embed.js
├── README.md
├── robots.txt
├── validation-report.json
└── assets/
    ├── favicon.svg
    └── og-image.svg
```

### File Responsibilities

| File | Purpose |
| --- | --- |
| `index.html` | Full production launch page, SEO metadata, FAQs, and JSON-LD |
| `styles.css` | Primary-site design system, responsive layouts, motion, and accessibility states |
| `script.js` | Mobile navigation, reveal behavior, score animation, and CTA analytics events |
| `embed.html` | Compact iframe-safe product interface |
| `embed.css` | Namespaced embed styling and 1200 × 940 layout controls |
| `embed.js` | Embed CTA event hook |
| `robots.txt` | Crawler instructions |
| `validation-report.json` | Validation results for URLs, schemas, CTA IDs, relative links, and embed dimensions |
| `assets/favicon.svg` | Browser and shortcut icon |
| `assets/og-image.svg` | Social-sharing graphic |

---

## Quick Start

### Clone the Repository

```bash
git clone https://github.com/JFeimster/funding-workflow-builder.git
cd funding-workflow-builder
```

### Preview Locally

Using Python:

```bash
python3 -m http.server 8080
```

On Windows, either command may work:

```powershell
py -m http.server 8080
```

```powershell
python -m http.server 8080
```

Open:

- Primary site: http://localhost:8080/
- Embed: http://localhost:8080/embed.html

The files can also be opened directly, but a local server provides more realistic browser behavior.

---

## Embed Installation

### Generic Iframe

```html
<iframe
  src="https://funding-workflow-builder.vercel.app/embed.html"
  width="100%"
  height="940"
  style="max-width:1200px;border:0;overflow:hidden;"
  loading="lazy"
  title="Funding Workflow Guardrail Builder"
  allow="clipboard-write"
></iframe>
```

### Responsive Wrapper

```html
<div style="width:100%;max-width:1200px;margin:0 auto;">
  <iframe
    src="https://funding-workflow-builder.vercel.app/embed.html"
    width="100%"
    height="940"
    style="display:block;width:100%;border:0;overflow:hidden;"
    loading="lazy"
    title="Funding Workflow Guardrail Builder"
    allow="clipboard-write"
  ></iframe>
</div>
```

### Wix

1. Add **Embed Code**.
2. Choose **Embed a Site**.
3. Enter:

   ```text
   https://funding-workflow-builder.vercel.app/embed.html
   ```

4. Set the width to `100%`.
5. Set the height to `940px`.
6. Set a maximum container width of `1200px` where the Wix layout permits.
7. Check tablet and mobile breakpoints before publishing.

### Notion

1. Type `/embed`.
2. Paste:

   ```text
   https://funding-workflow-builder.vercel.app/embed.html
   ```

3. Resize the embed block.

Notion may add its own frame, padding, and height behavior.

---

## Deployment

### Vercel

The project is already deployed to Vercel.

| Field | Value |
| --- | --- |
| Project name | `funding-workflow-builder` |
| Project ID | `prj_53WX5Wjn0irjE4K2JgWj7SfX15Fj` |
| Team | Jason Feimster's projects |
| Team ID | `team_fYzYTSpH5gj1di6KiPHV6tbx` |
| Framework | None / static |
| Production domain | `funding-workflow-builder.vercel.app` |
| Default Git branch | `main` |

For a fresh import:

1. Import the GitHub repository into Vercel.
2. Select **Other** or no framework preset.
3. Leave the build command empty.
4. Leave the install command empty.
5. Use the repository root as the output location.
6. Deploy.

### Recommended Release Workflow

1. Create a feature branch.
2. Test locally.
3. Open a preview deployment.
4. Review the primary and embed pages.
5. Validate CTA links and responsive behavior.
6. Merge into `main`.
7. Confirm the production deployment.
8. Re-run the validation checklist.

---

## Production SEO Cleanup

> [!IMPORTANT]
> The production page currently still contains placeholder `YOUR-DOMAIN.com` values in canonical, Open Graph, Twitter image, and BreadcrumbList metadata. `robots.txt` also references a sitemap URL that is not currently included in the repository.

Before treating the deployment as SEO-complete, update `index.html` as follows:

```text
https://YOUR-DOMAIN.com/funding-workflow-guardrail-builder
→
https://funding-workflow-builder.vercel.app/
```

```text
https://YOUR-DOMAIN.com/assets/og-image.svg
→
https://funding-workflow-builder.vercel.app/assets/og-image.svg
```

Review the BreadcrumbList entries. Do not link to a nonexistent local `/ai-agents` page.

Then either:

1. Add a real `sitemap.xml`, or
2. Remove the sitemap line from `robots.txt`.

Recommended canonical:

```html
<link rel="canonical" href="https://funding-workflow-builder.vercel.app/">
```

Recommended Open Graph URL:

```html
<meta property="og:url" content="https://funding-workflow-builder.vercel.app/">
```

Recommended Open Graph image:

```html
<meta
  property="og:image"
  content="https://funding-workflow-builder.vercel.app/assets/og-image.svg"
>
```

---

## SEO and Structured Data

The primary page contains:

- SEO title
- Meta description
- Canonical tag
- Open Graph metadata
- Twitter card metadata
- `SoftwareApplication` JSON-LD
- `FAQPage` JSON-LD
- `BreadcrumbList` JSON-LD

The embed uses:

```html
<meta name="robots" content="noindex,follow">
```

Do not add fake ratings, aggregate ratings, reviews, testimonials, certifications, or pricing claims to structured data.

---

## Analytics Hooks

The site works without analytics.

When configured, it can emit events to:

- Native browser `CustomEvent`
- Google Tag Manager or Google Analytics through `window.dataLayer`
- Plausible through `window.plausible`

### Browser Event

```text
guardrail:cta
```

### CTA IDs

```text
cta-launch-gpt-hero
cta-launch-gpt-mid
cta-launch-gpt-final
cta-download-checkpoint-map
cta-open-automation-pack
cta-embed-launch-gpt
```

### Example Listener

```js
window.addEventListener("guardrail:cta", (event) => {
  console.log(event.detail);
});
```

### Example Event Payload

```json
{
  "id": "cta-launch-gpt-hero",
  "href": "https://chatgpt.com/g/g-6a57c12bd01c8191acf2a3a0b038961c-funding-workflow-guardrail-builder",
  "timestamp": "2026-07-15T18:00:00.000Z"
}
```

---

## Accessibility

The site includes:

- Semantic landmarks
- Skip-to-content link
- Keyboard-accessible navigation
- Visible focus states
- Native disclosure controls for FAQs
- Accessible labels
- Text labels and icons in addition to color
- Responsive layouts
- Reduced-motion fallbacks
- No autoplaying media
- No forced modal windows
- No browser-history manipulation
- No critical content that depends on JavaScript

The Green, Yellow, and Red model is never communicated by color alone.

---

## Performance

The project is intentionally lightweight:

- No framework hydration
- No external font dependency
- No third-party UI library
- No package installation
- No server-side rendering
- No database connection
- Local SVG assets
- Minimal JavaScript
- Static Vercel delivery
- Browser caching through Vercel's edge network

---

## Knowledge Pack

The GPT is supported by 20 Markdown knowledge files.

### Core Knowledge

1. `product-overview.md`
2. `human-review-checkpoint-map.md`
3. `green-yellow-red-classifier.md`
4. `eight-workflow-checkpoints.md`
5. `exception-trigger-library.md`
6. `reviewer-role-matrix.md`
7. `escalation-paths.md`
8. `audit-log-schema.md`
9. `override-log-template.md`
10. `forbidden-actions.md`
11. `prelaunch-qa-scorecard.md`
12. `safe-language-and-disclaimers.md`

### Implementation Knowledge

13. `n8n-routing-patterns.md`
14. `crm-routing-patterns.md`
15. `notion-airtable-review-queue.md`
16. `workflow-output-templates.md`
17. `example-funding-workflows.md`
18. `workflow-test-cases.md`
19. `data-privacy-and-redaction.md`
20. `action-endpoints.md`

The Google Drive project folder also contains:

- A project README
- `assets/`
- `knowledge/`
- `knowledge-pack-manifest.json`
- `validation-report.json`

---

## Planned Action Roadmap

The GPT's current value is primarily knowledge-driven. External Actions should be treated as a planned implementation layer unless separately configured and verified.

### No-Auth

Potential public utilities using synthetic or redacted data:

- Classify an abstract workflow task
- Build an anonymous guardrail map
- Score workflow readiness
- Validate a guardrail map
- Generate routing pseudocode
- Redact a workflow description
- Create temporary exports

### API Key

Potential protected services:

- Retrieve policy templates
- Run guardrail policy checks
- Scan risky funding language
- Validate JSON, YAML, CSV, and CRM schemas
- Generate n8n specifications
- Generate CRM specifications
- Render downloadable artifacts
- Run synthetic workflow evaluations

### OAuth

Potential connected-system actions:

- Save and version projects
- Create Notion or Airtable review queues
- Create CRM stages and fields
- Export files to Google Drive
- Create disabled n8n workflow drafts
- Append override records
- Create incidents
- Notify assigned reviewers

Any write, notification, external export, database creation, or workflow creation should require explicit confirmation.

---

## Validation

The repository includes `validation-report.json`.

The current validation covers:

- Required project files
- Exact GPT URL
- Exact Human Review Checkpoint Map URL
- Exact Funding Agency Automation Pack URL
- CTA tracking IDs
- Valid `SoftwareApplication` JSON-LD
- Valid `FAQPage` JSON-LD
- Valid `BreadcrumbList` JSON-LD
- Relative links in `index.html`
- Relative links in `embed.html`
- Embed maximum-width declaration
- Embed maximum-height declaration

Validation does not replace browser, accessibility, SEO, privacy, or legal review.

---

## Privacy and Data Handling

Use:

- Redacted workflow descriptions
- Synthetic applicant records
- Representative examples
- Field names
- Data categories
- Abstracted decision rules

Do not submit:

- Passwords
- One-time codes
- API keys
- OAuth tokens
- Social Security numbers
- Full bank-account numbers
- Unredacted identity documents
- Complete live applicant financial records through unsecured tools

The GPT and site do not need live applicant data to map workflow controls.

---

## Product Boundaries

The Funding Workflow Guardrail Builder may help teams:

- Map workflow stages
- Identify unsafe automation
- Create human-review queues
- Define reviewer authority
- Draft implementation logic
- Create audit fields
- Test workflow scenarios
- Improve operational readiness

It does not:

- Approve or deny funding
- Replace underwriting
- Establish binding terms
- Declare fraud
- Replace legal counsel
- Replace compliance review
- Replace tax or accounting advice
- Guarantee funding outcomes
- Guarantee regulatory compliance

---

## Maintenance Checklist

Before each production release:

- [ ] Confirm primary site loads
- [ ] Confirm embed loads
- [ ] Confirm GPT URL
- [ ] Confirm Human Review Checkpoint Map URL
- [ ] Confirm Funding Agency Automation Pack URL
- [ ] Confirm Notion record URL
- [ ] Confirm Google Drive project folder URL
- [ ] Test desktop, tablet, and mobile layouts
- [ ] Test keyboard navigation
- [ ] Test visible focus states
- [ ] Test reduced-motion behavior
- [ ] Validate JSON-LD
- [ ] Validate canonical and Open Graph URLs
- [ ] Check `robots.txt`
- [ ] Check sitemap behavior
- [ ] Confirm external links use `noopener noreferrer`
- [ ] Confirm CTA event IDs
- [ ] Run `validation-report.json` checks
- [ ] Review privacy and limitation language
- [ ] Confirm no unsupported funding or compliance claims

---

## Ecosystem Map

```text
Custom GPT
    ↓
Funding Workflow Guardrail Builder
    ↓
Primary launch site
    ├── Full product explanation
    ├── GPT conversion CTA
    ├── Human Review Checkpoint Map
    └── Funding Agency Automation Pack
    ↓
Embed version
    ├── Wix
    ├── Notion
    ├── Partner portals
    └── Static dashboards
    ↓
Knowledge pack
    ├── 12 core control files
    └── 8 implementation files
    ↓
Future Actions
    ├── No-Auth utilities
    ├── API-key services
    └── OAuth-connected workflows
```

---

## Disclaimer

This project provides educational and operational workflow guidance. It does not provide legal, lending, underwriting, tax, accounting, or compliance advice.

It does not guarantee:

- Funding approval
- Eligibility
- Funding speed
- Final terms
- Business results
- Regulatory compliance

Funding criteria, laws, platform behavior, and operating requirements may change. Qualified professionals and authorized decision-makers should review high-impact workflows and decisions.
