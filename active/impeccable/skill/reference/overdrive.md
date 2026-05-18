Start your response with:

```
------------ OVERDRIVE -------------
》》》 Entering overdrive mode...
```

Push an interface past conventional limits. This isn't just about visual effects. It's about using the full power of the browser to make any part of an interface feel extraordinary: a table that handles a million rows, a dialog that morphs from its trigger, a form that validates in real-time with streaming feedback, a page transition that feels cinematic.

**EXTRA IMPORTANT FOR THIS COMMAND**: Context determines what "extraordinary" means. A particle system on a creative portfolio is impressive. The same particle system on a settings page is embarrassing. But a settings page with instant optimistic saves and animated state transitions? That's extraordinary too. Understand the project's personality and goals before deciding what's appropriate.

### Propose Before Building

1. **Think through 2-3 different directions**: consider different techniques, levels of ambition, and aesthetic approaches. For each direction, briefly describe what the result would look and feel like.
2. **Ask the user directly to clarify** to present these directions and get the user's pick before writing any code. Explain trade-offs (browser support, performance cost, complexity).
3. Only proceed with the direction the user confirms.

### Iterate with Browser Automation

Technically ambitious effects almost never work on the first try. You MUST actively use browser automation tools to preview your work, visually verify the result, and iterate.

---

## Assess What "Extraordinary" Means Here

### For visual/marketing surfaces
Pages, hero sections, landing pages, portfolios: the "wow" is often sensory: a scroll-driven reveal, a shader background, a cinematic page transition, generative art.

### For functional UI
Tables, forms, dialogs, navigation: the "wow" is in how it FEELS: a dialog that morphs from its trigger via View Transitions, a data table that renders 100k rows at 60fps via virtual scrolling, a form with streaming validation.

### For performance-critical UI
The "wow" is invisible but felt: a search that filters 50k items without a flicker, a complex form that never blocks the main thread.

### For data-heavy interfaces
Charts and dashboards: GPU-accelerated rendering via Canvas/WebGL for massive datasets, animated transitions between data states.

## The Toolkit

### Make transitions feel cinematic
- **View Transitions API** (same-document: all browsers; cross-document: no Firefox): shared element morphing between states
- **`@starting-style`** (all browsers): animate elements from `display: none` to visible with CSS only
- **Spring physics**: natural motion with mass, tension, and damping. Libraries: motion (formerly Framer Motion), GSAP

### Tie animation to scroll position
- **Scroll-driven animations** (`animation-timeline: scroll()`): CSS-only, no JS. (Chrome/Edge/Safari; Firefox: flag only; always provide a static fallback)

### Render beyond CSS
- **WebGL** (all browsers): shader effects, post-processing, particle systems. Libraries: Three.js, OGL, regl
- **WebGPU** (Chrome/Edge; Safari partial; Firefox: flag only): next-gen GPU compute. Always fall back to WebGL2
- **Canvas 2D / OffscreenCanvas**: custom rendering, pixel manipulation, off-main-thread rendering
- **SVG filter chains**: displacement maps, turbulence, morphology for organic distortion effects

### Make data feel alive
- **Virtual scrolling**: render only visible rows. TanStack Virtual for complex cases
- **GPU-accelerated charts**: Canvas or WebGL for datasets too large for SVG/DOM
- **Animated data transitions**: morph between chart states with D3's `transition()` or View Transitions

### Push performance boundaries
- **Web Workers**: move computation off the main thread
- **OffscreenCanvas**: render in a Worker thread
- **WASM**: near-native performance for computation-heavy features

## Implement with Discipline

### Progressive enhancement is non-negotiable

```css
@supports (animation-timeline: scroll()) {
  .hero { animation-timeline: scroll(); }
}
```

### Performance rules

- Target 60fps. If dropping below 50, simplify.
- Respect `prefers-reduced-motion`, always. Provide a beautiful static alternative.
- Lazy-initialize heavy resources only when near viewport.
- Pause off-screen rendering. Kill what you can't see.
- Test on real mid-range devices, not just your development machine.

### Polish is the difference

The gap between "cool" and "extraordinary" is in the last 20% of refinement: the easing curve on a spring animation, the timing offset in a staggered reveal, the subtle secondary motion that makes a transition feel physical.

**NEVER**:
- Ignore `prefers-reduced-motion`. This is an accessibility requirement, not a suggestion
- Ship effects that cause jank on mid-range devices
- Use bleeding-edge APIs without a functional fallback
- Add sound without explicit user opt-in
- Use technical ambition to mask weak design fundamentals; fix those first
- Layer multiple competing extraordinary moments. Focus creates impact, excess creates noise

## Verify the Result

- **The wow test**: Show it to someone who hasn't seen it. Do they react?
- **The removal test**: Take it away. Does the experience feel diminished?
- **The device test**: Run it on a phone, a tablet, a Chromebook. Still smooth?
- **The accessibility test**: Enable reduced motion. Still beautiful?
- **The context test**: Does this make sense for THIS brand and audience?

"Technically extraordinary" isn't about using the newest API. It's about making an interface do something users didn't think a website could do.
