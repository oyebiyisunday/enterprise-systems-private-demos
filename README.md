Private repositories — available upon request
Willing to work through demos, architecture tours, stack Q&A, and qualified read-only access.

1. CoreBox — flagship commerce & last-mile platform
One backend · four surfaces · checkout to proof of delivery

Surface	Stack
API
Node 20, TypeScript, Express, PostgreSQL
Merchant console
Next.js PWA
Customer app
Expo (pickup, send, receive, orders)
Driver app
Expo (dispatch, navigation, safety, POD)
Commerce: Auth (signup → reset), store onboarding + admin review, catalog, cart, Stripe Payment Intents + webhooks, inventory, care-word alerts, telemetry taxonomy, secure uploads.

Digital addressing: GPS → short code → resolve; reverse geocode (Google / Mapbox / Nominatim); privacy modes (public, delivery_only, restricted); country-adaptive policy; deep links to Google Maps, Waze, Apple Maps, OSRM.

Driver safety pack: Proof-of-arrival, mandatory handoff confirmation, unsafe-location feedback, offline retry queue, POD capture, cross-platform handoff (iOS + Android).

Tools: Docker Postgres, Stripe, Supabase (optional), Helmet/CORS/rate-limit, Zod, Multer, EAS, Railway/Nixpacks/Vercel, go-live smoke tests.

Docs: Deployment env matrix, deploy groups, analytics taxonomy, country-adaptive ruleset.

Brag: Multi-surface monorepo with production security (JWT + onboarding secrets, privacy-aware locations), payment-ready Stripe flow, last-mile ops built in—not bolted on.

2. CoreERP — procurement & logistics ERP (MIT)
Streamlit workspace for the full procure-to-pay and logistics office

12 modules: Dashboard KPIs · Materials master · Suppliers · Requisitions · RFQ · Purchase orders · Shipments/customs · Inventory/GRN · MRP/forecast · Finance/costs · Trade documents (COA, MSDS, B/L) · Approval inbox · Reports/analytics · User admin.

5 roles with real workflow: System Admin · Requester · Procurement Manager · Finance Manager · Plant Manager — role on account (no shared role switcher), audit log on sign-in and approvals.

Stack: Python 3.10+, Streamlit, SQLAlchemy, PostgreSQL/SQLite, Pandas, Plotly, OpenPyXL, bcrypt, Docker Compose.

Ops: 8 doc guides, cloud deploy (Railway, Azure, AWS, VM), validate.py pre-release gate.

Brag: Full PR → PO → ship → GRN → payment with approvals; trade doc center; MIT; Docker one-command deploy.

3. Barcode Serialization — manufacturing traceability (.NET 8)
System of record for unit identity, movement, and recall

Answers in minutes: What unit? Where made/shipped? What's in the case/pallet? What's in the recall?

Architecture: Api · Application · Domain (GS1) · Infrastructure (EF Core) · Edge worker (offline plant line + sync).

API: Products, batches, serials (unit/case/pallet), aggregation, scan events, shipments, trace by batch/unit/pallet/shipment, label data, AuthentiScan bridge, scan integrity.

Enterprise: API-key RBAC (Admin/Operator/Integration), RabbitMQ or in-process queue, PostgreSQL + migrations, audit logs, unit + integration tests, Swagger.

Brag: Deployable traceability—not slides; edge-ready factories; recall scoping via REST; pairs with AuthentiScan for consumer trust.

4. AuthentiScan — anti-counterfeit (3 surfaces)
Surface	Stack
API
ASP.NET Core 8, EF Core
Manufacturer portal
React + Vite + TypeScript
Consumer app
Flutter + mobile_scanner
Flows: Generate-and-print signed serials (ZPL) · Factory first-scan · Consumer verify · Dashboard + clone alerts.

6 verification statuses: AUTHENTIC · NOT_FOUND · CLONED · EXPIRED · NOT_FACTORY_SCANNED · SUSPICIOUS.

Integrations: Auth0 (prod portal), Zebra TCP printer gateway, Swagger, demo seed endpoint.

Brag: Factory-to-consumer anti-counterfeit; crypto-signed serials; clone detection dashboard; wired to Serialization as authoritative source.

