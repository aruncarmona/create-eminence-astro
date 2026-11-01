# Development plan

Build the MVP in the order below. Use one feature commit per step, including its implementation, tests, dependency changes, and documentation.

## Foundation

- [ ] **01 Define the product** — Establish the MVP scope, conventions, and development plan. Commit: `docs(core): define the Eminence Astro product`.
- [ ] **02 Establish the CLI** — Add the executable, help, version, TypeScript toolchain, license, and CLI tests. Target Node.js 24 and supported pnpm version.
- [ ] **03 Validate project inputs** — Collect identity, destination, Git, and multilingual choices. Reject unsafe or non-empty destinations; support cancellation and unattended flags.
- [ ] **04 Initialize optional Git** — Check availability and identity, initialize before applying features, and support `--no-git` without changing global settings.
- [ ] **05 Apply ordered setup stages** — Define prerequisites, changes, installation, verification, progress reporting, and commit messages. Stop on failure and preserve files.
- [ ] **06 Generate minimal Astro** — Add the homepage, configuration, private manifest, matching lockfile, and project README. Verify installation and build before the first generated commit.
- [ ] **07 Configure strict TypeScript** — Add Astro checking, the source alias, and documented commands. Verify intentional type errors fail.
- [ ] **08 Configure formatting** — Add Prettier, appropriate plugins, output exclusions, and format/check commands. Verify Windows line endings.
- [ ] **09 Add component tests** — Configure Vitest for Astro and include a real rendering test that fails when behavior changes.
- [ ] **10 Establish CI** — Run frozen installation, formatting, type checks, tests, and builds using the declared runtime and package manager.

## Hosting and configuration

- [ ] **11 Define public and build settings** — Validate site identity and URLs, distinguish browser-visible values from server values, and provide `.env.example`.
- [ ] **12 Configure Cloudflare Workers** — Add the adapter, Wrangler configuration, tested compatibility date, generated binding types, and local production preview.
- [ ] **13 Demonstrate runtime variables and secrets** — Add `.dev.vars.example`, a public-value example, and a server-only example key. Test that secrets never appear in browser output.
- [ ] **14 Separate environments** — Document local, preview, and production settings, separate bindings and secrets, preview noindex behavior, and explicit deployment targets.

Use clearly fake example credentials. Ignore real secret files, assign each setting one configuration owner, and keep local development independent of production credentials.

## Website structure and styling

- [ ] **15 Configure Tailwind** — Add the Vite integration, global stylesheet, and shared color and typography variables. Do not install a component library.
- [ ] **16 Add accessible layouts** — Create document and default layouts, landmarks, skip navigation, visible focus, and useful slots.
- [ ] **17 Establish page and section conventions** — Keep routes in `src/pages/`, layouts in `src/layouts/`, shared components in `src/components/`, and page sections in `src/components/sections/<page>/`. Add one small page-composition example and document the conventions without creating empty folders.
- [ ] **18 Add Svelte islands** — Configure the integration and formatting. Test a hydrated fixture and confirm ordinary Astro pages avoid unnecessary Svelte client code.
- [ ] **19 Configure the font** — Use one family, the required styles, and a system fallback. Verify generated assets.
- [ ] **20 Add theme switching** — Support light, dark, and system modes, persistence, early application, keyboard access, storage failure, and a usable no-JavaScript appearance.
- [ ] **21 Configure metadata** — Integrate Eminence Astro Suite for titles, descriptions, canonicals, social metadata, and icons. Test escaping and duplicate-tag prevention.

## Localization and error pages

- [ ] **22 Add optional multilingual routing** — Default to English at `/` and Spanish at `/es/`. Translate visible text, metadata, and accessibility labels. English-only output must omit Paraglide and related files.
- [ ] **23 Add language navigation** — Derive languages from configuration, preserve the corresponding path and query string, and work without a client framework.
- [ ] **24 Complete localized SEO** — Generate public canonicals, reciprocal alternates, the chosen `x-default`, localized sitemap entries, and robots output through one sitemap owner.
- [ ] **25 Add the 404 page** — Return the correct status, localized explanation, reliable navigation, theme support, and accessible recovery. Exclude it from indexing and the sitemap.
- [ ] **26 Add the 500 page** — Use a minimal localized document independent of database, authentication, and email services. Include safe recovery and a request reference when available; keep internal errors private. Verify actual SSR failures using fixtures excluded from release.

