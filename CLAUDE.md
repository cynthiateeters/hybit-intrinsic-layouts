# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

**HAP's Learning Lab: Intrinsic Layouts** - A static HTML/CSS/JavaScript educational website teaching modern CSS intrinsic layout techniques through 6 interactive learning stations. HAP (HyBit A. ProtoBot™) is Prof. Teeters' apprentice who guides students through hands-on web development learning with his friendly first-person narrative.

This is a **pure HTML/CSS/JS project** with no build process, no frameworks, and zero npm dependencies (except optional Lighthouse CLI for batch testing).

**Current state**: This is a learning lab in development. The template infrastructure is complete (`templates/`, `.claude/skills/`, `css/`, `js/`), and curriculum planning is in progress (`reports/modern-css-layout-mastery/`). The `stations/` and `demos/` directories are prepared but stations have not yet been created from templates.

## Dual purpose

This repository serves two purposes:

1. **Active Learning Lab**: Creating "HAP's Intrinsic Layouts Learning Lab" teaching modern CSS layout techniques
2. **Reusable Template**: Providing infrastructure for creating additional HAP Learning Labs on other topics

**Template infrastructure includes**:

- **7 Claude Skills** - Progressive validation and standards enforcement
- **4 Templates** - Station HTML, demo HTML, curriculum plan, easter egg data
- **Static Assets** - HAP design system CSS, syntax highlighting, easter egg system
- **Documentation** - Complete guides for customization

**Current learning lab topic**: Modern CSS intrinsic layouts (container queries, aspect-ratio, clamp(), etc.)

## Common development commands

### Local development

```bash
# Start local server (required for JSON loading to work)
live-server --port=3000

# Then open http://localhost:3000 in browser
```

**Important**: Direct file opening (`file://` protocol) won't work due to CORS restrictions on JSON loading for the easter egg feature.

### Testing with Lighthouse

