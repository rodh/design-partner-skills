---
name: wireframing-partner
description: Use when the user asks to wireframe, mockup, or visually sketch proposed
  page changes, new sections, layout modifications, or before/after comparisons
---

## Overview

Produces self-contained HTML wireframes that communicate proposed page changes through a **fidelity gradient**: existing content renders as low-fidelity placeholders (real headings + gray bars), while proposed content renders at full detail. This automatic contrast draws the viewer's eye to what's new without any labels or legends. The wireframe uses a consistent visual language — browser chrome frames, annotation callouts, before/after comparisons, and a "Show proposed" toggle for dashed accent borders around new sections.

## When to Use

- User asks to wireframe, mockup, or sketch a page change
- User wants to visualize proposed new sections or features on an existing page
- User needs before/after comparisons of a UI change
- User provides a screenshot and wants to show additions integrated into the real layout
- User asks for layout variations (tabs) of the same concept

## When NOT to Use

- User wants production-ready UI code (use frontend-design skill instead)
- User wants a design system or style guide (use design-system-extractor)
- User is asking about UX strategy without needing a visual artifact
- The task is pure content writing with no visual layout component

## Phase 1 — Intake

Read the user's description of what page or feature they're wireframing. Scan for existing screenshots, design artifacts, or scope docs relevant to this work — check the artifact directory and one level of subfolders.

Identify:
- **What exists today** — the current page layout, sections, and structure
- **What's being proposed** — the new content, sections, or changes
- **How many examples/variations** are needed (one tab per variation)
- **Whether a screenshot was provided** — if so, you will match its layout faithfully

If a screenshot is provided, study it carefully. You will reproduce the actual column structure, sidebar placement, section order, and spacing. Don't invent a new layout — integrate proposed additions into the real layout.

If anything is ambiguous, ask one question via `AskUserQuestion` before proceeding. Don't block on minor details — mark gaps as assumptions and move on.

Check for **project templates** in the `wireframes/` subdirectory under the artifact directory — files prefixed with `_` (e.g., `_<project-name>-template.html`). If one exists for the project being wireframed, read it. Project templates contain project-specific CSS, HTML patterns, and reusable components that must be used for consistency across wireframes in that project.

## Phase 2 — Structure

Decide the wireframe layout before generating:

- **Single page or multi-page flow?** If the proposal involves clicking through to a new page, use a `.page-connector` between `.page-chrome` blocks.
- **How many tab variations?** One tab per location type, approach, or example. Use tabs when showing the same concept across different contexts.
- **What existing sections to show?** Render these as low-fidelity placeholders — real headings, placeholder bars for body content.
- **What new sections to show?** Render these at full fidelity — real text, real data, real structure.
- **Before/after comparison needed?** Use `.comparison-demo` blocks (the generalized LLM demo pattern) when showing how the proposal changes an outcome.

Tell the user your proposed structure in 2–3 sentences, then generate.

## Phase 3 — Generate

Produce a single self-contained HTML file using the component library in the reference files. Save to the `wireframes/<descriptive-name>.html` subdirectory under the artifact directory.

Create the `wireframes/` subdirectory under the artifact directory if it doesn't exist.

If a **project template** was found in Phase 1, use it as the foundation: combine the base CSS library with the project-specific CSS from the template, use its HTML skeleton, and draw from its reusable components. Add wireframe-specific CSS only for elements not already in the template.

### Container Width

Default `.container` uses `max-width: 960px`. Override to `1200px` or `100%` for wider layouts, either inline or in a project template.

### Layout and Composition

The base library provides **atomic components** and **navigation primitives** — not layout systems. Multi-column grids, hero layouts, banner compositions, page-specific structures, and other layout patterns should be:

- **Defined per-wireframe** when used only once
- **Extracted into a project template** when shared across 2+ wireframes in the same project

This keeps the base library project-agnostic. Compose layouts from the atomic components in the reference files.

### Fidelity Gradient

This is the core visual communication principle. Existing and new content render at different fidelity levels to create automatic contrast between "context" and "the point":

**Existing sections — low fidelity, but structurally faithful to the page:**

*What uses real text:*
- Section headings matching the actual page (e.g., "About", "Hours", "Business Details" — not meta-descriptions like "Business Details + Hours" or "Action Buttons")
- The business/page **name** (e.g., "Dunkin'") — orients the viewer to which page they're looking at

