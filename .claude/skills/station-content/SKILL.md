# Station content structure

## Description

Complete station HTML structure template for HAP Learning Labs. Validates that all 6 required sections are present with correct HAP components, heading hierarchy, and accessibility features. Prevents structural inconsistencies found across stations in the Colors project.

## When to use this Skill

**ALWAYS** use this Skill:
- When creating a new station page
- When editing existing station structure
- Before committing station HTML
- When reviewing station completeness

## Progressive validation steps

### Step 1: Station structure validation (6 required sections)

Every station MUST have these 6 sections in order:

1. **Header with HAP avatar and title**
2. **Top navigation** (back to hub + position indicator)
3. **"What You'll Learn" section** (EXACTLY 3 insight cards)
4. **Main content sections** (2-4 topic sections)
5. **Bottom navigation** (previous/hub/next links)
6. **Footer** (copyright and legal notices)

**Validation checklist**:
- [ ] All 6 sections present in correct order
- [ ] No missing sections
- [ ] No extra/custom sections outside this structure

### Step 2: Component usage validation

Check each section uses correct HAP components from style.css.

#### Section 1: Header with HAP avatar and title

**Required HTML structure**:
```html
<body>
    <!-- Skip link MUST be first -->
    <a href="#main-content" class="skip-link">Skip to main content</a>

    <header class="header">
        <div class="header-content">
            <!-- HAP avatar and title -->
            <div class="hybit-welcome">
                <div class="hybit-avatar">
                    <img src="[CLOUDINARY_URL]/hap-laptop_xiewar.jpg"
                         alt="Illustration of HAP (HyBit A. ProtoBot) studying on his laptop"
                         width="200"
                         height="200"
                         decoding="async"
                         fetchpriority="high">
                </div>
                <div>
                    <h1>HAP's Learning Lab: [STATION_TITLE]</h1>
                    <p class="subtitle">[Subtitle describing station focus]</p>
                </div>
            </div>

            <!-- HAP's introduction (SINGLE <p> tag only!) -->
            <div class="intro-box">
                <p><strong>Welcome to Station [N]!</strong> [HAP's personal story about learning this topic from Prof. Teeters...] 🟠</p>
            </div>
        </div>
    </header>
</body>
```

**Validation checklist**:
- [ ] Skip link is FIRST element in `<body>`
- [ ] HAP avatar uses `fetchpriority="high"` (LCP image)
- [ ] Title follows pattern: "HAP's Learning Lab: [Topic]"
- [ ] Intro box contains EXACTLY one `<p>` tag
- [ ] Introduction uses HAP's apprentice voice
- [ ] Introduction ends with 🟠 emoji

#### Section 2: Top navigation

**Required HTML structure**:
```html
<nav aria-label="Page navigation" class="page-navigation top-nav">
    <a href="../index.html" class="nav-link hub-link">🏠 Back to Hub</a>
    <div class="page-position" data-page="[N]">Station [N] of 6</div>
</nav>
```

**Validation checklist**:
- [ ] `aria-label="Page navigation"` present
- [ ] Link to hub (`../index.html`)
- [ ] Station number shown (N of 6)
- [ ] Uses `page-navigation` and `top-nav` classes

#### Section 3: "What You'll Learn" section

**Required HTML structure** (EXACTLY 3 insight cards):
```html
<main id="main-content" class="content-container">
    <section class="content-section">
        <h2 class="section-heading-centered">What You'll Learn at This Station</h2>

        <div class="overview-grid mt-2">
            <!-- Insight Card 1 -->
            <div class="insight-card">
                <h3><span class="insight-icon">[EMOJI]</span> [Learning Point 1]</h3>
                <p class="stat-large">[Key Metric/Statistic]</p>
                <p><strong>[Emphasis Statement]</strong></p>
                <p>[HAP's first-person explanation of what he learned...]</p>
            </div>

            <!-- Insight Card 2 -->
            <div class="insight-card">
                <h3><span class="insight-icon">[EMOJI]</span> [Learning Point 2]</h3>
                <p class="stat-large stat-teal">[Key Metric/Statistic]</p>
                <p><strong>[Emphasis Statement]</strong></p>
                <p>[HAP's first-person explanation...]</p>
            </div>

            <!-- Insight Card 3 -->
            <div class="insight-card">
                <h3><span class="insight-icon">[EMOJI]</span> [Learning Point 3]</h3>
                <p class="stat-large stat-brown">[Key Metric/Statistic]</p>
                <p><strong>[Emphasis Statement]</strong></p>
                <p>[HAP's first-person explanation...]</p>
            </div>
        </div>
    </section>
</main>
```

