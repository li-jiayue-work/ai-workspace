Space is the most underused design tool. Find the layout's actual problem (monotone spacing, weak hierarchy, identical card grids, the centered-stack default) and fix the structure, not the surface.

---

## Register

Brand: asymmetric compositions, fluid spacing with `clamp()`, intentional grid-breaking for emphasis. Rhythm through contrast: tight groupings paired with generous separations.

Product: predictable grids, consistent densities, familiar navigation patterns. Responsive behavior is structural (collapse sidebar, responsive table), not fluid typography. Consistency IS an affordance.

---

## Assess Current Layout

1. **Spacing**:
   - Is spacing consistent or arbitrary? (Random padding/margin values)
   - Is all spacing the same? (Equal padding everywhere = no rhythm)
   - Are related elements grouped tightly, with generous space between groups?

2. **Visual hierarchy**:
   - Apply the squint test: blur your eyes. Can you still identify the most important element and clear groupings?
   - Does whitespace guide the eye to what matters?

3. **Grid & structure**:
   - Is there a clear underlying structure, or does the layout feel random?
   - Are identical card grids used everywhere? (Icon + heading + text, repeated endlessly)
   - Is everything centered? (Left-aligned with asymmetric layouts feels more designed)

4. **Rhythm & variety**:
   - Does the layout have visual rhythm? (Alternating tight/generous spacing)
   - Is every section structured the same way? (Monotonous repetition)
   - Are there intentional moments of surprise or emphasis?

5. **Density**:
   - Is the layout too cramped? (Not enough breathing room)
   - Is the layout too sparse? (Excessive whitespace without purpose)
   - Does density match the content type?

## Plan Layout Improvements

Consult the [spatial design reference](spatial-design.md) for detailed guidance on grids, rhythm, and container queries.

- **Spacing system**: Use a consistent scale (Tailwind's, rem-based tokens, or custom system)
- **Hierarchy strategy**: How will space communicate importance?
- **Layout approach**: Flex for 1D, Grid for 2D, named areas for complex page layouts
- **Rhythm**: Where should spacing be tight vs generous?

## Improve Layout Systematically

### Establish a Spacing System

- Use a consistent spacing scale. What matters is that values come from a defined set, not arbitrary numbers.
- Name tokens semantically: `--space-xs` through `--space-xl`
- Use `gap` for sibling spacing instead of margins; eliminates margin collapse hacks
- Apply `clamp()` for fluid spacing that breathes on larger screens

### Create Visual Rhythm

- **Tight grouping** for related elements (8-12px between siblings)
- **Generous separation** between distinct sections (48-96px)
- **Varied spacing** within sections (not every row needs the same gap)
- **Asymmetric compositions**: break the predictable centered-content pattern when it makes sense

### Choose the Right Layout Tool

- **Use Flexbox for 1D layouts**: Rows of items, nav bars, button groups, card contents
- **Use Grid for 2D layouts**: Page-level structure, dashboards, data-dense interfaces
- **Don't default to Grid** when Flexbox with `flex-wrap` would be simpler
- Use `repeat(auto-fit, minmax(280px, 1fr))` for responsive grids without breakpoints

### Break Card Grid Monotony

- Don't default to card grids for everything; spacing and alignment create visual grouping naturally
- Use cards only when content is truly distinct and actionable. Never nest cards inside cards
- Vary card sizes, span columns, or mix cards with non-card content

### Strengthen Visual Hierarchy

- Use the fewest dimensions needed. Space alone can be enough; generous whitespace around an element draws the eye.
- Be aware of reading flow: in LTR languages, the eye naturally scans top-left to bottom-right
- Create clear content groupings through proximity and separation

### Manage Depth & Elevation

- Create a semantic z-index scale (dropdown -> sticky -> modal-backdrop -> modal -> toast -> tooltip)
- Build a consistent shadow scale (sm -> md -> lg -> xl); shadows should be subtle
- Use elevation to reinforce hierarchy, not as decoration

### Optical Adjustments

- If an icon looks visually off-center despite being geometrically centered, nudge it. Only if you're confident it actually looks wrong.

**NEVER**:
- Use arbitrary spacing values outside your scale
- Make all spacing equal (variety creates hierarchy)
- Wrap everything in cards (not everything needs a container)
- Nest cards inside cards (use spacing and dividers for hierarchy)
- Use identical card grids everywhere (icon + heading + text, repeated)
- Center everything (left-aligned with asymmetry feels more designed)
- Default to the hero metric layout (big number, small label, stats, gradient) as a template
- Use arbitrary z-index values (999, 9999); build a semantic scale

## Live-mode signature params

Each variant MUST declare a `density` param:

```json
{"id":"density","kind":"range","min":0.6,"max":1.4,"step":0.05,"default":1,"label":"Density"}
```

For variants whose topology genuinely changes:

```json
{"id":"structure","kind":"steps","default":"grid","label":"Structure","options":[
  {"value":"stacked","label":"Stacked"},
  {"value":"grid","label":"Grid"},
  {"value":"bento","label":"Bento"}
]}
```

See `reference/live.md` for the full params contract.
