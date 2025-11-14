# Demos directory

This directory will contain your interactive demo HTML files.

## What are demos?

Interactive demonstrations that let students experiment with concepts hands-on. Examples:
- Calculators (contrast ratios, font sizes, grid systems)
- Converters (color formats, units, values)
- Comparisons (before/after, good/bad examples)
- Visualizers (animations, transformations, effects)
- Generators (palettes, layouts, code snippets)

## Getting started

1. **Copy the demo template** for each interactive tool you want to create:
   ```bash
   cp ../templates/demo-template.html contrast-checker.html
   cp ../templates/demo-template.html format-converter.html
   ```

2. **Customize the demo**:
   - Replace all `[PLACEHOLDER]` markers with your demo's functionality
   - Add interactive controls (sliders, inputs, buttons)
   - Implement JavaScript for real-time updates
   - Display generated code or results
   - Add copy-to-clipboard functionality

3. **Link from stations**:
   - Reference demos from station pages
   - Use consistent linking patterns
   - Test all links locally

## File naming convention

**Recommended naming**:
- Use kebab-case: `contrast-checker.html`, `color-converter.html`
- Be descriptive: Name reflects what the demo does
- Keep it short: Avoid overly long filenames

**Examples from hybit-colors**:
- `contrast-fixer.html` - Tool to fix color contrast issues
- `gradient-builder.html` - Visual gradient generator
- `dark-mode-demo.html` - Dark mode implementation example

## Demo structure

Each demo should include:
- Clear instructions on how to use it
- Interactive controls (inputs, sliders, buttons)
- Real-time output or preview
- Generated code display (if applicable)
- Copy button for generated code
- HAP's tips about the concept being demonstrated

## Best practices

### Accessibility
- All interactive elements must be keyboard accessible
- Use proper ARIA labels on controls
- Ensure sufficient color contrast
- Test with `accessibility-check` Skill

### Performance
- Keep JavaScript minimal and focused
- Avoid external dependencies when possible
- Test with Playwright MCP or Lighthouse
- Ensure 99+ performance score

### Code quality
- Use semantic HTML (`<label>`, `<fieldset>`, `<output>`)
- Implement input validation
- Provide helpful error messages
- Show generated code in `<pre><code>` blocks

### User experience
- Provide clear instructions
- Show examples or presets
- Update preview in real-time
- Include reset/clear functionality

## Testing demos

Use the `testing-framework` Skill patterns:

**Visual testing** (Playwright MCP):
```
Test the [demo-name].html at localhost:5500:
1. Take screenshot of initial state
2. Interact with controls (click, drag, type)
3. Verify output updates correctly
4. Test copy button functionality
5. Take screenshot of final state
```

**Accessibility testing**:
- Run accessibility audit with Playwright MCP or Lighthouse
- Test keyboard navigation (Tab through all controls)
- Verify all inputs have labels
- Check color contrast on all text

## Common demo patterns

### Pattern 1: Calculator/Converter
- Input fields for values
- Calculation logic in JavaScript
- Display result in real-time
- Show formula or explanation

### Pattern 2: Visual builder
- Interactive controls (sliders, color pickers)
- Live preview of result
- Generated code display
- Copy button

### Pattern 3: Comparison tool
- Side-by-side examples
- Toggle between good/bad
- Highlight differences
- Explain why one is better

## Need help?

- Read the complete demo template: `../templates/demo-template.html`
- Review demo patterns: `../.claude/skills/demo-builder/SKILL.md`
- Check testing approaches: `../.claude/skills/testing-framework/SKILL.md`
- See completed examples: Look at demos in the `hybit-colors` learning lab

---

**Ready to build?** Copy `../templates/demo-template.html` to your first demo file and start customizing!
