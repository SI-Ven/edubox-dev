# Project Development Roadmap

## 1. Project Overview

- **Project description:** EduBox is an education platform with a Next.js admin portal for managing curriculum and content, a Laravel API shared by the web and mobile clients, and an Expo mobile app for teachers working in low-connectivity environments.
- **Technology stack:** Docker and Docker Compose, Traefik, Keycloak, keycloak-config-cli, MariaDB, Laravel/PHP, Laravel Reverb, Next.js/React/TypeScript, NextAuth, TanStack React Query, Zustand, Axios, Tailwind CSS, HeroUI, i18next, Laravel Echo, Pusher, Pest, and Expo/React Native.
- **Repository structure:** A polyrepo workspace containing the configuration repository, Keycloak theme repository, Laravel core repository, Next.js web client repository, and Expo mobile app repository.
- **Development workflow:** Phase 1 establishes the complete local and shared infrastructure plus both application foundations; Phase 2 delivers every feature end to end; Phase 3 completes testing, deployment, and final verification.

---

## 2. Phase 1: Project Foundation and Infrastructure

### 2.1 Workstation and Prerequisites

- [ ] Install Git, Docker Engine, Docker Compose v2, GNU Make, Node.js 24, curl, wget, and jq.
- [ ] Enable corepack and pnpm.
- [ ] Configure the Git user name and email.
- [ ] Verify Docker runs without sudo.
- [ ] Review Linux users, file permissions, hosts file, ports, and process basics.
- [ ] Confirm ports 80 and 443 are available.

### 2.2 Architecture and Repository Setup

- [ ] Define user types, responsibilities, services, URL plan, and architecture diagram.
- [ ] Create the workspace and the five project repositories.
- [ ] Add repository ignore rules and onboarding READMEs.
- [ ] Define branch, pull request, and commit message conventions.
- [ ] Install Husky pre-push hooks in every repository.
- [ ] Configure branch protection for the main branch.
- [ ] Create the committed environment template and local environment file strategy.
- [ ] Configure the local user ID and host name values.

### 2.3 Docker and Core Infrastructure

- [ ] Create the initial Docker Compose configuration.
- [ ] Create the shared Docker network.
- [ ] Configure the local development domain.
- [ ] Add Traefik as the single reverse proxy.
- [ ] Verify the Traefik dashboard and routing.
- [ ] Configure HTTPS and TLS certificates.
- [ ] Verify HTTP redirects to HTTPS.
- [ ] Add the application MariaDB database with persistent storage.
- [ ] Verify database persistence across container recreation.
- [ ] Add Adminer for database access.
- [ ] Add MailHog for development email capture.
- [ ] Verify MailHog captures a test email.
- [ ] Create the Makefile with help and lifecycle targets.
- [ ] Automate the complete project bootstrap sequence.
- [ ] Verify container networking and service name resolution.

### 2.4 Identity and Access Infrastructure

- [ ] Create the Keycloak image and repository.
- [ ] Add the Keycloak database and Keycloak service behind Traefik.
- [ ] Configure Keycloak proxy handling and health checks.
- [ ] Review authentication, authorization, OAuth2, OIDC, and JWT concepts.
- [ ] Add keycloak-config-cli to the infrastructure.
- [ ] Create the EduBox realm as code.
- [ ] Configure password policy, brute-force protection, OTP, token lifespans, SMTP, and frontend URL.
- [ ] Define all realm roles.
- [ ] Define the super administrator and teacher groups.
- [ ] Register the backend, frontend, and mobile clients.
- [ ] Add the roles claim mapper.
- [ ] Create the backend technical user and grant admin API roles.
- [ ] Configure client scopes and the status claim.
- [ ] Configure the custom reset-credentials flow.
- [ ] Verify password reset email reaches MailHog.
- [ ] Seed the first administrator account.
- [ ] Obtain and inspect a token manually.
- [ ] Verify userinfo returns roles and status.
- [ ] Build the branded login and email themes with English and Khmer messages.
- [ ] Set up and verify identity database dump and restore.