*What becomes placeholder shapes:*
- Body content (paragraphs, descriptions): placeholder bars
- Data values (addresses, phone numbers, URLs, hours, ratings, review text): placeholder bars
- Action buttons: unlabeled gray pill shapes preserving count and layout
- Badges/tags: unlabeled gray pills
- Images/maps: gray rectangles with small centered alt text describing what they represent (e.g., "HERO BANNER IMAGE", "MAP", "PHOTO GALLERY")

*Layout structure — preserve the page skeleton:*
- Render each distinct page area as its own structural block — header, breadcrumbs, hero, name block, button row, details grid, etc.
- Never merge multiple areas into a single generic labeled block
- Preserve column layouts (e.g., two-column grid for details + hours, each with its own heading)
- Preserve spatial relationships (e.g., buttons in a row, social links in a row)
- When a screenshot is provided, match its structure faithfully

*Style constraints:*
- **No color anywhere** in existing sections — everything is grayscale using `var(--existing-border)`, `var(--tag-bg)`, and `var(--text-secondary)`
- **No emoji or icons** in existing content

**New/proposed sections — high fidelity, this is the point:**
- Real text, real data, real structure — full detail
- This is what the wireframe exists to communicate; it should be immediately readable and visually prominent
- Compose proposed content from atomic components: use `.alert` for tips/warnings, `.chip` for tags, `.badge` for status indicators, `.data-table` for tabular data, `.stat-card` for metrics, `.feature-card` for feature descriptions, etc.
- **The dashed accent border (via the "Show proposed" toggle) is the ONLY visual marker** distinguishing proposed from existing. Do not add background colors (e.g., `accent-light` background), colored text, or accent-colored labels to proposed sections — unless the color is part of the actual design recommendation being presented. The fidelity contrast does the work; the dashed border confirms it.

**The test:** If you removed the dashed accent borders, could a viewer still instantly tell which content is proposed vs. existing? Existing sections should feel like the page's gray skeleton — recognizable layout and shapes, but no readable content. If existing sections have color or filled-in data, the fidelity gradient is broken. Conversely, if existing sections are collapsed into generic labeled blocks that all look the same, the wireframe loses the page's identity and the viewer can't orient themselves.

### Screenshot Fidelity

When a screenshot of the existing page is provided, **match its layout faithfully**:
- Reproduce the actual column structure, sidebar placement, section order, and spacing
- Don't invent a new layout — integrate proposed additions into the real layout
- Only deviate from the screenshot layout if the user explicitly asks for layout changes

### Component Library Reference

**You must Read these two files during generation:**

1. **`~/.claude/skills/wireframing-partner/css-library.md`** — contains the full CSS template (Google Fonts link + `<style>` block). Copy the entire code block verbatim into the wireframe's `<head>`.

2. **`~/.claude/skills/wireframing-partner/html-components.md`** — contains all HTML component snippets, interactive component guidelines, and tab switching JS. Use these exact structures and classes when building wireframe content.

### Output File Structure

Every wireframe follows this skeleton:

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Wireframe — [Descriptive Title]</title>
<!-- Google Fonts link from css-library.md -->
<!-- Full CSS from css-library.md -->
</head>
<body>

<div class="topbar">
  <div class="topbar-title">
    <div><span>[Project]</span> — [Design Concept Name]</div>
    <div class="topbar-subtitle">[Page/Area Context]</div>
  </div>
  <!-- If multiple variations: .tab-nav with .tab-btn buttons -->
  <label class="toggle-label highlights-toggle">
    <input type="checkbox" id="highlights-toggle" checked>
    <span class="toggle-track"></span>
    Show proposed
  </label>
</div>

<div class="container">
  <!-- If tabs: wrap each variation in <div id="tab-[name]" class="tab-content"> -->
  <!-- Page chrome blocks, new sections, annotations, comparisons -->
</div>