**Validation checklist**:
- [ ] `<main id="main-content">` present (for skip link)
- [ ] Section heading: "What You'll Learn at This Station"
- [ ] EXACTLY 3 insight cards (no more, no less)
- [ ] Each card has: icon emoji, heading, stat, emphasis, explanation
- [ ] Stat variations: `stat-large`, `stat-teal`, `stat-brown`
- [ ] All explanations use HAP's first-person voice

#### Section 4: Main content sections

**Common content patterns**:

**Pattern A: Topic section with code example**:
```html
<section class="content-section">
    <div class="topic-section">
        <h2>[Topic Heading]</h2>
        <p class="mb-2">[HAP's introduction to the topic...]</p>

        <div class="warning-box mt-2">
            <h3>🟠 HAP's Old Way vs. What I Learned</h3>
            <p><strong class="text-error">❌ WRONG: [What HAP did initially]</strong></p>
            <pre><code class="language-[css/html/javascript]">[Bad code example]</code></pre>

            <p class="mt-1"><strong class="text-success">✅ RIGHT: What I Learned</strong></p>
            <pre><code class="language-[css/html/javascript]">[Good code example]</code></pre>

            <p class="mt-1">[HAP's explanation why second is better]</p>
        </div>
    </div>
</section>
```

**Pattern B: HAP note callout**:
```html
<div class="hap-note-callout">
    <img src="[CLOUDINARY_URL]/hap-[expression].jpg"
         alt="Illustration of HAP [emotional state/activity]"
         width="150"
         height="150"
         class="hap-note-image"
         decoding="async"
         loading="lazy">
    <div class="hap-note-content">
        <h3>[HAP's Discovery/Tip/Mistake]:</h3>
        <p>[First-person narrative about specific experience with Prof. Teeters...]</p>
    </div>
</div>
```

**Pattern C: Code example with prompt box**:
```html
<div class="prompt-box">
    <div class="prompt-label">[Description of code]:</div>
    <pre><code class="language-[css/html/javascript]">[Code example]</code></pre>
    <p class="code-comment mt-1">[HAP's explanation of what the code does]</p>
</div>
```

**Pattern D: Quick reference tips**:
```html
<section class="content-section">
    <h2 class="section-heading-centered">Quick Reference</h2>
    <div class="tips-grid mt-2">
        <div class="tip-card">
            <div class="tip-number">1</div>
            <div>
                <h3>[Tip Title]</h3>
                <p>[Concise tip description]</p>
            </div>
        </div>
        <!-- Repeat for 6-8 tips -->
    </div>
</section>
```

**Validation checklist**:
- [ ] 2-4 main content sections (not more than 4)
- [ ] Each section uses `content-section` class
- [ ] Headings follow hierarchy: h2 → h3 (no skipped levels)
- [ ] Code examples use Prism.js syntax highlighting
- [ ] HAP note callouts use first-person voice
- [ ] Images below fold have `loading="lazy"`

#### Section 5: Bottom navigation

**Required HTML structure**:
```html
<nav aria-label="Station pagination" class="page-navigation bottom-nav">
    <a href="station[N-1].html" class="nav-link prev-link">← Previous: Station [N-1] - [Title]</a>
    <a href="../index.html" class="nav-link hub-link">🏠 Hub</a>
    <a href="station[N+1].html" class="nav-link next-link">Next: Station [N+1] - [Title] →</a>
</nav>
```