### 2.5 Backend Initialization

- [ ] Add the Laravel service to Docker Compose.
- [ ] Configure the Traefik route and path rewrite for the backend API.
- [ ] Create the Laravel project.
- [ ] Review the Laravel project structure.
- [ ] Configure backend environment variables and connect Laravel to MariaDB.
- [ ] Generate the application key and run the default migrations.
- [ ] Configure API-only routing.
- [ ] Configure trusted proxy handling.
- [ ] Configure JSON error responses.
- [ ] Define the API response contract.
- [ ] Create the Keycloak-compatible users table.
- [ ] Update the User model.
- [ ] Add the backend setup target to the Makefile.
- [ ] Verify Artisan commands and migration status.

### 2.6 Frontend Initialization

- [ ] Create the Next.js application in Docker.
- [ ] Add the web client service and Traefik route.
- [ ] Configure Next.js settings and development origins.
- [ ] Configure frontend environment variables.
- [ ] Create the frontend folder structure and TypeScript path aliases.
- [ ] Create the site configuration and shared utility helpers.
- [ ] Set up ESLint, Prettier, and type checking.
- [ ] Install Husky pre-commit hooks for the web client.
- [ ] Configure Tailwind, HeroUI, English and Khmer fonts, dark mode, and the dynamic class safelist.
- [ ] Create the root layout and provider tree with metadata, fonts, and initial language handling.
- [ ] Create the base Axios client and API configuration.
- [ ] Configure React Query and global toasts.
- [ ] Configure i18next with English and Khmer and create the language helpers.
- [ ] Build the shared data table, action bar, and filter store.
- [ ] Build the modal, alert dialog, form, sort, and upload building blocks.
- [ ] Create shared page title, validation, debounce, and unsaved changes helpers.
- [ ] Verify hot reload, linting, type checking, theming, and translations.

### 2.7 Environment, Networking, and Service Communication

- [ ] Configure all required environment files.
- [ ] Align shared secrets and public URLs across repositories.
- [ ] Verify container-to-container connectivity.
- [ ] Verify routing for the portal, identity, API, and WebSocket paths.
- [ ] Document service ports and public URLs.
- [ ] Verify the foundation bootstrap workflow from a clean state.

### Phase 1 Completion Checklist

- [ ] All required tools are installed and Docker runs without sudo.
- [ ] The five repositories exist and Git hooks are active.
- [ ] Docker Compose starts the complete infrastructure stack.
- [ ] The local domain resolves and HTTPS works without certificate warnings.
- [ ] MariaDB, Adminer, MailHog, Keycloak, and keycloak-config-cli are configured and working.
- [ ] The Keycloak realm, clients, roles, groups, users, and theme are configured.
- [ ] Laravel is initialized, connected to the database, and returns JSON API responses.
- [ ] Next.js is initialized and served through Traefik.
- [ ] Frontend tooling, styling, providers, API client, translations, and shared components are ready.
- [ ] Backend and frontend communicate using aligned environment values.
- [ ] The foundation bootstrap sequence starts all services and initializes the workspace from a clean state.

---

## 3. Phase 2: Feature Development

### Feature 1: Authentication and Authorization

**Backend Tasks**
- [ ] Install and configure the Keycloak JWT guard.
- [ ] Validate Keycloak tokens for API requests.
- [ ] Implement role-based authorization middleware.
- [ ] Add userinfo caching and cache invalidation.
- [ ] Implement the Keycloak Admin API helper.
- [ ] Implement user, group, and role helper methods.
- [ ] Create the first administrator bootstrap command.
- [ ] Verify unauthenticated, forbidden, and authorized API behavior.