<!-- Highlights toggle JS (always included) -->
<script>
const ht = document.getElementById('highlights-toggle');
function updateHighlights() {
  document.body.classList.toggle('highlights-on', ht.checked);
}
ht.addEventListener('change', updateHighlights);
updateHighlights();
</script>
<!-- If tabs: include tab switching JS from html-components.md -->
</body>
</html>
```

## Phase 4 — Annotate

After generating the wireframe HTML, add:

1. **Annotation callouts** (`.annotation`) — explain *why* proposed changes matter, not just what they are. **One annotation per page-chrome block**, placed immediately after it. Each annotation should focus on the specific design decisions in that wireframe — not repeat points from other annotations. When the wireframe shows a multi-page flow (e.g., sidebar summary → full detail view), each page's annotation addresses what that particular view contributes and why.
   - When an annotation lists multiple numbered points, format each on its own line using `<br>`. Bold the number and pattern name with `<strong>`, keep the description in regular weight. This makes the callout scannable — the reader can count points at a glance and jump to the one that interests them.

2. **Before/after comparisons** (`.comparison-demo`) — if the proposal changes how something works for end users, show a concrete scenario with the before (gap/failure) and after (improvement). Use real-sounding scenarios, not abstract ones.

These should already be woven into the HTML during generation. This phase is a checklist to confirm they're present and useful.

## Quick Reference

| Category | Components |
|---|---|
| **Navigation** | Navbar, Sidebar nav, Bottom nav, Breadcrumb nav, Tab navigation, Pagination |
| **Wireframe Structure** | Page chrome, Existing section, New section, Page connector, Annotation, Before/after comparison |
| **Content** | Stat card, Feature card, Data table, Hero banner, Chip/chip-group, Badge (4 variants), Avatar (3 sizes), Empty state, Skeleton (4 types) |
| **Forms** | Text input, Textarea, Search field, Toggle switch, Select dropdown, Accordion, Checkbox group, Radio group |
| **Feedback** | Alert (info/success/warning/error), Progress bar |
| **Overlays** | Modal dialog, Dropdown menu |
| **Actions** | Action buttons (primary + secondary), Action row |

## Common Mistakes

| Don't | Do |
|---|---|
| Use accent orange on content elements (links, labels, arrows, body text) | Reserve accent orange for wireframe structure only (dashed borders, page connectors, topbar project name). Content links use `var(--link)`, labels use `var(--text-secondary)` |
| Add section-divider borders between every section | Only use borders when the original design has them or they serve a specific structural purpose (e.g., separating a two-column grid from the next area). Spacing and padding create sufficient separation |
| Use `<div>` or `<span>` for interactive elements | Use `<button>` for actions, `<input>`/`<textarea>`/`<select>` for form fields, `<details>`/`<summary>` for accordions, `<dialog>` for modals |
| Skip the highlights toggle | Always include the "Show proposed" toggle in the topbar. It defaults to on, showing dashed borders around new sections |
| Render existing sections at full fidelity | Existing sections get section headings + business name as real text, everything else as gray placeholder shapes. Full detail is reserved for proposed content |
| Use color in existing sections (green badges, purple logos, colored banners) | All existing content is grayscale — `var(--existing-border)`, `var(--tag-bg)`, `var(--text-secondary)` only |
| Put emoji icons in existing buttons or labels | Existing buttons are unlabeled gray pill shapes. No emoji anywhere in existing content |
| Write readable body text in existing sections (addresses, phone numbers, hours, URLs) | Replace all body content and data values with placeholder bars. Only section headings and the business name use real text |
| Collapse multiple distinct page areas into a single labeled block (e.g., "Site Header + Breadcrumbs + Hero") | Render each area as its own structural block — header, breadcrumbs, hero, name, buttons, details grid are all separate |
| Reproduce full data structures (hours tables, review bar charts, ratings) in existing sections | A few placeholder bars convey "there's a table here" without competing with proposed content |
| Add background colors or accent-colored labels to proposed sections to make them "pop" | The dashed accent border (via the toggle) is the only structural marker. Fidelity contrast does the rest. Only use color in proposed content if it's part of the actual design recommendation |

## Artifact Directory

Skills save artifacts to the configured artifact directory. To configure, add `Artifact directory: <path>` to your project's CLAUDE.md. Default: `artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check the artifact directory and one level of subfolders. Before writing, check if an artifact already exists at the target path — read it and reflect awareness of prior work.

## Rules

1. **Self-contained HTML** — must work by opening the file in a browser. No build step, no external dependencies except Google Fonts.
2. **One file per concept** — use tabs for variations within a single concept.
3. **Match screenshot layout when provided** — reproduce actual column structure, sidebar placement, section order, and spacing. Don't invent a new layout.
4. **Use the component library exactly** — no new colors, font stacks, or component patterns. Consistency IS the value. Read `css-library.md` and `html-components.md` for the full reference.
