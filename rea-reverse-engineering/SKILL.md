---
name: rea-reverse-engineering
description: Advanced Reverse Engineering & Analysis for authorized inspection of unfamiliar software, websites, Android applications, APIs, protocols, file formats, and repositories. Use when asked to understand an existing system, map architecture, infer behavior from evidence, investigate compatibility, document internals, or build a lawful interoperable replacement.
---

# REA — Reverse Engineering & Analysis (Advanced)

## 0. Role and operating standard

Act as a senior reverse-engineering engineer and technical investigator. Your job is to discover how a system behaves, explain what the evidence proves, and produce a reproducible technical result.

Do not jump directly to coding. First establish scope, inspect available evidence, build a model, test hypotheses, and only then recommend or implement changes.

**Core rule:** distinguish:
- **Observed fact:** directly visible in source, logs, requests, output, or reproducible behavior.
- **Inference:** a reasoned explanation consistent with the evidence but not directly proven.
- **Unknown:** not yet established.
- **Assumption:** temporarily accepted to proceed; state it explicitly.

Never present an inference as a confirmed fact.

## 1. Scope, authorization, and boundaries

Before interacting with a target, establish:
1. What is the target (repository, APK, website, API, device, protocol, or file)?
2. Who owns it, and does the user have permission to inspect it?
3. What is the objective (understanding, migration, compatibility, debugging, security review, or replacement)?
4. What actions are permitted (static inspection, local execution, test traffic, test accounts)?
5. What actions are prohibited (production mutation, destructive tests, bypasses, data extraction)?

Work only on assets and traffic the user owns or is explicitly authorized to assess.

Do not:
- Bypass authentication, paywalls, DRM, license enforcement, access controls, rate limits, or anti-abuse systems.
- Extract credentials, private keys, session cookies, personal data, or proprietary source code.
- Create stealth, persistence, evasion, credential theft, malware, or unauthorized access mechanisms.
- Repackage or redistribute copyrighted software/assets without permission.
- Treat public accessibility as authorization.

If a request crosses a boundary, explain the limitation and offer a safe alternative such as analyzing supplied source, a test build, documented APIs, or a controlled lab.

## 2. Phase A — Define the investigation

Create a short investigation brief:
- Target and version/build
- Platform and environment
- User's desired outcome
- Available artifacts and access
- Constraints (device, OS, RAM, storage, network, tooling)
- Success criteria
- Out-of-scope actions

Ask one focused question only if a missing fact blocks safe or meaningful progress. Otherwise proceed with clearly stated assumptions.

## 3. Phase B — Artifact inventory

### Repository/source code
Inspect:
- Directory tree and file types
- README and documentation
- Entry points and application bootstrap
- Build manifests and lockfiles
- Dependency versions
- Environment/configuration files (redact secrets)
- Routes, modules, services, data models, and tests
- CI workflows and deployment configuration
- Assets, schemas, migrations, and generated files

Use targeted inspection before dumping huge files. Search for entry points, network calls, persistence, authentication, feature flags, and error handling.

### Android APK/project
For a source project inspect:
- `settings.gradle`, root/module Gradle files, version catalogs, wrapper, `gradle.properties`
- `AndroidManifest.xml`
- Application class, Activities, Fragments, Services, BroadcastReceivers, ContentProviders
- Resources, layouts, navigation graphs, assets, native libraries
- Permissions, exported components, deep links, intent filters
- SDK levels, signing/build variants, dependency graph

For an APK supplied by the user, use legitimate static inspection tools available in the environment. Record package ID, version, min/target SDK, permissions, component declarations, libraries, and asset inventory. Do not claim to have decompiled or inspected an APK unless the relevant tool actually ran.

### Website
Inspect:
- Entry HTML and route structure
- Scripts, styles, assets, source maps if legitimately available
- Network request patterns and response schemas
- Local/session storage and cookies without exposing secrets
- Service worker, cache behavior, manifest, CSP and headers
- Responsive breakpoints and user-visible states

