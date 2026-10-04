# AI Product Website, Sales, Subscription and Admin: delivery plan

Prepared: 4 October 2026  
Project ID: WS | Status: Planned; documentation only  
Scope: both the sales/subscription website and owner admin panel

## Source specifications

- [Website, sales and subscription summary](AI-Product-Website-Sales-and-Subscription-Summary.md)
- [Admin panel specification](AI-Product-Admin-Panel-Specification.md)
- Format reference: [Enquiry-to-Quotation delivery plan](../project-development/01-enquiry-to-quotation-assistant/README.md)

## Delivery documents

- [Status: 18 planned sprints](_STATUS.md)
- [Roadmap: six PIs](PI/README.md)
- [Module, feature and source coverage](docs/01-module-feature-sprint-matrix.md)
- [Architecture, contracts and product ownership](docs/02-architecture-and-integration.md)
- [Quality, acceptance and release gates](docs/03-quality-and-release-gates.md)
- [Decisions and dependencies](docs/04-decisions-and-dependencies.md)
- [Evidence and acceptance templates](templates/README.md)

Each PI has its own README and three sprint folders. Each sprint contains two WS feature IDs, six tasks, six acceptance checks, dependencies, demonstration and evidence requirements. WS IDs are independent of EQ and other product plans.

## Roadmap

| PI | Outcome | Sprints |
|---|---|---|
| [PI-01](PI/PI-01-foundation/README.md) | Commercial scope and secure foundation | S01-S03 |
| [PI-02](PI/PI-02-website-offers/README.md) | Sales website and versioned offers | S04-S06 |
| [PI-03](PI/PI-03-billing-usage/README.md) | Payments, subscriptions and usage | S07-S09 |
| [PI-04](PI/PI-04-customer-product/README.md) | Customer onboarding and product integration | S10-S12 |
| [PI-05](PI/PI-05-admin-operations/README.md) | Owner administration and support | S13-S15 |
| [PI-06](PI/PI-06-qualification-launch/README.md) | Market qualification, recovery and launch | S16-S18 |

Both specifications are integrated into one backlog: admin security begins in S03, offer controls in S06, full operator screens in S13-S15, and operational qualification in S17. This prevents deferring critical admin controls until after launch.

## Product boundary

Launch one selected product in one validated market. The quotation assistant is an example, not a final business decision. This plan implements sales, account, commercial and operating surfaces and integrates the selected product's complete workflow. It does not build a new LLM or duplicate catalogue/invoice/knowledge logic.

S02 records one authoritative owner for identity, subscriptions, usage, job execution and tenant data. If the chosen product already implements a service or admin view, reuse it and attach its evidence. Coordinate overlapping EQ S13-S18/S22-S24 or equivalent product sprints rather than bill or count work twice. S11 remains blocked if no real qualified product workflow exists.

A React/TypeScript frontend and Next.js business APIs are a planning option based on the reference, not a pinned stack. Provider, prices, markets, model, hardware and hosting remain undecided. No website, payment account, code, installation or deployment is created by these documents.

Three two-week sprints per PI would be 36 nominal sequential weeks. This is a scope-sizing aid, not a delivery commitment; re-estimate service reuse, staffing and capacity at each PI. Extra providers, automatic overages, multi-product bundles, advanced campaigns and private-installation automation remain deferred.
