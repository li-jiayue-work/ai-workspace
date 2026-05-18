> **Additional context needed**: what's appropriate for the domain (playful vs professional vs quirky vs elegant).

Find the moments where unexpected polish would turn a functional interface into one users remember and tell other people about. Add only where the moment earns it; delight everywhere reads as noise.

---

## Register

Brand: delight can be distributed across copy voice, section transitions, discovery rewards, seasonal touches, personality across the whole surface.

Product: delight at specific moments, not pages. Completion, first-time actions, error recovery, milestone crossings. Reliability and consistency carry the rest of the experience; delight pushed everywhere reads as noise.

---

## Assess Delight Opportunities

Identify where delight would enhance (not distract from) the experience:

1. **Find natural delight moments**:
   - **Success states**: Completed actions (save, send, publish)
   - **Empty states**: First-time experiences, onboarding
   - **Loading states**: Waiting periods that could be entertaining
   - **Achievements**: Milestones, streaks, completions
   - **Interactions**: Hover states, clicks, drags
   - **Errors**: Softening frustrating moments
   - **Easter eggs**: Hidden discoveries for curious users

2. **Understand the context**:
   - What's the brand personality? (Playful? Professional? Quirky? Elegant?)
   - Who's the audience? (Tech-savvy? Creative? Corporate?)
   - What's the emotional context? (Accomplishment? Exploration? Frustration?)
   - What's appropriate? (Banking app != gaming app)

3. **Define delight strategy**:
   - **Subtle sophistication**: Refined micro-interactions (luxury brands)
   - **Playful personality**: Whimsical illustrations and copy (consumer apps)
   - **Helpful surprises**: Anticipating needs before users ask (productivity tools)
   - **Sensory richness**: Satisfying sounds, smooth animations (creative tools)

If any of these are unclear from the codebase, ask the user directly to clarify.

**CRITICAL**: Delight should enhance usability, never obscure it. If users notice the delight more than accomplishing their goal, you've gone too far.

## Delight Principles

### Delight Amplifies, Never Blocks
- Delight moments should be quick (< 1 second)
- Never delay core functionality for delight
- Make delight skippable or subtle
- Respect user's time and task focus

### Surprise and Discovery
- Hide delightful details for users to discover
- Reward exploration and curiosity
- Don't announce every delight moment
- Let users share discoveries with others

### Appropriate to Context
- Match delight to emotional moment (celebrate success, empathize with errors)
- Respect the user's state (don't be playful during critical errors)
- Match brand personality and audience expectations
- Cultural sensitivity (what's delightful varies by culture)

### Compound Over Time
- Delight should remain fresh with repeated use
- Vary responses (not same animation every time)
- Reveal deeper layers with continued use
- Build anticipation through patterns

## Delight Techniques

### Micro-interactions & Animation

**Button delight**:
```css
.button {
  transition: transform 0.1s, box-shadow 0.1s;
}
.button:active {
  transform: translateY(2px);
  box-shadow: 0 2px 4px rgba(0,0,0,0.2);
}
.button:hover {
  transform: translateY(-2px);
  transition: transform 0.2s cubic-bezier(0.25, 1, 0.5, 1); /* ease-out-quart */
}
```

**Loading delight**:
- Playful loading animations (not just spinners)
- Personality in loading messages (write product-specific ones, not generic AI filler)
- Progress indication with encouraging messages
- Skeleton screens with subtle animations

**Success animations**:
- Checkmark draw animation
- Confetti burst for major achievements
- Gentle scale + fade for confirmation
- Satisfying sound effects (subtle)

**Hover surprises**:
- Icons that animate on hover
- Color shifts or glow effects
- Tooltip reveals with personality
- Cursor changes (custom cursors for branded experiences)

### Personality in Copy

**Playful error messages**:
```
"Error 404"
"This page is playing hide and seek. (And winning)"

"Connection failed"
"Looks like the internet took a coffee break. Want to retry?"
```

**Encouraging empty states**:
```
"No projects"
"Your canvas awaits. Create something amazing."
```

**IMPORTANT**: Match copy personality to brand. Banks shouldn't be wacky, but they can be warm.

### Illustrations & Visual Personality

**Custom illustrations**: Empty state illustrations, error state illustrations, loading state illustrations, success state illustrations.

**Icon personality**: Custom icon set matching brand personality, animated icons, illustrative icons, consistent style across all icons.

**Background effects**: Subtle particle effects, gradient mesh backgrounds, geometric patterns, parallax depth, time-of-day themes.

### Satisfying Interactions

**Drag and drop delight**: Lift effect on drag, snap animation when dropped, satisfying placement sound, undo toast.

**Toggle switches**: Smooth slide with spring physics, color transition, haptic feedback on mobile.

**Progress & achievements**: Streak counters with celebratory milestones, progress bars that "celebrate" at 100%, badge unlocks with animation.

**Form interactions**: Input fields that animate on focus, checkboxes with satisfying scale pulse, auto-grow textareas.

### Sound Design

**Subtle audio cues** (when appropriate):
- Notification sounds (distinctive but not annoying)
- Success sounds (satisfying "ding")
- Error sounds (empathetic, not harsh)

**IMPORTANT**: Respect system sound settings, provide mute option, keep volumes quiet, don't play on every interaction.

### Loading & Waiting States

**Make waiting engaging**:
- Interesting loading messages that rotate
- Progress bars with personality
- Fun facts or tips while waiting

**WARNING**: Avoid cliched loading messages like "Herding pixels", "Teaching robots to dance", "Consulting the magic 8-ball". These are AI-slop copy, instantly recognizable as machine-generated. Write messages specific to what your product actually does.

### Celebration Moments

**Success celebrations**: Confetti for major milestones, animated checkmarks, progress bar celebrations at 100%, personalized messages.

**Milestone recognition**: First-time actions get special treatment, streak tracking and celebration, progress toward goals.

## Implementation Patterns

**Animation libraries**: Framer Motion (React), GSAP (universal), Lottie (After Effects animations), Canvas confetti (party effects)

**IMPORTANT**: File size matters. Compress images, optimize animations, lazy load delight features.

**NEVER**:
- Delay core functionality for delight
- Force users through delightful moments (make skippable)
- Use delight to hide poor UX
- Overdo it (less is more)
- Ignore accessibility (animate responsibly, provide alternatives)
- Make every interaction delightful (special moments should be special)
- Sacrifice performance for delight
- Be inappropriate for context (read the room)

## Verify Delight Quality

- **User reactions**: Do users smile? Share screenshots?
- **Doesn't annoy**: Still pleasant after 100th time?
- **Doesn't block**: Can users opt out or skip?
- **Performant**: No jank, no slowdown
- **Appropriate**: Matches brand and context
- **Accessible**: Works with reduced motion, screen readers

When the moments feel earned, hand off to `/impeccable polish` for the final pass.