**Frontend Tasks**
- [ ] Implement NextAuth login with Keycloak.
- [ ] Add access token, refresh token, and role handling to the session.
- [ ] Implement automatic token refresh.
- [ ] Add token caching and session-expired detection to the Axios client.
- [ ] Pass the selected language to the Keycloak login page.
- [ ] Implement Keycloak logout.
- [ ] Protect all private pages by default.
- [ ] Create the public route group.
- [ ] Create the not-found page.
- [ ] Create the public account deletion instruction page.
- [ ] Build the loading splash screen.
- [ ] Build the route and role table.
- [ ] Build role-aware sidebar navigation.
- [ ] Implement the proxy route guard.
- [ ] Add role-based action visibility.
- [ ] Implement idle timeout and automatic logout.
- [ ] Implement session-expired handling.

**Completion Check**
- [ ] API requests return 401 without a token and 200 with a valid token.
- [ ] Tampered and expired tokens are rejected.
- [ ] Role-protected endpoints return 200 or 403 correctly.
- [ ] Login completes and the session contains the access token and roles.
- [ ] Token refresh works without requiring a new login.
- [ ] The Axios client attaches tokens and emits the session-expired event on a 401.
- [ ] Logout ends the Keycloak session.
- [ ] The Keycloak login page follows the selected application language.
- [ ] Private pages redirect to login and return to the original URL.
- [ ] Public pages are accessible without login.
- [ ] Forbidden routes redirect and forbidden actions are hidden.
- [ ] Idle timeout and session-expired flows work.

### Feature 2: Grades Management, Audit Trail, Filtering, and Multilingual Content

**Backend Tasks**
- [ ] Create the grades migration and model.
- [ ] Create the grade API resource.
- [ ] Implement grade list, detail, create, update, status toggle, and reorder.
- [ ] Add active grades and grade filter option endpoints.
- [ ] Add grade uniqueness validation and pagination.
- [ ] Create audit log storage and audit action definitions.
- [ ] Add automatic authorship and audit hooks to grades.
- [ ] Add bulk audit logging and the audit log retrieval endpoint.
- [ ] Create the filter engine and filter configuration storage.
- [ ] Seed filter configurations and apply generic filtering to grade lists.
- [ ] Create languages and grade translations storage.
- [ ] Add language management and active language endpoints.
- [ ] Add translation saving and retrieval to grade updates.
- [ ] Add the database seeding target.

**Frontend Tasks**
- [ ] Create the Grades service hooks and API interfaces.
- [ ] Build the Grade management page with list, search, filter, sort, and pagination.
- [ ] Build create and edit forms with translation editing.
- [ ] Add status toggle, reorder dialog, and role-based actions.
- [ ] Add grade translation and validation messages.

**Completion Check**
- [ ] All grade endpoints work.
- [ ] 401, 403, 404, and 422 responses behave correctly.
- [ ] Pagination metadata is correct.
- [ ] Authorship and audit logs are written.
- [ ] Filters and filter configurations work.
- [ ] Languages are seeded and grade translations are saved and returned.
- [ ] Grade service hooks and API interfaces are in place.
- [ ] The grade page supports list, search, filter, sort, pagination, create, edit, toggle, reorder, role gating, and translations.
- [ ] `make db-seed` works.

### Feature 3: Platform Settings, Files, and Uploads

**Backend Tasks**
- [ ] Create the file storage layer and upload, view, download, and existence endpoints.
- [ ] Create the platform settings storage and management endpoints.
- [ ] Add public platform settings, fallback configuration, and the fallback logo.
- [ ] Configure storage linking and file permissions.

**Frontend Tasks**
- [ ] Build the Platform settings page.
- [ ] Add logo upload and preview.
- [ ] Reuse platform name and logo in the admin shell.

**Completion Check**
- [ ] File upload and viewing work.
- [ ] Public platform settings work without a token.
- [ ] The login page displays the configured logo.
- [ ] The Platform settings page saves changes.

### Feature 4: User Groups, Admin Users, and Data Scoping

