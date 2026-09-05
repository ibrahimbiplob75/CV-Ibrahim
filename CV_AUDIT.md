# CV audit — Md Ibrahim Biplob

Audit date: 5 September 2026. Scope: `/data/My_Application`, the existing `CV_Project/index.html`, and the supplied instruction/background text.

## Deliverables and evidence standard

- `cv-software-engineer.html`: recruitment-focused full-stack/MERN CV.
- `cv-europe-msc.html`: education-first academic CV, with technical projects and prospective research interests.
- Original `index.html` was preserved during the initial audit. At the user’s subsequent request, it was replaced with the verified Software Engineer CV.

The scan covered all 10 software project directories, their application manifests, source layout, representative implementations, database models, deployment files, and available Git metadata. This is a portfolio evidence review, not an exhaustive line-by-line code or security audit. Dependencies alone were not treated as proof of practical use. Environment files, database contents, uploaded personal records, and credential values were not used. Project applications were not started or deployed.

Code establishes that an implementation exists; it does not establish successful production operation, sole authorship, commercial ownership, or a measured result. The user's background establishes employment; the old CV supplies education, contact details, awards, and prior responsibilities. Git author-name matches provide supporting contribution evidence, not identity certification or proof that every feature was personally written. The CVs therefore distinguish contribution bullets from descriptions of what a platform includes.

## Existing CV audit

The original has a photo/header, contact links, skills sidebar, education, activities, objective, professional experience, projects, achievements, and references. It also repeats summaries/contact information, uses very small text, mixes projects with employment, loads external fonts/styles/scripts, and includes demo credentials. The new versions use a single semantic reading order, local inline CSS, visible contact links, responsive layout, and A4 print styling. Both contain selectable text and a Print / Save as PDF button. ATS compatibility is supported by simple structure; no ATS vendor score is claimed.

Facts retained from the original/background:

- Md Ibrahim Biplob; Dhaka, Bangladesh; primary telephone and email; GitHub, LinkedIn, and portfolio destination.
- BSc in CSE, NITER / University of Dhaka, 2020–2025; CGPA 3.43; session 2019–2020. No GPA scale was supplied, so none was added.
- Software Developer at RETINA; LMS/ERP development, planning, fixes, QA, and enhancements.
- Lead Software Engineer at Intellisoft, also identified by the user as their own IT company; development, technical decisions, and deployment responsibilities.
- ICPC Asia Dhaka Regional 2024: year from supplied background, rank 221st from original CV. No independent contest record was supplied.
- Selected club/ambassador/ICT Olympiad activities and awards from the original CV.

The original RETINA entry says “June 2024 – Running,” while its summary and the supplied background say approximately twelve months/one year. These conflict as of this audit date. Both new CVs say “Current role” without calculating tenure or inventing a corrected start date. Intellisoft employment dates were not provided and are also omitted.

## All discovered software projects

Paths below are relative to the workspace root. Features are implementation evidence, not production guarantees. Employer/client affiliation is not inferred from a folder name.

### 1. Retina — education/LMS/ERP suite

- Components: `retina-admin-frontend`, `retina-student-frontend`, `retina-web`, `retina-backend-api`.
- Purpose: student learning, examinations, admissions, and academic/branch administration.
- Frontend: React admin/student applications; Next.js/TypeScript public application. Backend: Express/Node.js; MongoDB/Mongoose models.
- Authentication: backend auth and CSRF middleware; role/permission models and controllers. These are mechanisms present, not a claim of complete security.
- Features: course/content management, exam answer/start flows, enrollment/admission, result models, branch and finance workflows.
- Integrations: SSLCommerz controller constructs payment requests and invokes the SDK; bKash controller/token helpers exist. S3 client implementation supports file management. AI agent/retrieval code exists, beyond package declarations.
- Deployment: backend Dockerfile and `.github/workflows/deploy-ec2.yml` establish Docker/EC2 deployment configuration; execution success was not verified.
- Evidence: `Retina/retina-backend-api/server/controllers/exam/`, `server/models/Enrollment.js`, `server/models/OfflineResult.js`, `server/models/RolePermission.js`, `server/controllers/sslcommerzController.js`, `server/controllers/file_manager/s3.js`, `server/lib/ai/mastraInstance.js`; frontend source/component trees.
- Contribution: RETINA employment and LMS/ERP responsibilities explicitly supplied. Recent Git author-name matches in backend/admin/student histories support collaboration, but do not assign ownership of payment, AI, or every module. New CVs retain broad contribution wording and do not claim personal authorship of the AI subsystem.

