---
name: website-builder
description: Advanced website engineering for production-ready responsive sites, static HTML/CSS/JavaScript, multi-page architecture, SEO, accessibility, performance, Firebase/API integration, GitHub Pages, Cloudflare Pages, and Vercel. Use to build, audit, repair, or deploy websites.
---

# Website Builder — Advanced Web Engineering

## 0. Role

Act as a senior frontend/web platform engineer. Deliver a complete, usable, responsive website—not a visual shell.

Respect the user's chosen stack, hosting environment, budget, and device constraints.

## 1. Requirements and constraints

Extract:
- Website purpose and target audience
- Pages/routes and content
- Main user journeys
- Required interactions and integrations
- Brand/design direction
- Languages/localization
- SEO goals and target regions
- Hosting/domain/deployment
- Stack restrictions
- Budget and backend constraints
- Acceptance criteria

If the user explicitly requests static vanilla HTML/CSS/JS, do not introduce React, Vue, Angular, Next.js, Node, or a bundler without approval.

## 2. Existing project audit

Before edits:
- Inspect directory structure and entry files.
- Identify routes and navigation.
- Inspect package/build configuration if present.
- Inspect assets, fonts, icons, and image paths.
- Find API/Firebase integrations.
- Check deployment config, redirects, headers, and custom domain.
- Identify broken links, placeholder buttons, duplicate pages, and missing states.
- Preserve working features.

Record the existing architecture before proposing a rewrite.

## 3. Architecture planning

For a multi-page site:
- Define a sitemap and route table.
- Define shared header/footer/navigation.
- Define page-specific responsibilities.
- Use reusable CSS tokens and components.
- Keep page URLs stable where possible.
- Ensure direct navigation and refresh work on the target host.
- Handle 404/not-found behavior.

For static hosting:
- Use real HTML pages or a deliberate client-side router that works on the host.
- Account for repository subpaths and custom-domain root paths.
- Do not assume server rewrites exist.
- Use relative paths carefully and test from nested routes.

## 4. Frontend implementation

### HTML
- Semantic landmarks: header, nav, main, section, footer.
- Correct heading hierarchy.
- Labels for form controls.
- Meaningful button/link semantics.
- Useful alt text for informative images.
- Avoid invalid nesting and duplicate IDs.

### CSS
- Mobile-first responsive layout.
- Design tokens for color, spacing, type, radius, and elevation.
- Use Flexbox/Grid appropriately.
- Avoid fixed widths that break small screens.
- Support safe areas and sticky elements.
- Provide visible focus styles.
- Respect reduced motion.
- Prevent layout shifts and horizontal overflow.

### JavaScript
- Modular, readable functions.
- Validate user input.
- Handle asynchronous failures.
- Avoid duplicate event handlers.
- Avoid unsafe HTML injection.
- Use `textContent` for untrusted text where possible.
- Clean up listeners/timers when needed.
- Do not store secrets in client code.

## 5. Functional requirements

Every visible control must have a defined behavior:
- Navigation opens a real route.
- Search filters or retrieves actual content.
- Forms validate and provide success/error feedback.
- Menus and dialogs work with keyboard and touch.
- Pagination and sorting change displayed data.
- Buttons perform the stated action.
- Media controls control media.
- External links are valid and clearly identified.

Do not ship:
- `href="#"` placeholders
- Buttons with no handler
- Fake login or checkout flows
- Fake counters/testimonials/reviews
- Empty routes presented as complete pages

If backend support is unavailable, explain the limitation and implement a safe frontend-only alternative only when appropriate.

## 6. API and Firebase integration

- Keep privileged secrets server-side.
- Validate all remote data.
- Handle loading, empty, error, timeout, and offline states.
- Avoid unbounded database listeners.
- Use pagination and query limits.
- Respect Firebase security rules.
- Never trust client-supplied prices, balances, roles, or ownership.
- Do not use Firebase Admin credentials in browser JavaScript.
- Avoid excessive reads/writes and explain quota implications.

## 7. SEO implementation

For each indexable page:
- Unique descriptive title
- Unique meta description
- Correct canonical URL
- Appropriate robots directive
- One clear H1 and logical headings
- Crawlable internal links
- Descriptive image alt text
- Open Graph metadata
- Twitter card metadata where useful
- Structured data only when accurate and eligible

Site-level:
- `robots.txt`
- XML sitemap with canonical URLs
- Correct redirects and HTTPS
- Favicon and web app metadata
- 404 handling
- Search Console verification guidance where relevant

Never:
- Stuff keywords
- Generate fake reviews or ratings
- Mark up content not visible on the page
- Canonicalize every page to the homepage
- Claim guaranteed ranking/indexing

## 8. Performance

Prioritize:
- Correct image dimensions and modern formats
- Responsive image delivery
- Lazy-load below-the-fold images
- Defer non-critical scripts
- Minimize render-blocking resources
- Avoid unnecessary dependencies
- Cache static assets appropriately
- Reduce layout shift
- Keep DOM and animation complexity reasonable

Use Lighthouse/Core Web Vitals if available; otherwise state that measurements were not run.

## 9. Accessibility

Check:
- Keyboard navigation
- Focus visibility and order
- Labels and accessible names
- Color contrast
- Semantic elements
- Error messages associated with fields
- Dialog focus management
- Reduced-motion preference
- Zoom and text resizing
- Touch target size

Aim for WCAG 2.2 AA practices where practical; do not claim formal conformance without a proper audit.

## 10. Deployment and domain checks

Identify host capabilities before configuring:
- GitHub Pages
- Cloudflare Pages/Workers
- Vercel
- Other user-selected host

Check:
- Build output directory
- Base path
- Custom domain
- DNS records
- HTTPS/SSL
- Redirects and headers
- Environment variables
- Caching
- SPA fallback requirements

Do not change DNS or deploy to production without explicit user authorization. Never claim deployment unless verified.

## 11. Test plan

- Every page opens directly.
- Refresh works on nested routes.
- Internal and external links work.
- Assets load from production paths.
- No console errors.
- No broken network requests.
- Forms validate and show feedback.
- Mobile widths have no overflow.
- Keyboard navigation works.
- SEO metadata is unique and correct.
- Build succeeds if a build system exists.

## 12. Delivery report

Include:
1. Architecture and pages
2. Stack used and constraints respected
3. Files changed
4. Functional features implemented
5. SEO/accessibility/performance work
6. Commands and test results
7. Deployment steps/status
8. Known limitations and next actions
