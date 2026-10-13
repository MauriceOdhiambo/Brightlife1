# SND Brightlife CBO

Production Node.js web application for SND Brightlife CBO covering member services, savings, table banking, lending, repayments, guarantor approvals, administration, reporting and community programmes.

## Stack

- Node.js 20+
- Vercel serverless runtime
- Supabase / PostgreSQL
- HTML, CSS and browser JavaScript
- Resend and WhatsApp Cloud API integrations
- Vercel Cron for scheduled operations

## Run locally

```bash
npm install
node --env-file=.env server.mjs
```

The application is available at `http://localhost:3000`.

For Vercel development, `npm run dev` starts the Node.js application directly. Production deployments continue to use the existing Vercel serverless API and cron configuration.

## Environment

Copy `.env.example` to `.env` and provide the production values for Supabase, cron authentication and any enabled messaging/payment integrations.

Never expose server secrets in browser code.

## Project structure

```text
/
├── index.html
├── assets/
│   ├── app.css
│   └── app.js
├── api/
│   ├── server.js
│   └── cron/[job].js
├── project-images/
├── server.mjs
├── package.json
└── vercel.json
```

The browser application keeps the established Brightlife workflows and calls the Node.js API at `/api/server`. The standalone Node server provides the same API locally while Vercel continues to run the production serverless functions.

## Current production UI

The workspace uses a persistent member navigation shell, responsive navigation, route-aware browser history, a direct member-login logout flow, and a responsive statement/reporting centre. Public navigation uses the same responsive layout rules across desktop and mobile.

## Production deployment

Deploy the repository to the existing Vercel project with the required environment variables. No database migration is required for this frontend/Node runtime modernization.


## Public website and sitemap implementation

The public website is structured around the supplied SND Brightlife CBO sitemap: Home, About Us, Our Projects, Water Project detail, Governance, Partner With Us, Support Us / Donate, Contact Us and Savings & Loan Information. Member login, registration, savings and loans dashboard, guarantor portal and the dedicated 404 state remain part of the existing application.

### Images and content

- Website image files are centralized in `assets/images/` and referenced with root-relative paths (`/assets/images/<filename>`), so images continue to resolve on nested routes and hash-based pages.
- The project includes descriptive copies of the additional client-supplied photographs covering water collection and storage, poultry activities, bicycle repair and community transport.
- Public pages use real client-supplied activity photographs in place of the generic category artwork where suitable photos are available. Image elements include a local fallback in case a source file fails to load.
- Administrator-published project titles, descriptions and photo URLs are reflected in the public project cards and project detail view. The Content Management page accepts direct public image URLs or local paths under `/assets/images/`.
- The Partner With Us and Support Us pages include a direct email pathway for funding proposals and partnership enquiries at `sndbrightlife@gmail.com`.
- The public Savings & Loan Information page uses the existing member loan bands: 12% for up to 7 days, 16% for 8–14 days, 18% for 15–20 days, and 20% for 21–30 days. The processing fee and existing guarantor conditions are also described.

### Run locally

```bash
npm install
node --env-file=.env server.mjs
```

The application is available at `http://localhost:3000`. Use `npm run check` to run the JavaScript syntax checks for the server and browser application.

### Deployment notes

Deploy the repository to the existing hosting project with its required environment variables. Keep administrator credentials and service keys on the server only. Verify public pages, uploaded/published project content and the member workflows in the deployment environment before release.

## Sitemap-aligned public website update

The public presentation is rendered from `assets/app.js` and styled by `assets/app.css`. The sitemap-focused page set includes Home, About Us, Our Projects, Water Project detail, Governance, Partner With Us, Support Us / Donate, Contact, Savings & Loan Information, and the branded 404 state. The existing member login, registration, savings/loans dashboard and guarantor portal remain part of the application.

### Image organization

- Client-provided project photographs and the organization mark are stored in `assets/images/`.
- Locally generated sitemap-style illustrative images are stored in `assets/images/generated/`.
- Public page image references use local `/assets/images/...` paths and local fallback images. Administrator-published project photos can override defaults when a valid public image URL or local asset path is supplied.

### Administrator-published project content

The public project cards load the published content keys managed through the CBO content-management screen. Published titles, descriptions and photos update matching project cards; additional programme cards are appended when the administrator publishes content for supported extra programme keys.

### Local development

```bash
npm install
npm run dev
```

The server defaults to `http://localhost:3000`. Run `npm run check` to validate the server and browser JavaScript syntax.

## Sitemap and member experience refinement (October 2026)

- Increased the public-site brand mark and member workspace logo while keeping the shared header responsive.
- Reduced homepage project-card copy and made each programme card open a dedicated, sitemap-styled project profile. The Water Project continues to use its dedicated detail page.
- Added consistent detail-page structures for education, health and wellbeing, economic empowerment, community development, poultry, vocational skills and entrepreneurship.
- Detail pages read published administrator project titles, descriptions and images where available, in addition to the public project-card integration.
- Refined login and registration form spacing, labels, input focus states, action buttons, and registration welcome panel.
- Refined member workspace sidebar, top bar, data tables, form controls, focus states and responsive spacing without replacing existing account logic.

Run `npm run check` to validate server and client JavaScript syntax. Run `npm start` to serve the site locally.