### 2. Ecommerce-site — storefront and business administration

- Components: `Ecommerce-Business-Client`, `Ecommerce-Business-dashbaord` (folder spelling retained), `Ecommerce-Business-API`, and `deployment`.
- Purpose: customer shopping plus catalogue, order, inventory, and operational administration.
- Frontend: Next.js storefront; React dashboard. Backend: Node.js/Express. Database: MongoDB/Mongoose; Redis/BullMQ background jobs.
- Authentication: `Ecommerce-Business-API/middleware/authMiddleware.js` and user/role models.
- Features: product variants, stock-aware cart validation, order and customer workflows. `services/InventoryValidationService.js` reads products/combinations and adjusts or rejects unavailable quantities.
- Integrations: courier service/Steadfast modules; queued Facebook publishing/catalog code. `queues/facebookWorker.js` connects jobs to publishing services. No revenue, throughput, conversion uplift, or production payment claim was added.
- Deployment: GitHub Actions workflows plus `deployment/nginx/`, `deployment/systemd/`, release/deploy/rollback scripts. Configuration supports the deployment skill claims, not an uptime claim.
- Evidence: `Ecommerce-Business-Client/src/lib/services/`, `Ecommerce-Business-API/services/InventoryValidationService.js`, `services/StockMovementService.js`, `modules/courier/CourierService.js`, `queues/`, and `deployment/`.
- Contribution: matching author names appear across all three application histories and deployment history. Selected as project work; its relationship to a particular employer or client is unspecified.

### 3. Restuarent — restaurant operations platform

- Components: `apps/web`, `apps/store`, `apps/api`, shared packages and `prisma`.
- Purpose: restaurant/outlet administration, customer ordering, inventory, point of sale, and billing.
- Frontend: Next.js/React/TypeScript. Backend: NestJS. Database: PostgreSQL via Prisma (explicit schema datasource), migrations and relational models.
- Authentication: JWT auth guard; role permissions; request tenant context. `common/guards/permission.guard.ts` reads persisted role assignments, while `common/interceptors/tenant-context.interceptor.ts` establishes request context.
- Features: purchase/production/inventory modules, orders, split bills, audit logs, tenant/outlet models; Socket.IO dependencies and gateway structure.
- Integrations: Cloudinary module; payment-provider abstractions. **The bKash provider returns success without calling a gateway. It is a stub and was excluded as a real integration.**
- Deployment: `docker-compose.yml` exists. No production hosting claim included.
- Evidence: `Restuarent/prisma/schema.prisma`, `apps/api/src/modules/`, guards/interceptors above, `apps/api/src/test/cross-tenant.e2e-spec.ts`, `cross-outlet.e2e-spec.ts`, `permission-matrix.e2e-spec.ts` and other test files.
- Test presence is verified; test suites were not executed, and no security guarantee or passing result is asserted.
- Contribution: matching author names in Git support contribution to the project. Chosen for both CVs, especially academic software architecture/database/security relevance. Not conflated with the old CV's “Demo Restaurant” MERN project: this inspected system uses NestJS/PostgreSQL.

### 4. Intellisoft — company website and content administration

- Components: `Intellisoft/Intellisoft` frontend, `Intellisoft/intellisoft-backend`.
- Purpose: company services, projects, team profiles, ongoing work and enquiries.
- Frontend: React. Backend: Express. Database: MongoDB/Mongoose.
- Authentication: protected routes and role authorization in `middleware/auth.js`; project create/update/delete routes enforce administrative access.
- Features: team/project/pricing/contact/running-work data models and route handlers; frontend admin pages.
- Integrations/deployment: Cloudinary upload middleware, email dependency/routes, Firebase Hosting config for frontend and Vercel config for backend. Not a verification of live availability.
- Evidence: `Intellisoft/intellisoft-backend/routes/projects.js`, `models/`, `middleware/auth.js`, frontend `src/services/api.js`, `firebase.json`, backend `vercel.json`.
- Contribution: company leadership supplied by user and original CV; matching author names in frontend/backend histories. Used under Intellisoft experience. The chatbot route alone was not represented as original AI research.

### 5. Intellisoft-Task — task and project management