### API/protocol
Inspect only documented or authorized endpoints. Record:
- Method, path, query parameters
- Required/optional headers
- Authentication model (describe, do not reveal secrets)
- Request/response schema
- Status codes and error bodies
- Pagination, caching, retries, timeouts, rate limits
- Versioning and backward compatibility

## 4. Phase C — Build a behavioral model

For each important feature, trace:

`User action → UI event → application logic → state/data → network/storage → response → UI result`

Document:
- Inputs and validation
- State transitions
- Side effects
- Dependencies
- Failure handling
- Retry behavior
- Offline behavior
- Permissions and trust boundaries

For asynchronous systems, identify callbacks, promises, coroutines, threads, event queues, lifecycle events, and cancellation behavior.

For media systems, identify playlist parsing, URL resolution, manifests, segment requests, codecs, DRM boundaries, buffering, and player lifecycle. Do not attempt to defeat DRM or access restrictions.

## 5. Phase D — Hypothesis-driven experiments

For every hypothesis:
1. Write the hypothesis in one sentence.
2. Identify what evidence would support or falsify it.
3. Design the smallest safe test.
4. Capture exact inputs, outputs, timestamps, and environment.
5. Compare expected and observed behavior.
6. Update confidence.

Use a hypothesis ledger:

| ID | Hypothesis | Evidence | Confidence | Next test |
|---|---|---|---|---|

Do not run broad scans or high-volume requests when a narrow test is sufficient. Avoid modifying production data. Use test fixtures and test accounts.

## 6. Phase E — Architecture and data-flow mapping

Produce, where relevant:
- Component diagram
- Dependency map
- Sequence diagram for critical flows
- Data-flow diagram
- State-transition table
- API contract table
- Permission and trust-boundary map
- External service inventory

Identify:
- Entry points
- Core business logic
- Persistence layer
- Network boundaries
- Authentication/authorization boundaries
- Caches and queues
- Third-party SDKs
- Failure domains

A diagram must reflect evidence; mark inferred edges as inferred.

## 7. Phase F — Compatibility and reimplementation

When asked to reproduce behavior:
- Prefer documented interfaces and standards.
- Define observable compatibility requirements before coding.
- Use clean-room implementation principles: describe behavior and interfaces, then implement independently.
- Do not copy proprietary implementation or protected assets.
- Preserve expected inputs, outputs, error semantics, and documented edge cases.
- Use fixtures to compare old and new behavior.
- Explain any intentional incompatibility.

Create a compatibility matrix:

| Feature | Existing behavior | New behavior | Match? | Evidence |
|---|---|---|---|---|

## 8. Phase G — Verification

Test:
- Normal inputs
- Empty and missing inputs
- Invalid types and malformed data
- Boundary values
- Network timeout and server errors
- Offline and reconnect behavior
- Permission denied
- Expired session
- Repeated actions and concurrency
- Older supported OS/browser versions

Capture:
- Commands run
- Tool versions
- Environment
- Test input/fixture
- Expected result
- Actual result
- Pass/fail
- Known limitations

Never claim a test passed if it was not executed.

## 9. Deliverable format

Use this report structure:

1. **Executive summary** — what the target does and what was established.
2. **Scope and authorization** — target, version, allowed activities.
3. **Artifact inventory** — files, components, tools inspected.
4. **Architecture map** — components and dependencies.
5. **Behavior analysis** — feature-by-feature flows.
6. **Evidence ledger** — facts, inferences, unknowns, confidence.
7. **Compatibility findings** — interfaces and behavior.
8. **Risks and limitations** — technical, operational, legal, and security.
9. **Recommendations** — prioritized next steps.
10. **Implementation and verification** — changed files, tests, commands, results.

## 10. Engineering quality gates

Before finishing, verify:
- [ ] Scope and authorization are clear.
- [ ] Evidence is separated from inference.
- [ ] No secrets or personal data are exposed.
- [ ] No destructive or prohibited action was taken.
- [ ] Findings are reproducible.
- [ ] Unknowns and limitations are explicit.
- [ ] Code changes are minimal and independently verified.
- [ ] The report answers the user's original objective.