Test nested routes, unsupported locales, and alternating language requests. Document the limits of application-level 500 handling.

## Email

- [ ] **27 Add Resend** — Use hosted templates through a server-only helper. Support disabled, mock, and explicitly configured live modes, a working local example, idempotency keys, and useful failure handling. Do not add React Email.
- [ ] **28 Localize email selection** — Map email type and locale to a template identifier or alias. Include welcome and notification examples in English and Spanish. Pass the resolved website locale explicitly; test fallback, missing mappings, variables, and concurrent requests.

Live sending requires explicit configuration. Identify mock examples as mock sends. Do not expose a generic public sending endpoint or send live email from automated tests.

## Packaging and release

- [ ] **29 Prepare setup checkpoints** — Bundle tested stage files, dependency specifications, and matching lockfiles for both language paths. Check out generated commits and verify the checks appropriate to each stage.
- [ ] **30 Verify the packed creator** — Invoke it outside the source checkout. Exercise both language paths, both Git choices, real installation, production builds, browser behavior, package contents, and Windows/Linux process handling.
- [ ] **31 Prepare the MVP release** — Version the creator and bundled setup together, require package verification, use a manual publication trigger, and follow the generated README from a fresh directory.
- [ ] **32 Retire the legacy starter** — Compare capabilities, replace remaining deployments and references, add a retirement notice, and archive after verification. Permanent deletion is separate.

## After the MVP

- [ ] **Database** — Choose the database and access tools, verify Workers compatibility, and add connection examples, environment isolation, queries, and migrations where applicable.
- [ ] **Authentication** — Choose a maintained solution compatible with the runtime and database. Add server-side authorization, session handling, protected-route examples, and localized account emails where needed.
- [ ] **Analytics** — Choose the provider and decide whether it becomes default. Add clear setup guidance and a small integration with local/preview tracking disabled unless explicitly enabled.
- [ ] **CMS** — Choose the client's workflow: an external service such as Strapi, repository content built into the site, or a justified custom editing experience. Validate content, exclude drafts, protect credentials, and document publishing and rebuilds.

## Setup stage rules

- Apply real project changes in order. Do not copy a finished application and manufacture empty commits.
- Record only completed stages with matching manifests and lockfiles.
- Run the same setup operations with Git disabled, omitting Git commands.
- State which checks were skipped when installation is disabled.
- Preserve files and identify the failed stage. Automatic resume is outside the MVP unless implemented and tested.
- Maintain one feature source; prepared checkpoints are generated artifacts.

## Documentation

Keep the creator README as a concise overview. Put detailed setup, commands, examples, and limitations in separate wiki pages for each feature. Update the relevant page with its feature rather than postponing documentation until release.

The generated project's README must describe its selected features, actual commands, configuration, customization, and deployment, with a link to the wiki. It should be sufficient for an experienced Astro developer to begin working.

## Feature completion checklist

- [ ] Define behavior and acceptance criteria.
- [ ] Implement the smallest complete version.
- [ ] Verify success and relevant failure cases using meaningful assertions.
- [ ] Update the relevant wiki page and affected README instructions.
- [ ] Include manifest and lockfile changes together.
- [ ] Check for secrets, personal configuration, unnecessary dependencies, and generated files.
- [ ] Run the checks available at this stage and review the diff.
- [ ] Create the feature commit when authorized.

## Boundaries

Prefer Node's standard library for arguments, files, paths, URLs, and simple CLI tests. Add dependencies when they avoid substantial maintenance; keep component and browser testing tools where needed.

Exclude daisyUI, Storybook, a separate component library, React Email, Biome, multiple frontend framework or package-manager implementations, and a generic plugin platform.

Project creation must not overwrite existing work, change global Git identity, create remote repositories, deploy applications, provision paid resources, or apply production migrations. Existing-project upgrades are outside the MVP.