**Backend Tasks**
- [ ] Create user group storage, the administrator flag, and related foreign keys.
- [ ] Implement user group CRUD and status toggling.
- [ ] Implement admin user listing, detail, creation, and updates.
- [ ] Synchronize user groups and role mappings with Keycloak.
- [ ] Create the admin setup email and required actions.
- [ ] Implement reset two-factor authentication.
- [ ] Implement own-profile retrieval, account activation, and self-edit protection.
- [ ] Create the user-subject pivot and assigned-subject query scope.
- [ ] Add the approved-subject scope for teachers.
- [ ] Implement subject accessibility checks and apply data scoping to subject-related endpoints.

**Frontend Tasks**
- [ ] Build the Roles and Permissions page.
- [ ] Build the permission tree.
- [ ] Build the Users Management page.
- [ ] Add group and subject selectors to the user form.
- [ ] Add the reset two-factor authentication action.
- [ ] Add role and scope-aware actions.

**Completion Check**
- [ ] Groups synchronize to Keycloak with role mappings.
- [ ] Admin creation is atomic across both systems.
- [ ] The setup email is received.
- [ ] Permission changes apply immediately.
- [ ] Restricted administrators see only assigned subjects.
- [ ] The view-all-data role bypasses subject scoping.
- [ ] The Roles and Permissions and Users Management pages work.

### Feature 5: Content Catalogue

**Backend Tasks**
- [ ] Create the subjects table, model, resource, and controller.
- [ ] Add subject translations.
- [ ] Add subject pictogram upload.
- [ ] Add subject status management and reorder.
- [ ] Create the resources table, model, resource, and controller.
- [ ] Add resource translations and reorder.
- [ ] Create the activities table, model, resource, and controller.
- [ ] Add activity type and status enums.
- [ ] Add activity duration and resource relationships.
- [ ] Add activity usage lookup for courses.
- [ ] Create the attachments table, model, and controller.
- [ ] Add the attachment type enum and ordering.
- [ ] Add form requests and filter configurations.

**Frontend Tasks**
- [ ] Build the Subject management page.
- [ ] Build the Resource management page.
- [ ] Build the Activity management page.
- [ ] Add the activity detail view and attachments.
- [ ] Add unpublish warnings for activities used in courses.
- [ ] Add translations, pictogram uploads, and reorder interfaces.

**Completion Check**
- [ ] Subject, resource, activity, and attachment CRUD work.
- [ ] Enums cast correctly.
- [ ] Filter configurations exist for each list.
- [ ] Content pages support listing, creation, editing, translations, reorder, and role gating.

### Feature 6: Course Builder

**Backend Tasks**
- [ ] Create the course, module, outcome, session, and session activity tables and models.
- [ ] Implement course CRUD and duplicate validation.
- [ ] Implement module CRUD and ordering.
- [ ] Implement session CRUD and learning outcomes.
- [ ] Implement activity attachment, ordering, and status toggling.
- [ ] Implement course status and publishing rules.
- [ ] Add soft deletes, the active tracks count, and the course framework helper.

**Frontend Tasks**
- [ ] Build the Course management list and detail pages.
- [ ] Build the course builder.
- [ ] Add module, session, and activity ordering.
- [ ] Add learning outcome editing.
- [ ] Add the publish requirement checklist.
- [ ] Add the active tracks warning.
- [ ] Add the unsaved changes guard.

**Completion Check**
- [ ] Course tree CRUD works with ordering.
- [ ] Publish rules are enforced.
- [ ] Soft deletes are in place.
- [ ] The course builder creates and publishes a complete course.

### Feature 7: Configuration-Driven Dashboard

**Backend Tasks**
- [ ] Create and seed the dashboard and statistic configuration storage.
- [ ] Implement the dashboard endpoint with role filtering.
- [ ] Implement the statistic executor with fail-closed authorization.

**Frontend Tasks**
- [ ] Build the dashboard page with configured cards and responsive layout.
- [ ] Load statistics for each card.

**Completion Check**
- [ ] Cards are filtered by roles.
- [ ] Statistics are computed.
- [ ] Hidden statistics return 403.
- [ ] The dashboard renders configured cards with live numbers.