**Recommended method**: Use the DevTools MCP server (Claude Code's built-in browser automation):

```bash
# Claude Code can test pages directly using MCP
# Ask: "Test this page with Lighthouse using DevTools MCP"
# Or: "Run accessibility audit on all stations"
```

**Alternative method**: Use Lighthouse npm package for batch testing:

```bash
# Install dependencies (one time only)
npm install

# Run Lighthouse CI on all configured pages (requires local server on port 8000)
npm run lh:ci

# Run single-page Lighthouse tests:
npm run lh http://localhost:3000/index.html        # View in browser
npm run lh:desktop http://localhost:3000/index.html  # Desktop preset
npm run lh:mobile http://localhost:3000/index.html   # Mobile preset
npm run lh:html http://localhost:3000/index.html     # HTML report → reports/lh-report.html
npm run lh:json http://localhost:3000/index.html     # JSON report → reports/lh-report.json
npm run lh:csv http://localhost:3000/index.html      # CSV report → reports/lh-report.csv
```

**Lighthouse CI configuration** (`lighthouserc.json`):
- Tests `index.html` and all 6 station pages
- Requires local server on port 8000 (`python3 -m http.server 8000` or `live-server --port=8000`)
- Runs 3 passes per page for accuracy
- Enforces strict assertions: Performance ≥99, Accessibility/Best Practices/SEO = 100

**Performance targets**:

- Performance: ≥99/100
- Accessibility: 100/100
- Best Practices: 100/100
- SEO: 100/100

## Template architecture

### Zero dependencies approach

- **No build process**: Edit HTML/CSS/JS directly
- **No frameworks**: Pure vanilla JavaScript
- **No npm runtime dependencies**: Only Lighthouse for testing (optional)
- **CDN delivery**: Images served via Cloudinary CDN
- **Local fonts**: Variable fonts (Nunito, Source Code Pro) hosted locally in `fonts/` for performance
  - Nunito: Primary UI font (variable weight 200-1000, regular + italic)
  - Source Code Pro: Monospace for code (variable weight 200-900, regular + italic)
  - Format: WOFF2 variable fonts for optimal compression
  - `font-display: swap` for faster initial render
- **Progressive enhancement**: Works without JS (except easter egg system)

### File organization

```
hybit-intrinsic-layouts/
├── .claude/
│   └── skills/                # 7 Claude Skills for validation
│       ├── hap-voice/        # Voice and personality enforcement
│       ├── accessibility-check/ # WCAG 2.2 Level AA validation
│       ├── security-audit/   # OWASP Top 10, XSS prevention
│       ├── testing-framework/ # Testing decision matrix
│       ├── station-content/  # Station structure patterns
│       ├── demo-builder/     # Interactive demo patterns
│       └── css-standards/    # HSL color format enforcement
├── templates/
│   ├── station-template.html # Complete station HTML structure
│   ├── demo-template.html    # Interactive demo structure
│   ├── curriculum-plan-template.md # Content planning guide
│   └── hybit-insights-template.json # Easter egg messages
├── css/
│   ├── style.css             # HAP design system (~5400 lines)
│   └── prism-hap-theme.css   # Syntax highlighting theme (~224 lines)
├── js/
│   └── easter-egg.js         # HyBit insights system (~181 lines)
├── fonts/                    # Local font files for performance
│   ├── Nunito/               # Variable fonts (regular + italic)
│   └── Source_Code_Pro/      # Variable fonts (regular + italic)
├── data/
│   ├── README.md             # Easter egg documentation
│   └── hybit-insights.jsonc  # Easter egg content (to be created)
├── stations/                 # Station pages (to be created from templates)
│   └── README.md             # Directory documentation
├── demos/                    # Interactive demos (to be created from templates)
│   └── README.md             # Directory documentation
├── reports/                  # Planning and research documents
│   ├── claude-code-directive.md
│   └── modern-css-layout-mastery/  # Curriculum planning docs
├── index.html                # Hub page with [PLACEHOLDER] content
├── CLAUDE.md                 # This file
├── README.md                 # Template usage guide
├── VALIDATION-CHECKLIST.md   # Template infrastructure validation
├── package.json              # Lighthouse testing scripts
├── lighthouserc.json         # Lighthouse CI configuration
└── LICENSE, TRADEMARK.md, CONTENT-LICENSE.md  # Legal files
```

## Current project workflow

**For this intrinsic layouts learning lab**, the workflow is:

1. **Planning phase** (in progress): Curriculum planning documents in `reports/modern-css-layout-mastery/`
2. **Content creation** (next): Create 6 stations from `templates/station-template.html` → `stations/station[1-6].html`
3. **Demo creation**: Build interactive demos from `templates/demo-template.html` → `demos/[demo-name].html`
4. **Easter egg setup**: Customize `templates/hybit-insights-template.json` → `data/hybit-insights.jsonc`
5. **Hub page**: Complete placeholders in `index.html`
6. **Validation**: Run all 7 Claude Skills before deployment
7. **Testing**: Lighthouse CI validation (target: 99+/100 performance)
8. **Deployment**: Deploy to static host (Netlify, GitHub Pages, etc.)

**Important**: Before creating any station or demo files, consult the planning documents in `reports/modern-css-layout-mastery/` for the curriculum structure and HAP's learning journey.

## Template customization workflow

**For creating NEW learning labs on different topics**, follow this workflow:

### Step 1: Plan your curriculum

1. Read `templates/curriculum-plan-template.md`
2. Fill in all [PLACEHOLDER] sections
3. Save as `CONTENT-PLAN.md` in your new learning lab directory
4. Define 6 station topics that build progressively
5. Write HAP's struggles and learning moments in first-person

### Step 2: Set up Skills

Copy the `.claude/skills` directory to your new learning lab:

```bash
cp -r .claude ~/your-new-lab/.claude
```

Claude Code will automatically use these Skills for validation.

### Step 3: Copy static assets

```bash
cp -r css ~/your-new-lab/css
cp -r js ~/your-new-lab/js
cp -r data ~/your-new-lab/data
```

### Step 4: Customize templates

**For each station (1-6)**:

1. Copy `templates/station-template.html` → `stations/station[N].html`
2. Use your `CONTENT-PLAN.md` to fill in [PLACEHOLDER] content
3. Maintain HAP's first-person apprentice voice
4. Reference the `hap-voice` and `station-content` Skills

**For interactive demos**:

1. Copy `templates/demo-template.html` → `demos/[demo-name].html`
2. Use the `demo-builder` Skill for structure guidance
3. Implement JavaScript patterns documented in template
4. Test accessibility with `accessibility-check` Skill

**For easter eggs**:

1. Copy `templates/hybit-insights-template.json` → `data/hybit-insights.jsonc`
2. Define parameters for your topic
3. Write messages in HAP's voice
4. Test with `?hybit=[parameter]` in URLs

### Step 5: Validate with Skills

Before committing any code, run through these Skills:

- `hap-voice`: Validate HAP's first-person voice
- `accessibility-check`: Ensure WCAG 2.2 Level AA compliance
- `css-standards`: Verify all colors use hsl() format
- `security-audit`: Check easter egg whitelist validation
- `testing-framework`: Run audits with DevTools MCP or Lighthouse (target: 99+/100)

## Claude Skills reference

### When to use each Skill

**Before writing ANY code**:

- `css-standards`: Consult before adding any CSS colors

**While creating content**:

- `hap-voice`: Validate HAP's personality and tone
- `station-content`: Ensure station structure is complete
- `demo-builder`: Build interactive demonstrations

**Before committing**:

- `accessibility-check`: Verify WCAG compliance
- `security-audit`: Validate security patterns
- `testing-framework`: Run performance tests

### How to use Skills

Claude Code automatically loads Skills from `.claude/skills/`. To use a Skill:

1. Read the Skill's `SKILL.md` file
2. Follow the progressive validation steps
3. Complete all checklists
4. Use provided code patterns

## HAP's voice guidelines

**Critical**: HAP always speaks in first-person apprentice voice.

**Correct patterns**:

- ✅ "I learned from Prof. Teeters that..."
- ✅ "When I was practicing..."
- ✅ "This was tricky for me too..."
- ✅ "Prof. Teeters showed me..."

**Incorrect patterns**:

- ❌ "You should..." (too instructional)
- ❌ "This tutorial teaches..." (not personal)
- ❌ "Obviously, the answer is..." (not humble)
- ❌ Generic statements without attribution

**HAP's personality**:

- Enthusiastic but humble
- References Prof. Teeters as mentor
- Shares mistakes and learning moments
- Uses "I" and "me", not "you" or "we"
- Makes complex topics relatable

See `hap-voice` Skill for complete guidelines.

## Content conventions

### Heading capitalization

**HTML files** (educational content): Use **title case**

- ✅ "The Resolution Problem"
- ✅ "Why Typography Matters"

**Markdown files** (technical docs): Use **sentence case**

- ✅ "The resolution problem"
- ✅ "Why typography matters"

### Emoji usage

**HAP's signature emoji**: 🟠 (orange circle) for tips and insights

**Approved emoji** (good visibility on cream background):

- 🟠 HAP's signature - use as safe alternative
- 🔬 Science, research, HAP's lab context
- 📊 Data, metrics
- 🎯 Goals, targets
- 🎨 Design, colors
- 🚀 Performance
- 🌐 Web, browsers
- 📸 Images
- 🗂️ Organization, systems
- 🎡 Relationships, cycles
- ♿ Accessibility

**Never use** (poor visibility):

- ❌ 💡 ⚡ ⭐ ✨ (yellow on cream = invisible)
- ❌ 🤖 (use HAP images instead)

### Markdown standards

**From user's global rules**:

- Headers: Sentence case, single space after `#`
- Lists: Use `-` exclusively (never `*` or `+`)
- Code blocks: Always specify language (```css not```)
- Links: `[text](url)` with NO spaces
- Tables: Include header separator row

## CSS architecture

### Single source of truth

**All colors MUST be defined in `css/style.css` in the `:root` block** (lines 39-150+).

The CSS architecture includes:
- **Core color palette** (lines 40-50): Warm orange, peach, brown, teal, success/warning colors
- **WCAG AA accessible variants** (lines 52-64): Darker versions meeting 4.5:1 or 3:1 contrast ratios
- **Light background variants** (lines 66-76): Success, error, info, warning backgrounds
- **Code block theme** (lines 78-86): Dark mode colors for code examples
- **UI neutrals** (lines 88-94): Borders, muted text, hover states
- **Demo-specific palettes** (lines 104+): Scoped colors for individual interactive demos

**Use hsl() format exclusively**:

```css
/* ✅ CORRECT */
:root {
  --warm-orange: hsl(32, 76%, 63%);
  --peach-background: hsl(32, 35%, 88%);
}

/* ❌ WRONG - NEVER use hex or rgb */
:root {
  --warm-orange: #E8A557;  /* FORBIDDEN */
  --peach-background: rgb(232, 165, 87);  /* FORBIDDEN */
}
```

See `css-standards` Skill for complete rules and enforcement patterns.

### CRITICAL: clamp() formula requirement

**When you generate a clamp() expression, do NOT treat the middle value (the 'preferred' value) as just a fixed or arbitrary percentage like 5%. Instead, compute it as a fluid expression that describes the slope between the minimum and maximum size over a defined viewport or container width range.**

**The formula**:

```
preferred = BASE + (SLOPE × viewport-unit)

Where:
SLOPE = (max-size - min-size) / (max-viewport - min-viewport)
BASE = min-size - (SLOPE × min-viewport)
```

**For example**: Derive the slope using (max-size – min-size) ÷ (max-viewport-width – min-viewport-width) and express the preferred value as a unit like `vw`, `cqi`, or calc()-based combination (e.g., `2.5vw + 1rem`) rather than a plain `%`.

**Why this matters**: This ensures that the size scales logically and predictably between the min and max rather than "floating" unpredictably based on parent element size.

**In short: middle value = a scaling formula, not an arbitrary percentage.**

**Correct examples**:

```css
/* ✅ CORRECT - Computed slope formula */
padding: clamp(1rem, 0.5rem + 1vw, 3rem);
/* Base (0.5rem) + slope (1vw) scales predictably across viewport range */

margin-block: clamp(2rem, 1rem + 2.5vh, 6rem);
/* Viewport-relative scaling with computed slope */

gap: clamp(1rem, 0.5rem + 1.25vmax, 3rem);
/* Uses vmax for scaling with computed slope */

/* Container-relative spacing (Station 5) */
padding: clamp(1rem, 0.5rem + 2cqi, 3rem);
/* Container inline units with computed slope */
```

**Wrong examples**:

```css
/* ❌ WRONG - Arbitrary percentage */
padding: clamp(1rem, 5%, 3rem);
/* 5% is relative to parent size - unpredictable scaling! */

/* ❌ WRONG - Just viewport unit, no base */
padding: clamp(1rem, 2vw, 3rem);
/* Missing base calculation - doesn't scale correctly */

/* ❌ WRONG - Random percentage */
gap: clamp(0.5rem, 3%, 2rem);
/* Parent-relative % doesn't create predictable slope */
```

**Practical approach for common viewport range (320px → 1920px)**:

```css
/* Spacing scale with computed slopes */
:root {
  --space-xs: clamp(0.5rem, 0.4rem + 0.5vw, 1rem);
  --space-sm: clamp(1rem, 0.75rem + 0.625vw, 1.5rem);
  --space-md: clamp(1.5rem, 1rem + 1.25vw, 2.5rem);
  --space-lg: clamp(2rem, 1.25rem + 1.875vw, 4rem);
  --space-xl: clamp(3rem, 1.5rem + 3.75vw, 6rem);
}
```

**Station-by-station usage**:
- **Station 1**: Preview the pattern without teaching the math
- **Station 3**: Full teaching of formula with HAP working through calculation
- **Station 5**: Same pattern applied to container units (`cqi`, `cqb`)
- **All stations**: Always use computed slope formulas, never arbitrary percentages

See `reports/claude-code-directive.md` for complete explanation and examples.

### HAP component library

Reusable HAP-branded components:

1. **HAP Note Callout** (`.hap-note-callout`) - Tips and insights
2. **Insight Cards** (`.insight-card`) - Key learning points
3. **Analysis Grid** (`.analysis-grid`) - Multiple related points
4. **HAP Info Grid** (`.hap-info-grid`) - Structured lists
5. **Navigation Patterns** (`.page-navigation`) - Top/bottom nav
6. **Footer** (`.footer`) - Copyright and legal info
7. **Interactive Demos** (`.demo-container`) - Tools and calculators

See `station-content` and `demo-builder` Skills for usage patterns.

## JavaScript architecture

**Minimal JavaScript philosophy**: Only ~189 lines total for easter egg system.

**Easter egg system** (`js/easter-egg.js`):

- Loads content from `data/hybit-insights.jsonc`
- Whitelist-based parameter validation (XSS-safe)
- Native `<dialog>` element for modals
- URL parameter pattern: `?hybit=detail`, `?hybit=formats`, etc.
- See `data/README.md` for complete documentation

**Security features**:

- No user input in HTML
- Pre-defined messages only
- Whitelist validation
- Safe HTML tags: `<code>`, `<strong>`, `<em>` only

See `security-audit` Skill for validation patterns.

## Accessibility requirements

**WCAG AA compliance** is mandatory for all pages:

- Text contrast: 4.5:1 minimum for normal text
- Large text contrast: 3:1 minimum (≥18px or ≥14px bold)
- Color never used as only indicator (always pair with icons/text)
- Alt text for all images (descriptive, not "image of")
- Semantic HTML (`<header>`, `<nav>`, `<main>`, `<article>`)
- Skip link for keyboard users
- ARIA labels on navigation landmarks

See `accessibility-check` Skill for complete checklist.

## Performance requirements

**Lighthouse targets** (all stations must meet):

- Performance: 99-100/100
- Accessibility: 100/100
- Best Practices: 100/100
- SEO: 100/100

**Optimization checklist**:

- [ ] All images have explicit width/height
- [ ] Below-fold images use `loading="lazy"`
- [ ] LCP image has `fetchpriority="high"`
- [ ] Scripts use `defer` attribute
- [ ] CSS uses custom properties (not repeated values)
- [ ] No layout shift (CLS = 0)

See `testing-framework` Skill for validation steps.

## Legal and licensing

**Multi-license approach**:

- **Code**: MIT License (open source)
- **HAP™ Character**: Proprietary (Prof. Teeters)
- **Educational Content**: Proprietary (academic use allowed)

**Required copyright notices**:

HTML footer:

```html
<p>HAP™ Educational Content © 2025 Cynthia Teeters. All rights reserved.</p>
<p>HyBit A. ProtoBot™ (HAP™) character and the apprentice learning methodology are proprietary educational innovations.</p>
```

HTML comment (end of file):

```html
<!--
HAP™ Educational Content © 2025 Cynthia Teeters. All rights reserved.
HyBit A. ProtoBot™ (HAP™) character and the apprentice learning methodology are proprietary educational innovations.
Character concept, teaching methodology, and all written content created by Prof. Cynthia Teeters.
Visual elements created with AI assistance.
-->
```

**Always use**:

- HAP™ (with trademark symbol)
- HyBit A. ProtoBot™ (with trademark symbol)

## Common pitfalls to avoid

1. **Don't use Write tool on existing files** - Use Edit instead
2. **Don't copy from existing stations** - CRITICAL: Always use `templates/station-template.html` as starting point for new stations, never copy from `station1.html`, `station2.html`, etc. This ensures consistent structure and CUSTOMIZE comments.
3. **Don't break HAP's voice** - First-person, humble, references Prof. Teeters
4. **Don't skip performance testing** - Use DevTools MCP or Lighthouse to maintain 99+ scores
5. **Don't use hex/rgb colors** - Use hsl() format exclusively
6. **Don't use arbitrary percentages in clamp()** - CRITICAL: Use computed slope formulas (`base + slope × vw`), not arbitrary `%` like `clamp(1rem, 5%, 3rem)`. See "CRITICAL: clamp() formula requirement" section above.
7. **Don't create new files unnecessarily** - Use templates provided
8. **Don't forget width/height on images** - Causes layout shift
9. **Don't use color alone** - Pair with icons/text for accessibility
10. **Don't commit without testing locally** - Ensure JSON loads, images display
11. **Don't skip Skills validation** - Each Skill prevents specific problems
12. **Don't use title case in markdown** - Sentence case for `.md` files

## Project-specific resources

### Planning documents location

**Current intrinsic layouts curriculum planning is in `reports/modern-css-layout-mastery/`:**

- `master-outline.md` - Overall curriculum structure
- `intrinsic-layout-curriculum-plan-v3.md` - Latest detailed curriculum plan
- `implementation-plan-station1.md` - Station 1 implementation details
- `station6-directive.md` - Station 6 requirements
- `ai-drift-prevention-research.md` - Quality control strategies
- `chatgpt-review.md` - External validation feedback

**Always consult these documents before creating stations or demos for this learning lab.**

### Reports directory usage

The `reports/` directory is for:
- Curriculum planning documents
- Research and analysis
- Implementation strategies
- External reviews and feedback
- Progress tracking

**Following user's global rules**: When asked to create reports, put them in the `reports/` folder and make NO changes to code.

## Getting help

**For this intrinsic layouts learning lab**:

- Consult planning documents in `reports/modern-css-layout-mastery/` for curriculum structure
- Use templates to create stations (`templates/station-template.html`)
- Run relevant Claude Skills for validation
- Test locally with `live-server --port=3000` before deploying

**For instructors customizing the template for NEW topics**:

- Start with `templates/curriculum-plan-template.md` - fill in all 6 stations first
- Use provided templates (don't create from scratch)
- Consult Skills before each phase of work
- Test with DevTools MCP or `npm run lh:ci` before deployment

**For developers**:

- This is a template - fork and customize freely (MIT license)
- HAP character usage requires permission (see licensing)
- Maintain educational content license
- All Skills are documented with examples

## Template customization checklist

Before starting your new learning lab:

- [ ] Create new repo from this GitHub template or copy directory to new location
- [ ] Rename directory to your learning lab topic
- [ ] Fill out `templates/curriculum-plan-template.md` completely
- [ ] Verify all 6 station topics are defined
- [ ] Write HAP's struggles and learning moments
- [ ] Plan 2-3 interactive demos per station
- [ ] Define easter egg parameters for your topic
- [ ] Set up local development server
- [ ] Verify Claude Code can access `.claude/skills/` directory

After customization:

- [ ] All stations use hsl() colors (validated with `css-standards` Skill)
- [ ] All content uses HAP's first-person voice (validated with `hap-voice` Skill)
- [ ] All pages meet WCAG AA (validated with `accessibility-check` Skill)
- [ ] All pages score 99+ on performance tests (validated with `testing-framework` Skill using DevTools MCP)
- [ ] Easter egg system tested on all pages
- [ ] Local testing completed with live-server
- [ ] Copyright notices included in all HTML files

---

**Remember**: This is a teaching tool. Clarity, accessibility, and HAP's friendly voice are more important than technical complexity. Keep it simple, keep it accessible, keep it HAP!