- Purpose: coordinate tasks, assignments, projects, meetings, and reminders.
- Frontend: Vue/Pinia with application views. Backend: Cloudflare Worker request handlers, not Express. Database: Cloudflare D1 through Prisma adapter.
- Authentication: authenticated request handling through auth services and route checks.
- Features: project/task assignments, task status transitions, calendar aggregation and scheduled due-date reminders.
- Integrations: email service invoked by task workflows. Deployment: `wrangler.jsonc`, Worker fetch/scheduled entrypoints and D1 client binding.
- Evidence: `Intellisoft-Task/server/index.js`, `server/prisma.js`, `server/routes/taskRoutes.js`, `server/services/taskService.js`, `server/services/email/`, `prisma/schema.prisma`, `src/views/dashboard/projects/`.
- Contribution: matching author names in Git. Included as selected project work, without claiming specific contract dates or ownership from the name alone. It is not described as the old CV's PostgreSQL HR/payroll suite.

### 6. Certificate-Website — certificate administration

- Components: `Client`, `Server`.
- Purpose: manage certificate requests, generation, storage, downloads and stock workflows.
- Frontend: React. Backend: Express; MongoDB access and model files.
- Authentication: `Server/middleware/auth.js` and authentication routes/controllers.
- Features: `certificateController.js` implements generate, preview, save, list and download-status actions; request and stock routes/models are present.
- Integrations: rendering/QR and S3 packages are declared; not all integration paths were traced end to end, so no personal S3 deployment claim is derived from this project.
- Evidence: `Certificate-Website/Server/controllers/certificateController.js`, `routes/request.js`, `routes/stock.js`, `models/CertificateRequest.js`, `models/CertificateStock.js`.
- Contribution: some Git author-name matches; client/employer relationship and operating status unverified. Not selected due to stronger recent systems.

### 7. gardashlar — member contribution and fund tracking

- Components: React frontend and Express backend; MongoDB/Mongoose.
- Purpose: member deposits, contributions, investments and fund summaries.
- Authentication: `backend/src/middleware/auth.js`, authenticated route handlers.
- Features: member/profile dashboards, deposits, contribution reports, system costs and investment summary calculations. `routes/investments.js` reads Deposit/Investment/InvestmentProject models and builds a fund summary.
- Integrations: Cloudinary/upload dependencies; deployment not verified.
- Evidence: `gardashlar/backend/src/routes/investments.js`, `routes/contributions.js`, `routes/contributionReports.js`, `models/index.js` and frontend source.
- Contribution: matching author names in both histories. No ownership of funds or financial performance claimed. Not selected to keep CVs focused.

### 8. Smash — e-commerce and order management

- Components: React/TypeScript frontend, Express/TypeScript backend; MongoDB/Mongoose.
- Purpose: catalogue, checkout, customer orders and inventory administration.
- Authentication: auth service, admin model and auth routes.
- Features: checkout order creation, status updates, stock reduction/restoration, low-stock warnings, inventory history and order emails. These are implemented service calls, not just dependency names.
- Integrations: email/Cloudinary services. Deployment: frontend Vercel workflow; deployment success unverified.
- Evidence: `Smash/backend/src/services/order.service.ts`, `inventory.service.ts`, `email.service.ts`, `models/`, `Smash/frontend/.github/workflows/vercel-deploy.yml`.
- Contribution: matching author names in both histories. Not selected because Ecommerce-site offers broader complementary evidence.

### 9. Medi_Chem — course, enrollment and quiz application

- Components: React/TypeScript frontend; Express backend with MongoDB/Mongoose models. Both legacy and `src` backend trees exist.
- Purpose: course material, enrollment, student learning and quiz administration.
- Authentication: `src/middleware/auth.js`; quiz routes use authentication and admin checks.
- Features: course/modules/materials, enrollments, quiz questions/attempts, activity logs; quiz routes support spreadsheet question import.
- Integrations: upload/storage packages exist, but a complete deployed payment/storage workflow was not verified. Payment model presence is not proof of a live payment gateway.
- Evidence: `Medi_Chem/medi_chem_server/src/routes/quizzes.js`, `src/models/`, `src/routes/enrollments.js`, frontend `admin/pages/` and `student_profile/`.
- Contribution: author-name matches in both histories. Some frontend pages are explicitly placeholders; do not treat every screen as finished. Not selected to avoid duplicating RETINA's educational domain.

### 10. Boilerplate — reusable Laravel administration foundation