### Feature 8: UI Translation Management

**Backend Tasks**
- [ ] Create translation string storage and the mobile translations endpoint.
- [ ] Add admin translation update, export, and import.
- [ ] Create the default translation import command and translation file.
- [ ] Add the translation file sorting hook.

**Frontend Tasks**
- [ ] Build the Language management page with the inline translation table.
- [ ] Add translation editing and spreadsheet export and import.

**Completion Check**
- [ ] Translation strings are imported.
- [ ] The mobile translations endpoint works.
- [ ] The pre-commit hook sorts translation files.
- [ ] The Language management page works.

### Feature 9: Public Endpoints and Rate Limiting

**Backend Tasks**
- [ ] Create the public versioned route group.
- [ ] Add the teacher registration endpoint.
- [ ] Add the forgot-password endpoint.
- [ ] Add translations, active languages, subject options, resource options, pictogram, and attachment download endpoints.
- [ ] Add the account lock status endpoint.
- [ ] Add email change confirmation and cancellation pages.
- [ ] Configure named rate limiters.
- [ ] Ensure real client IP handling for throttling.

**Completion Check**
- [ ] Public versioned routes are available.
- [ ] Rate limits return 429 with the retry header.
- [ ] Forgot-password responses do not reveal account existence.
- [ ] Email links render a confirmation page before acting.

### Feature 10: Mobile Teacher API and Offline Sync

**Backend Tasks**
- [ ] Create device storage, the device middleware, registration, and status endpoints.
- [ ] Add teacher profile, interface language, password change, and account deletion endpoints.
- [ ] Add email change request and status endpoints.
- [ ] Add teacher subject requests and admin approval, rejection, and revocation.
- [ ] Add tracks, track setup options, matched courses, uniqueness checks, and course framework requests.
- [ ] Add session preparation, session delivery, and module preparation endpoints.
- [ ] Add activity ratings, activity statistics, sync metadata, and resource sync endpoints.
- [ ] Add idempotent offline upserts, sync failure logging, and offline session revocation.
- [ ] Add admin teacher and device management.

**Frontend Tasks**
- [ ] Build the Teacher management and teacher detail pages with the unregister device action.
- [ ] Build the Subject requests page with approve, reject, and revoke actions.

**Completion Check**
- [ ] Teacher registration and approval workflow work.
- [ ] Device binding is enforced.
- [ ] Tracks and offline outbox endpoints are idempotent.
- [ ] Teacher and Subject requests pages work.

### Feature 11: Queues and Data Exports

**Backend Tasks**
- [ ] Configure the database queue and the queue worker container.
- [ ] Create export history storage and export status and data type definitions.
- [ ] Add export request validation and role-based export access.
- [ ] Implement the export job, progress reporting, and export strategies.
- [ ] Implement export history, download, delete, retry, clear-all, and expired export cleanup.

**Frontend Tasks**
- [ ] Build the Data export page and export form.
- [ ] Add export history with infinite scroll and download, retry, and delete actions.

**Completion Check**
- [ ] The queue worker processes jobs.
- [ ] The export job generates files.
- [ ] History, download, delete, and retry work.
- [ ] Users see only their own exports.
- [ ] The Data export page works.

### Feature 12: Real-time Updates

**Backend Tasks**
- [ ] Install and configure Laravel Reverb with its container and Traefik route.
- [ ] Configure broadcasting authentication.
- [ ] Create the export progress and subject request status events and authorize private channels.

**Frontend Tasks**
- [ ] Configure Laravel Echo and Pusher with the Echo provider and listener hook.
- [ ] Add live export progress, automatic download, and live subject request updates.

**Completion Check**
- [ ] Reverb runs behind Traefik.
- [ ] Private channel authentication returns a signature.
- [ ] Events broadcast without errors.
- [ ] The browser WebSocket connection succeeds.
- [ ] Export progress and subject request updates are live.

### Feature 13: Email and PDF Generation

