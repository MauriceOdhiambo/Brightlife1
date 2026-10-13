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


## Public website refresh (October 2026)

- The public landing page now follows the supplied sitemap direction: clear public CBO identity, project discovery, water-project detail, governance, partnership, support/donation information, and contact pathways.
- Public/member functions remain in the existing application; member login and registration controls are retained.
- Public photo assets are centralized in `assets/images/`. Client-supplied photographs use descriptive `client-*` filenames; the local logo mark and programme imagery are stored in the same directory.
- Do not publish unverified beneficiary totals, registration evidence, project budgets, donation payment details, or legal claims. Add approved documents and verified figures when the board authorizes them.
- The board is reviewing the savings/loan interest structure. The public information page deliberately states that terms are under review and should not be treated as final.
- The contact form currently shows an on-page confirmation only; the published phone and email are provided for direct contact until a backend submission endpoint is connected.

## Sitemap rebuild (October 2026)

The public website now uses the sitemap-aligned page renderer for Home, About Us, Our Projects, Water Project detail, Governance, Partner With Us, Support Us / Donate, Contact, Savings & Loan Information and a dedicated 404 state. The existing member authentication and financial workflows are retained rather than replaced with static mockups. The primary public navigation links into these pages, while member login and registration continue to open the existing forms.

### Image handling

Public assets are stored centrally in `assets/images/` and referenced from the site root using `/assets/images/<filename>`. Client-provided water, poultry and community-transport photographs are used where they genuinely match the content. Programme imagery without a matching client photograph is retained as illustrative material and must not be treated as evidence that a particular activity has been delivered. Replace those remaining illustrative images with licensed web photographs or additional approved client photographs before launch; preserve image credits/licensing records when using third-party photography.

### Review before launch

- Verify the public pages at desktop, tablet and mobile sizes against the supplied sitemap.
- Confirm that login, registration, member dashboard, savings/loans and guarantor flows still work with the production backend.
- Publish registration certificates, health officer correspondence, governance documents, verified project budgets and impact figures only after authorization.
- Keep the savings-and-loans interest terms marked as under board review until the board and appropriate Kenyan legal/regulatory advisers approve the final disclosure.
- Do not publish donation account details until they are formally approved and separated from member savings/loan funds.