**Special cases**:
- Station 1: No previous link (only hub + next)
- Station 6: No next link (only previous + hub)

**Validation checklist**:
- [ ] `aria-label="Station pagination"` present
- [ ] Three links: previous, hub, next (or appropriate for station 1/6)
- [ ] Descriptive link text (includes station number and title)
- [ ] Uses `page-navigation` and `bottom-nav` classes

#### Section 6: Footer

**Required HTML structure**:
```html
<footer class="footer">
    <p><strong>HAP's Learning Lab</strong> | An AI-Enhanced Educational Experience by Prof. Cynthia Teeters</p>
    <p class="footer-reminder">
        [HAP's one-sentence reminder about this station's key lesson] 🟠 — HAP
    </p>
    <div class="footer-copyright">
        <img src="[CLOUDINARY_URL]/HAP-learner_dvehmt.jpg"
             alt="Illustration of HAP the apprentice learner with his study book and tools"
             class="footer-hybit"
             width="80"
             height="80"
             decoding="async"
             loading="lazy">
        <div>
            <p>HAP&trade; Educational Content &copy; 2025 Cynthia Teeters. All rights reserved.</p>
            <p>HyBit A. ProtoBot&trade; (HAP&trade;) character and the apprentice learning methodology are proprietary educational innovations.</p>
            <p>Character concept, teaching methodology, and all written content created by Prof. Cynthia Teeters. Visual elements created with AI assistance.</p>
        </div>
    </div>
</footer>
```

**Validation checklist**:
- [ ] HAP's reminder customized to station topic
- [ ] Trademark symbols (™) present for HAP and HyBit A. ProtoBot
- [ ] Copyright year correct (2025)
- [ ] Footer HAP image has `loading="lazy"`

### Step 3: Content length validation

Check content is appropriate length (not too sparse, not overwhelming).

**Guidelines per station**:
- Total HTML: 400-600 lines (station3.html = 514 lines is ideal)
- Main content sections: 2-4 sections
- Code examples: 3-5 per station
- HAP note callouts: 2-4 per station
- Quick reference tips: 6-8 tips (if included)

**Too short** (< 400 lines):
- Likely missing content
- May not cover topic adequately
- Check for missing sections

**Too long** (> 600 lines):
- May be overwhelming for students
- Consider splitting into multiple stations
- Remove redundant examples

### Step 4: Heading hierarchy validation

Check heading levels follow semantic structure.

**Required hierarchy**:
```
h1 (page title) - EXACTLY ONE per page
└── h2 (main sections) - "What You'll Learn", topic headings
    └── h3 (subsections) - Insight cards, HAP notes, code examples
```

**Validation**:
- [ ] ONE `<h1>` tag (station title)
- [ ] `<h2>` for main sections (3-6 h2 tags typical)
- [ ] `<h3>` for subsections and components
- [ ] NO skipped levels (no h1 → h3 without h2)
- [ ] NO empty headings (`<h3></h3>`)

### Step 5: HAP component library reference

**Available HAP components** (from style.css):

| Component | Class | Use case |
|-----------|-------|----------|
| Insight cards | `.insight-card` | "What You'll Learn" section (3 cards) |
| HAP note callout | `.hap-note-callout` | HAP's personal insights/tips |
| Warning box | `.warning-box` | Wrong vs. Right code examples |
| Prompt box | `.prompt-box` | Code examples with explanation |
| Tip cards | `.tip-card` | Quick reference tips (numbered) |
| Topic section | `.topic-section` | Main content wrapper |
| Interactive demo | `.interactive-demo` | Links to demo files |

**When to use each**:
- **Insight cards**: ONLY in "What You'll Learn" section (EXACTLY 3)
- **HAP note callout**: For personal stories, Prof. Teeters insights, mistakes shared
- **Warning box**: For code comparisons (wrong vs. right)
- **Prompt box**: For correct code examples with explanation
- **Tip cards**: For quick reference lists (6-8 tips)
- **Interactive demo**: When station has associated demo file