- Purpose: reusable authentication, user/role management, settings and media administration.
- Frontend: Blade templates and Vue/Pinia resources. Backend: PHP/Laravel, Eloquent models/migrations.
- Database: configurable Laravel connections; a production MySQL deployment is not established by default configuration. MySQL remains background-only and is omitted from focused CV skill lists.
- Authentication/features: Laravel auth controllers, roles/permissions, CSV exports, user activities and media/file management.
- Evidence: `Boilerplate/composer.json`, `routes/`, `app/Http/Controllers/User/PermissionController.php`, `app/Models/`, `resources/views/`.
- Integrations: FTP filesystem package/configuration exists; actual remote operation unverified. Deployment unspecified.
- Contribution: no nested Git history discovered. User-supplied PHP/Laravel background is supported by application code, but sole authorship of the foundation is not asserted. Not selected as a flagship project.

## Repository inventory and recency

These are the latest local commit dates, not project start/completion dates or employment dates. Author-name matching examined up to 100 recent commits per repository and is only supporting evidence.

| Git checkout | Latest local commit |
|---|---|
| Intellisoft-Task | 2026-06-25 |
| Restuarent | 2026-08-05 |
| Certificate-Website | 2026-05-20 |
| gardashlar/backend | 2026-09-01 |
| gardashlar/frontend | 2026-09-01 |
| Retina/retina-web | 2026-09-03 |
| Retina/retina-student-frontend | 2026-08-22 |
| Retina/retina-backend-api | 2026-09-03 |
| Retina/retina-admin-frontend | 2026-09-03 |
| Intellisoft/intellisoft-backend | 2026-07-05 |
| Intellisoft/Intellisoft | 2026-09-03 |
| Smash/backend | 2026-09-01 |
| Smash/frontend | 2026-09-03 |
| Medi_Chem/medi_chem_server | 2026-08-31 |
| Medi_Chem/medi_chem | 2026-08-31 |
| Ecommerce-site/Ecommerce-Business-API | 2026-09-03 |
| Ecommerce-site/Ecommerce-Business-dashbaord | 2026-08-31 |
| Ecommerce-site/Ecommerce-Business-Client | 2026-09-03 |
| Ecommerce-site/deployment | 2026-07-30 |

The enclosing Ecommerce-site `.git` entry yielded no readable commit history. Boilerplate has no discovered nested checkout. Root metadata is managed workspace metadata; CV_Project is the document folder. No matching Ibrahim/Biplob author name appeared in the sampled retina-web history, so Next.js public-site ownership was not assigned to the user. No private remote URLs or other authors' personal data are reproduced.

## Classification and selection

| Category | Evidence and treatment |
|---|---|
| Professional employment | RETINA; explicit old CV and supplied background, supported by LMS/ERP code. |
| Company / startup work | Intellisoft lead role explicitly supplied; company application source corroborates technical context. |
| Other project work | E-commerce, restaurant, task system and remaining applications; commercial/personal boundaries not established. Listed neutrally as technical/engineering projects. |
| Academic projects | No thesis/course project attribution verified. The academic CV labels them technical projects, not coursework or research. |
| Competitive programming | ICPC 2024 from background; rank and practice sites from old CV. |
| Cloud / DevOps | EC2 workflow, Dockerfile, S3 code, Nginx/systemd/release scripts, GitHub Actions, Firebase/Vercel configurations, Worker/D1 implementation. Configuration is distinct from proof of execution. |
| Other technical experience | Laravel administration, Vue task application, serverless scheduled handlers and email workflows. |

Both CVs select Ecommerce-site, Restuarent, and Intellisoft-Task, with RETINA and Intellisoft as employment. The engineering version foregrounds delivery, APIs, databases, and deployment. The academic version starts with education/ICPC and emphasizes data modelling, access control, architecture and prospective study interests. Sharing projects keeps the career history consistent while changing the reasoning and order.

## Exclusions and information needing confirmation

- RETINA exact start date and duration conflict; Intellisoft dates absent. No dates invented.
- No verified language proficiency, native-language statement, IELTS/TOEFL results, or other language test evidence was supplied. Languages section omitted rather than guessing.
- No named completed certification with issuer/date was supplied. Awards are not relabelled as certifications.
- No transcript, thesis title, relevant course list, publications, research employment, or recommendation letters supplied. No research accomplishment invented; research interests are future interests from the prompt.
- C, C++, Java and Python in the academic CV come from existing CV/background, not newly verified repository work. MySQL, Postman and LaTeX are not highlighted because stronger concrete evidence is available for other skills.
- AI code exists in RETINA, but individual contribution is not established. No AI research or model-development claim included.
- No invented users, traffic, revenue, performance improvements, team size, uptime, or project completion dates. Old “Linux (6 yrs)” and “QA (1 yr)” labels omitted as stale/unreconciled durations.
- Old hardware/sanitary, RMC blood system, result portals, aquaculture, online magazine, AI tour, demo marketplace, university-management and HR-suite claims were not matched conclusively to these folders. They remain in the original but are not republished in the new selected projects.
- Generic certificates/skills were not added just to fill requested categories. The SDG award issuer is retained only as the original “UniV”; no expanded organization name or award date invented.
- Demo credentials and referee personal contacts excluded. The original credential text was not copied to the new outputs or this audit; the subsequent index update also removes it from `index.html`.
- Precise street address, secondary telephone, photo, religious affiliation and less relevant sporting activities omitted to reduce unnecessary personal information.
- Contact values and link destinations match the original. Primary phone reformatted to Bangladesh international notation. The original portfolio label did not match its destination; the new label accurately says “Intellisoft team profile.” External link availability and account ownership were not independently checked.

