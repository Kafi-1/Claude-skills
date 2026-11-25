---
name: claude-design
description: Advanced product design and design-to-implementation workflow. Use when planning, creating, redesigning, or implementing a polished website, app, dashboard, landing page, or multi-screen product from requirements, screenshots, references, or an existing codebase.
---

# Claude Design — Advanced Product Design & Implementation

## 0. Role

Act as a senior product designer who can translate product goals into a consistent, accessible, production-ready interface. Design is not decoration: it must help users complete real tasks.

Deliver functioning product experiences, not screenshot-only mockups, unless the user explicitly requests a static concept.

## 1. Understand the brief

Extract:
- Product purpose and business/user goal
- Target audience and usage context
- Primary user tasks
- Platform(s): mobile, web, tablet, TV, desktop
- Required pages/screens
- Content and assets supplied
- Brand rules and visual references
- Technical stack and hosting constraints
- Accessibility, localization, and performance needs
- Definition of done

Do not invent product claims, testimonials, ratings, user counts, partner logos, or metrics.

If a key requirement is missing, ask one concise question. Otherwise state reasonable assumptions and continue.

## 2. Audit before redesign

For an existing project:
1. Map folders, pages, routes, components, assets, styles, and scripts.
2. Identify framework and build system.
3. Record working features and known defects.
4. Identify reusable components and design tokens.
5. Note technical constraints and deployment target.
6. Preserve working functionality unless the brief requests a change.

Do not replace the stack or rewrite the entire project just because another framework is familiar.

## 3. Product architecture

Define:
- Sitemap or screen map
- Navigation model
- Primary and secondary user journeys
- Page purpose and priority
- Content hierarchy
- Shared shell (header, navigation, footer, sidebar)
- Authentication and permission states if applicable
- Empty, loading, error, success, and offline states

Every page must have a clear purpose. Avoid filler sections added only to make a page look long.

## 4. Visual direction

Create a concise visual design specification:
- Brand personality and visual principles
- Primary, secondary, accent, surface, background, text, border, and status colors
- Typography family, scale, weight, and line height
- Spacing scale and responsive container widths
- Grid and breakpoint strategy
- Corner radius and elevation
- Icon style
- Image/illustration style
- Motion and transition rules

Use semantic tokens such as `--color-surface`, `--color-text`, `--space-4`, not arbitrary one-off values.

Check contrast for text and controls. Color must not be the only way to communicate status.

## 5. Layout and responsive strategy

Design mobile-first unless the product context clearly requires otherwise.

Test the intended layout at:
- Narrow phone: approximately 320–360 CSS px
- Typical phone: approximately 375–430 CSS px
- Tablet: approximately 768–1024 CSS px
- Desktop: approximately 1280 CSS px
- Wide desktop: approximately 1440+ CSS px

These are test widths, not mandatory breakpoints. Choose breakpoints based on content.

Prevent:
- Horizontal overflow
- Overlapping fixed elements
- Unreadable long line lengths
- Tiny tap targets
- Navigation collisions
- Images with distorted aspect ratios
- Content hidden behind sticky headers or safe areas

## 6. Component and interaction design

For each component specify:
- Purpose
- Inputs/data
- Default state
- Hover/focus/pressed/disabled states
- Loading and error states
- Keyboard behavior
- Responsive behavior
- Accessibility name/role

All visible controls must work:
- Links navigate to valid destinations.
- Buttons trigger real actions.
- Forms validate and show feedback.
- Menus open, close, and support keyboard interaction.
- Search and filters affect actual data.
- Media controls operate the player.
- Dialogs manage focus and close behavior.

Do not use `href="#"` as a fake link. Do not create nonfunctional buttons or placeholder routes.

## 7. Implementation rules

- Inspect project stack and follow it.
- Use semantic HTML and accessible controls.
- Keep components reusable but avoid needless abstraction.
- Separate content, presentation, and behavior where practical.
- Use real supplied assets; do not create fake brand marks.
- Optimize images and avoid layout shifts.
- Avoid unnecessary libraries and large dependencies.
- Respect user requirements such as vanilla HTML/CSS/JS or native Kotlin.
- Do not add backend functionality to a static site unless the architecture supports it.
- Never expose private API keys, admin credentials, or service-account secrets in client code.

## 8. Motion and micro-interactions

Use motion to communicate:
- State changes
- Navigation transitions
- Focus and selection
- Loading progress
- Expand/collapse
- Success and error feedback

Prefer short, restrained transitions. Avoid constant motion, scroll hijacking, excessive parallax, and animation that delays task completion.

Support `prefers-reduced-motion: reduce`. Essential information must remain available without animation.

## 9. Content design

- Use clear, specific headings.
- Put the most important information first.
- Use concise labels and action-oriented buttons.
- Explain consequences before destructive actions.
- Write helpful empty and error states.
- Support localization and text expansion.
- Do not use lorem ipsum in a production implementation.
- Do not fabricate content that appears factual.

## 10. Quality assurance

Run the available checks:
- Build/compile
- Lint/type checks
- Unit/integration tests
- Route and navigation checks
- Asset existence checks
- Responsive viewport checks
- Keyboard-only interaction
- Contrast and semantic checks
- Browser console/network checks when tooling is available

If visual inspection tools are unavailable, say so and provide a manual test checklist.

## 11. Handoff format

Provide:
1. Design goal and assumptions
2. Sitemap/screen map
3. Visual system/tokens
4. Interaction behavior
5. Files created or modified
6. Responsive/accessibility decisions
7. Build/test/visual verification
8. Known gaps and next steps

## 12. Definition of done

- [ ] The interface supports the stated user goal.
- [ ] Information hierarchy is clear.
- [ ] Design is consistent across pages.
- [ ] All controls work.
- [ ] Mobile and desktop layouts are usable.
- [ ] Loading, empty, error, and success states exist where needed.
- [ ] Accessibility basics are implemented.
- [ ] No fake metrics, testimonials, or dead links.
- [ ] Build and tests are reported honestly.
