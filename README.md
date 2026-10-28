# ZYROO Delivery & Logistics Platform — Week 6
http://localhost:5174/ To Check online may ne the htlm file is not working

A responsive React + Vite frontend for the ZYROO local delivery and logistics management platform. This Week 6 build focuses on completing the user-facing order lifecycle, role-specific workspaces, tracking, notifications, usability, and final project documentation.

> **Source archive note:** The supplied Week 5 ZIP contained only the project README, package metadata, Vite config, and environment files; the referenced `src/` application was not included. This Week 6 version reconstructs the frontend using the architecture and features described in that README and the Week 6 brief. It should be treated as a rebuilt demo frontend, not as a verified patch of the original Week 5 source.

## Run locally

```bash
npm install
cp .env.example .env
npm run dev
```

Build and preview:

```bash
npm run build
npm run preview
```

## Demo access

All demo accounts use password `1234`.

- Business: `business@zyroo.test`
- Rider: `rider@zyroo.test`
- Customer: `customer@zyroo.test`

Use the role buttons on the login screen to switch between demo workspaces. Orders and notifications persist in browser `localStorage`; open the app in another tab to see browser storage updates reflected. This is a frontend demo and does not provide a production backend or real GPS tracking.

## Implemented in this Week 6 rebuild

- Role-based Business, Rider, and Customer demo login/workspaces.
- Business overview, order list, search, status/rider/date filters, pagination, CSV export, order creation, rider assignment, and cancellation.
- Rider delivery queue and guarded status progression: Assigned → Accepted → Picked Up → In Transit → Delivered.
- Customer-scoped orders and delivery tracking timeline.
- Order details drawer with pickup/drop-off, customer, fee, rider, and notes.
- Notifications list, unread count, mark-as-read, and mark-all-as-read.
- Rider directory with availability and delivery summary.
- Editable profile display name and phone field (demo state).
- Empty states, toast feedback, input validation, responsive layouts, keyboard focus indicators, reduced-motion support, and accessible labels for key controls.
- Local storage persistence and a storage-event listener for cross-tab order updates.
- Production build configuration and this setup/deployment README.

## Order lifecycle

`Pending → Assigned → Accepted → Picked Up → In Transit → Delivered`

`Cancelled` is treated as a separate final state. In the demo, a Business user can assign a rider to a pending order and cancel eligible orders; a Rider user can advance an assigned order through delivery stages.

## Technology

- React 18
- Vite 5
- React Router dependency retained for compatibility with the supplied Week 5 package metadata
- lucide-react icons
- Browser `localStorage` demo data (no live API configured)

## Environment configuration

`.env.example` retains the Week 5 variable names:

| Variable | Purpose |
|---|---|
| `VITE_API_URL` | Intended base URL for a future backend API |
| `VITE_USE_MOCK` | Week 5 mock/API switch; this rebuilt UI currently uses local browser demo state |
| `VITE_POLL_INTERVAL_MS` | Reserved for future API polling integration |
| `VITE_MOCK_FAIL_RATE` | Reserved for future mock API failure simulation |

Do not put secrets in frontend environment variables; Vite variables are exposed to the client bundle. A real production release needs a backend API, server-side authorization, secure session/token handling, persistent database, and deployment environment configuration.

## Testing checklist before production

- [ ] Verify sign-in, sign-out, and role permissions against a real backend.
- [ ] Complete an order from creation to delivery using multiple user roles.
- [ ] Verify rider assignment, cancellation rules, notifications, tracking, and order history.
- [ ] Add automated component and end-to-end tests.
- [ ] Test API errors, network timeouts, unauthorized requests, and duplicate submissions.
- [ ] Validate API payloads and phone/email/address fields server-side.
- [ ] Test mobile, tablet, laptop, and desktop sizes in Chrome, Edge, and Firefox.
- [ ] Complete keyboard, focus, contrast, labels, screen-reader, and accessible-error review.
- [ ] Audit dependencies, bundle size, lazy loading/code splitting, image use, and rendering performance.
- [ ] Configure a production API and environment variables, then deploy to Vercel, Netlify, Render, or a suitable host.
- [ ] Verify the deployed build, production API, deep-link routing, and console errors.
- [ ] Add final screenshots, live demo URL, and a short end-to-end demonstration.

## Deployment

This is a standard Vite app. Import the repository into Vercel or Netlify, set the build command to `npm run build` and output directory to `dist`. Configure SPA fallback/rewrite rules if required by the hosting provider. Set the production API environment only after a compatible backend is available. **No live deployment has been performed from this workspace.**

## Suggested demo walkthrough

1. Sign in as Business and create an order.
2. Assign a rider and inspect the order details.
3. Sign in as Rider and accept the delivery.
4. Progress the delivery through pickup and in-transit to delivered.
5. Sign in as Customer and review order status, tracking timeline, and notifications.
6. Return to Business to confirm the completed order and history.

## Project structure

```text
src/
  main.jsx       Complete React UI, role views, order lifecycle, demo state
  styles.css     Responsive UI, states, accessibility and reduced-motion styles
public/
index.html       Vite HTML entry point
.env.example     Documented environment variable template
README.md        Setup, feature notes, test checklist, deployment guidance
```

## Known limitations

- The Week 5 archive did not contain the original source code, so this is a clean rebuild rather than an incremental source-level upgrade.
- Authentication uses demo credentials only; it is not secure production authentication.
- Data is local to the browser. There is no real API server, database, server-side role enforcement, or cross-device synchronization.
- The tracking map is an illustrative route preview, not a real map or GPS feed.
- Performance, accessibility, cross-browser, and production deployment checklists are provided but require actual testing before release.