## Validation

Validation results are recorded below after rendering. Application test suites were not run because no application code was changed.

- Initial original SHA-256 comparison: unchanged. Subsequently, the user authorized updating `index.html`; it now matches `cv-software-engineer.html` byte-for-byte.
- Both HTML documents passed nesting, single-H1, local cross-link and inherited contact-link checks. No external styles, fonts or scripts are required.
- Headless Chrome rendered both documents successfully; both generated tagged, selectable-text, two-page A4 PDFs. Extracted text was inspected for reading order, complete sections and page boundaries.
- The academic CV was visually checked at a 390px mobile viewport; wrapping and navigation were readable. Both versions share the same responsive styles.
- Matching PDF exports are included as `cv-software-engineer.pdf` and `cv-europe-msc.pdf`.
- The first sandboxed browser launch was blocked by the environment; the approved local browser run completed successfully. No external website validation or project test execution is implied.

## Current presentation — original format restored

At the user's explicit correction, all three HTML entrypoints now use the original navy/gold header, circular profile photo, pale left sidebar, right content column, section bars and footer. The previously described single-column styling is superseded. The verified content is retained. Software and Abroad buttons switch the visible CV on the same page; the selected state is reflected in the URL hash and only that CV prints. The named HTML files default to their respective versions. Shared styling and behavior live in `cv-style.css` and `cv-switch.js`; the original Google Fonts families are restored with local fallback fonts. The profile image was restored at the user's request to preserve the original format.

Both default states and both click handlers were checked, including exclusive panel visibility and accessible pressed states. Desktop renders for both modes were visually inspected in Chrome, and both PDF exports were regenerated. Earlier validation descriptions refer to the previous layout.

## Portfolio domain update

User supplied the current portfolio URL: https://intellisoft.it.com/team/md-ibrahim-biplob . Updated both CV modes in all HTML entrypoints and refreshed PDF exports. This replaces the inherited Firebase team-profile destination.

## User-confirmed project domains and expanded project list

The user supplied the following project/domain mappings and explicitly requested adding missing projects in both modes. This supersedes the earlier limited project selection and the exclusion of the Bepari/RMC projects.

| Entry | User-supplied URL | Content source |
|---|---|---|
| RETINA employment | https://retinabd.org/ | Existing role; employer title now linked. |
| Care Nest e-commerce | https://carenest.shop | Existing audited e-commerce project, now named and linked. |
| Smash | https://smashstorebd.vercel.app/ | Previously audited Smash project and source features. |
| Gardashlar | https://frontend-gardshlar.vercel.app/ | Previously audited contribution/fund tracking code. |
| Bepari hardware management | https://bepari-client-site.vercel.app/ | User's project identification and original CV shop-system description. |
| RMC Rotaract blood management | https://rmcrotaract.org/ | User confirms medical college context; original CV supplies donor/request/stock/role features. |
| Dr Tawhid Academy | http://drtawhidacademy.com/ | User's description: medical coaching management system. No extra stack, features, or dates invented. |

The Dr Tawhid Academy deployment is not automatically equated with Medi_Chem because that code-to-domain relationship has not been established. URLs are retained exactly as supplied, including HTTP for the academy. Domain availability was not independently tested; inserting user-provided links is not a deployment verification. All three HTML entrypoints contain these additions in both modes; PDF exports were refreshed. The original navy/gold two-column design and Software/Abroad switching remain.

## Restaurant deployment links

User supplied separate restaurant interfaces: [Admin Panel](https://restuarent-complete-project-web.vercel.app/) and [Client Website](https://restuarent-complete-project-store.vercel.app/). Both links were added to the restaurant project in Software and Abroad modes across all three HTML entrypoints, and both PDF exports were refreshed. These are user-confirmed domain mappings; live availability was not independently tested.
