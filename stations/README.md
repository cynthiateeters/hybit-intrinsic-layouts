# Stations directory

This directory will contain your 6 learning station HTML files.

## Getting started

1. **Copy the station template** for each station you want to create:
   ```bash
   cp ../templates/station-template.html station1.html
   cp ../templates/station-template.html station2.html
   cp ../templates/station-template.html station3.html
   cp ../templates/station-template.html station4.html
   cp ../templates/station-template.html station5.html
   cp ../templates/station-template.html station6.html
   ```

2. **Fill in the [PLACEHOLDER] content** using your `CONTENT-PLAN.md`:
   - Replace all `[PLACEHOLDER]` markers with your actual content
   - Maintain HAP's first-person apprentice voice
   - Use the `hap-voice` Skill to validate tone and personality
   - Use the `station-content` Skill to ensure complete structure

3. **Validate each station** before moving to the next:
   - Run `accessibility-check` Skill for WCAG compliance
   - Run `css-standards` Skill to verify color format
   - Test locally with live-server
   - Check for console errors

## File naming convention

**Required naming**:
- `station1.html` through `station6.html` (lowercase, no spaces)

**Why this matters**: The `lighthouserc.json` configuration expects these exact filenames for automated testing.

## Station structure

Each station should include:
- Semantic HTML (`<header>`, `<main>`, `<nav>`, `<footer>`)
- HAP's first-person narrative throughout
- Code examples (before/after or good/bad)
- At least one HAP callout or note
- Navigation links to other stations
- Easter egg script reference

## Best practices

- **Always start with your content plan**: Don't write stations without completing `templates/curriculum-plan-template.md` first
- **Work on one station at a time**: Complete and validate each before moving forward
- **Test frequently**: Use live-server to preview changes immediately
- **Consult Skills early**: Don't wait until the end to validate

## Need help?

- Read the complete station template: `../templates/station-template.html`
- Review HAP's voice guidelines: `../.claude/skills/hap-voice/SKILL.md`
- Check content patterns: `../.claude/skills/station-content/SKILL.md`
- See a completed example: Look at the `hybit-colors` learning lab

---

**Ready to start?** Copy `../templates/station-template.html` to `station1.html` and begin customizing!