### Step 6: Review checklist

Before committing station HTML, verify:

**Structure**:
- [ ] All 6 required sections present in order
- [ ] Skip link is first element in body
- [ ] Main has `id="main-content"`
- [ ] Navigation has correct `aria-label`

**Content**:
- [ ] HAP's voice in all narrative sections
- [ ] Code examples use Prism.js syntax highlighting
- [ ] 2-4 main content sections (appropriate length)
- [ ] Quick reference section (if topic warrants it)

**Images**:
- [ ] HAP avatar has `fetchpriority="high"`
- [ ] All other images have `loading="lazy"`
- [ ] All images have `width` and `height`
- [ ] All images have descriptive `alt` text

**Accessibility**:
- [ ] Skip link present
- [ ] Heading hierarchy correct (no skipped levels)
- [ ] Navigation landmarks have `aria-label`
- [ ] No empty headings

**Footer**:
- [ ] HAP's reminder customized to station
- [ ] Trademark symbols present
- [ ] Copyright year correct

## Common mistakes

From Colors project station analysis:

1. **Wrong number of insight cards**
   - Issue: 2 cards or 4 cards instead of exactly 3
   - Fix: Always use exactly 3 insight cards in "What You'll Learn"

2. **Multiple paragraphs in intro box**
   - Issue: Using multiple `<p>` tags in intro box
   - Fix: Use EXACTLY one `<p>` tag (combine content if needed)

3. **Missing bottom navigation**
   - Issue: Stations without prev/next links
   - Fix: Always include bottom navigation (except special cases for station 1/6)

4. **Inconsistent HAP voice**
   - Issue: Switching from first-person to instructional mid-station
   - Fix: Use hap-voice Skill to validate all content

5. **Wrong Prism language**
   - Issue: `<code class="language-markup">` instead of `language-html`
   - Fix: Use correct language: `language-css`, `language-html`, `language-javascript`

6. **Missing aria-labels**
   - Issue: Navigation without descriptive labels
   - Fix: Top nav = "Page navigation", Bottom nav = "Station pagination"

7. **Empty headings**
   - Issue: `<h3></h3>` tags with no content
   - Fix: Remove empty headings or add content

## Example station structure

**Minimal complete station** (400 lines):
```html
<!DOCTYPE html>
<html lang="en">
<head>
    [Standard meta tags, CSS links, favicons]
</head>
<body>
    <a href="#main-content" class="skip-link">Skip to main content</a>

    <header class="header">
        [HAP avatar + title + intro box]
    </header>

    <nav aria-label="Page navigation" class="page-navigation top-nav">
        [Back to Hub + Station N of 6]
    </nav>

    <main id="main-content" class="content-container">
        <section class="content-section">
            <h2 class="section-heading-centered">What You'll Learn at This Station</h2>
            <div class="overview-grid mt-2">
                [3 insight cards]
            </div>
        </section>

        <section class="content-section">
            [Main topic 1 with code examples]
        </section>

        <section class="content-section">
            [Main topic 2 with HAP notes]
        </section>

        <section class="content-section">
            [Quick reference tips]
        </section>
    </main>

    <nav aria-label="Station pagination" class="page-navigation bottom-nav">
        [Previous + Hub + Next]
    </nav>

    <footer class="footer">
        [HAP reminder + copyright]
    </footer>

    <script src="../js/easter-egg.js"></script>
    [Prism.js scripts if code examples present]
</body>
</html>
```

## Notes

- Station structure is non-negotiable — all 6 sections required
- EXACTLY 3 insight cards (established pattern across all HAP labs)
- ONE paragraph in intro box (keeps it concise and focused)
- HAP's voice must be consistent throughout
- Code examples should be copy-paste ready (tested and working)
- Quick reference section is optional but recommended

---

**Skill version**: 1.0
**Last updated**: October 2025
**Source**: station3.html complete structure analysis + style guide component library
