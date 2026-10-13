# SND Brightlife CB0

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


## Public website refresh (October 2026)

- The public landing page now follows the supplied sitemap direction: clear public CBO identity, project discovery, water-project detail, governance, partnership, support/donation information, and contact pathways.
- Public/member functions remain in the existing application; member login and registration controls are retained.
- Public photo assets are centralized in `assets/images/`. Client-supplied photographs use descriptive `client-*` filenames; the local logo mark and programme imagery are stored in the same directory.
- Do not publish unverified beneficiary totals, registration evidence, project budgets, donation payment details, or legal claims. Add approved documents and verified figures when the board authorizes them.
- The board is reviewing the savings/loan interest structure. The public information page deliberately states that terms are under review and should not be treated as final.
- The contact form currently shows an on-page confirmation only; the published phone and email are provided for direct contact until a backend submission endpoint is connected.
