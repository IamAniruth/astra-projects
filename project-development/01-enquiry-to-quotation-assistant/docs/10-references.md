# Official technical references

Reviewed for this planning package on 30 September 2026. Follow the installed version's documentation during implementation; versions and platform eligibility can change. No dependency installation has been verified in this documentation task.

- [Next.js installation](https://nextjs.org/docs/app/getting-started/installation): scaffold and server setup.
- [Next.js backend-for-frontend guidance](https://nextjs.org/docs/app/guides/backend-for-frontend): Route Handlers and deployment limitations.
- [Vite getting started](https://vite.dev/guide/): React tooling and runtime requirements.
- [Node.js release schedule](https://nodejs.org/en/about/previous-releases): choose a supported LTS release.
- [pnpm installation](https://pnpm.io/installation): package-manager setup.
- [Drizzle PostgreSQL setup](https://orm.drizzle.team/docs/get-started/postgresql-new): database adapter and migrations.
- [Better Auth installation](https://better-auth.com/docs/installation): authentication setup; confirm database adapter and Next.js integration for the selected release.
- [BullMQ documentation](https://docs.bullmq.io/): Redis-backed background processing.
- [Astra source assessment and feature mapping](11-astra-llm-feature-mapping.md): selected local LLM integration baseline, private gateway contracts and release dependencies.
- [Stripe subscription webhooks](https://docs.stripe.com/billing/subscriptions/webhooks): provider-specific event handling if selected.
- [Razorpay subscriptions](https://razorpay.com/docs/payments/subscriptions/): alternative provider evaluation if eligible.

The architecture, sprint scopes, acceptance targets, and example configurations are proposed project decisions, not vendor guarantees. Choose and pin compatible versions during S01. Country-specific legal, tax, and payment eligibility decisions need current validation before launch.