5. FleetFlow — SAP-style logistics execution
Master Data → Planning → Execution → Confirmation → Analytics

12 Streamlit apps: Fleet · Drivers · Transport demands · Route planning · Dispatch monitor · Shipment tracking · POD · Operational reports · Exception alerts · Recommendations · Decision support · Data import.

LE chain: Create loads → plan/optimize stops → assign driver → release to dispatch → execute → confirm POD.

Stack: Streamlit, DuckDB, optional OSRM road routing, ETA engine, rules analytics.

Brag: SAP LE mental model for enterprise audiences; optional real-road routing; analytics beyond basic tracking.

6. Banking domain data model (BankDB)
Design deliverables + runnable SQL Server implementation + CI

Deliverables: UML class diagram · Chen ER · Physical design · Data dictionary (Excel) · Design report (Word) · Deployment diagram.

Implementation: Migrations 000–006 · Stored procedures · Triggers · Automated regression tests · GitHub Actions on SQL Server 2022 · PowerShell Deploy/RunTests/Invoke-LocalCI · OpenAPI 3 · ASP.NET Core 8 API over procedures · Security roles & masking · Ops runbooks.

Domain: Customers, accounts, deposits/withdrawals/transfers, address audit log, transaction comments, reporting procedures.

Brag: Diagrams + working T-SQL + CI in one package; business logic in DB; OpenAPI without bypassing procedures.

7. Thrift banking UI + API
Full-stack teller demo — React + Express + SQL Server

Two desks: Teller workstation (sign-on, verify account, post, till, statements) · Account opening desk (customers + accounts only).

Features: Till sessions · Posting audit · Credit cards with limits · Debt-aware balances · Session/operator audit log · Customer statements · Demo mode (no SQL) or live API mode.

SQL: Triggers + usp_PostTransaction · Till migration (OPENJSON) · Credit card borrowing rules.

Brag: Real teller UX with audit trail; dual-station separation; works offline in demo mode for quick walkthroughs.

8. CoreList — marketplace listing (Expo)
Split from CoreBox Customer (delivery-only) for clean architecture.

Routes: Landing grid · Store search · Catalog · Stripe checkout · Merchant signup.

Uses CoreBox API: /api/catalog/*, cart, checkout — reference copies for future microservice split.

Brag: Multi-app pattern on one API; marketplace UX isolated from logistics UX.

9. CoreBox Store Console — merchant PWA (Next.js)
Real-time partner dashboard: KPI hero, filters, paginated orders, status pills, dynamic store identity from API.

Contract-first API: Profile · Overview KPIs · Orders list · Status PATCH — documented in BACKEND-CONTRACT.md.

Brag: Production merchant-console patterns; PWA; never hardcoded store identity.

Ecosystem pitch (one paragraph)
CoreStack spans commerce (CoreBox, CoreList, Store Console), procurement (CoreERP), fleet execution (FleetFlow), manufacturing traceability (Serialization), consumer trust (AuthentiScan), and banking depth (BankDB + Thrift UI)—with 5 public GitHub portfolios for specs and analytics, and 9 private production builds available for walkthrough on request. 🔒 **Private repos — available upon request**

| Build | Highlights |
|-------|------------|
| **CoreBox** | 4-surface commerce + last-mile (API, web, 2 mobile apps, Stripe, digital addressing, driver safety) |
| **CoreERP** | MIT procurement ERP — PR/PO, MRP, GRN, approvals, trade docs, Docker |
| **Barcode Serialization** | .NET 8 traceability — serials, aggregation, recall, edge worker, RabbitMQ |
| **AuthentiScan** | Anti-counterfeit — .NET + React + Flutter, clone detection |
| **FleetFlow** | SAP LE-style fleet ops — plan, dispatch, POD, OSRM, analytics |
| **BankDB** | SQL Server banking — migrations, CI, OpenAPI, design deliverables |
| **Thrift UI** | Teller + account-opening — React, Express, SQL Server |
| **CoreList** | Expo marketplace listings + Stripe |
| **Store Console** | Next.js merchant PWA, contract-first API |

📬 Happy to demo any of these — [request walkthrough](https://www.corestacktechnologies.com/book-call)