**Backend Tasks**
- [ ] Create the transactional mailables and email templates.
- [ ] Create the PDF templates and helpers for lesson plans, session reports, and course frameworks.
- [ ] Create queued email and PDF jobs and configure SMTP.
- [ ] Add the test lesson plan command.

**Completion Check**
- [ ] Mailables send to MailHog.
- [ ] PDFs with Khmer text render correctly.
- [ ] Heavy email and PDF work runs through the queue.

### Feature 14: Scheduled Maintenance

**Backend Tasks**
- [ ] Create the expired export cleanup and activity statistics commands.
- [ ] Define the scheduled tasks, log pruning, and retention configuration.
- [ ] Add the scheduler container.

**Completion Check**
- [ ] The schedule is listed.
- [ ] The scheduler runs continuously.
- [ ] Prunable models are configured.
- [ ] Scheduled commands run successfully.

### Feature 15: Mobile Client Orientation

**Frontend Tasks (Mobile App)**
- [ ] Review the mobile authentication flow.
- [ ] Review the mobile routes and screens.
- [ ] Review offline-first storage and synchronization.
- [ ] Review the mobile API integration.
- [ ] Review the mobile release tooling.

**Completion Check**
- [ ] I can explain how the mobile app authenticates.
- [ ] I can explain offline-first synchronization and idempotent backend behavior.
- [ ] I know which backend features support the mobile app.

---

## 4. Phase 3: Final Integration and Quality Assurance

### Backend Testing

- [ ] Configure the isolated test environment with an in-memory database and database refresh.
- [ ] Write Pest feature tests for Grades with grade and user factories.
- [ ] Fake Keycloak authentication, userinfo, and Admin API responses.
- [ ] Run the backend test suite.

### Production Integration and Deployment

- [ ] Build the production web client image with multi-stage output, nginx, supervisord, and environment-based configuration.
- [ ] Create the staging and production Compose files.
- [ ] Add production queue worker and scheduler services.
- [ ] Create staging and production deploy targets and environment files.
- [ ] Verify the staging and production deployments.

### Final End-to-End Verification

- [ ] Rebuild the system from zero with `make setup`.
- [ ] Verify all expected containers are running.
- [ ] Verify HTTPS, HTTP redirects, and Traefik routers.
- [ ] Verify Adminer access to both databases.
- [ ] Verify Keycloak discovery and issuer URLs.
- [ ] Verify the branded login page in English and Khmer.
- [ ] Verify the forgot-password email and brute-force lockout.
- [ ] Verify API authentication and role enforcement.
- [ ] Verify audit logs are written.
- [ ] Verify web login, redirect behavior, and sidebar permissions.
- [ ] Verify all admin pages are available and registered with the correct roles.
- [ ] Verify grade CRUD, translations, and reorder.
- [ ] Verify user group and admin user flows.
- [ ] Verify course creation and publishing.
- [ ] Verify export progress and automatic download.
- [ ] Verify live subject request updates.
- [ ] Verify idle timeout and language persistence.
- [ ] Verify all admin page strings are translated.
- [ ] Verify teacher registration and subject requests.
- [ ] Verify device binding.
- [ ] Verify the mobile translations endpoint.
- [ ] Verify linting, type checking, pre-commit hooks, and main branch protection.
- [ ] Verify backend tests pass.

---

## 5. Final Completion Checklist

- [ ] The project bootstraps from zero with `make setup`.
- [ ] The complete infrastructure stack starts from a clean machine.
- [ ] The five repositories are complete and integrated.
- [ ] Backend and frontend projects are initialized and connected.
- [ ] Every feature in Phase 2 is implemented.
- [ ] Backend and frontend tasks for every feature are complete.
- [ ] All Phase 1, Phase 2, and Phase 3 completion checks pass.
- [ ] All three end-to-end user journeys work.
- [ ] All automated tests and quality checks pass.
- [ ] Staging and production deployments are verified.
- [ ] Documentation reflects the final setup and workflow.
