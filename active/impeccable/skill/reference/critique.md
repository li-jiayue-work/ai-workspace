> **Additional context needed**: what the interface is trying to accomplish.

### Setup: Resolve Target and Load Ignore List

1. **Resolve the primary artifact.** The user's phrasing ("the homepage", "the pricing flow") is not stable enough to track across runs. Resolve it to a concrete file path or URL.

2. **Compute the slug.** Run:
   ```bash
   node .claude/skills/impeccable/scripts/critique-storage.mjs slug "<resolved-path-or-url>"
   ```

3. **Read the ignore list** at `.impeccable/critique/ignore.md` if it exists. When a finding's text matches a line here, drop it silently.

### Gather Assessments

Launch two independent assessments. Neither may see the other's output.

**Tab isolation**: When browser automation is available, each assessment MUST create its own new tab.

#### Assessment A: LLM Design Review

Read the relevant source files (HTML, CSS, JS/TS) and, if browser automation is available, visually inspect the live page. Think like a design director. Evaluate:

**AI Slop Detection (CRITICAL)**: Does this look like every other AI-generated interface? Review against ALL DON'T guidelines from the parent impeccable skill.

**Holistic Design Review**: visual hierarchy, information architecture, emotional resonance, discoverability, composition, typography, color, states & edge cases, microcopy.

**Cognitive Load** (consult [cognitive-load](cognitive-load.md)):
- Run the 8-item cognitive load checklist. Report failure count: 0-1 = low (good), 2-3 = moderate, 4+ = critical.
- Count visible options at each decision point. If >4, flag it.
- Check for progressive disclosure.

**Emotional Journey**:
- What emotion does this interface evoke? Is that intentional?
- **Peak-end rule**: Is the most intense moment positive? Does the experience end well?
- **Emotional valleys**: Check for anxiety spikes at high-stakes moments.

**Nielsen's Heuristics** (consult [heuristics-scoring](heuristics-scoring.md)):
Score each of the 10 heuristics 0-4.

Return structured findings: AI slop verdict, heuristic scores, cognitive load assessment, what's working (2-3 items), priority issues (3-5 with what/why/fix), minor observations, provocative questions.

#### Assessment B: Automated Detection

Run the bundled deterministic detector:

**CLI scan**:
```bash
npx impeccable detect --json [--fast] [target]
```

**Browser visualization**: required when browser automation tools are available AND the target is a viewable page.

1. **Start the live detection server**: `npx impeccable live &`
2. **Create a new tab** and navigate to the page
3. **Label the tab**: `document.title = '[Human] ' + document.title;`
4. **Inject**: `const s = document.createElement('script'); s.src = 'http://localhost:PORT/detect.js'; document.head.appendChild(s);`
5. Wait 2-3 seconds, then read results from console with pattern `impeccable`
6. **Cleanup**: `npx impeccable live stop`

Return: CLI findings (JSON), browser console findings (if applicable), and any false positives noted.

### Generate Combined Critique Report

#### Design Health Score

Present the Nielsen's 10 heuristics scores as a table:

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | Visibility of System Status | ? | [specific finding or "n/a" if solid] |
| 2 | Match System / Real World | ? | |
| 3 | User Control and Freedom | ? | |
| 4 | Consistency and Standards | ? | |
| 5 | Error Prevention | ? | |
| 6 | Recognition Rather Than Recall | ? | |
| 7 | Flexibility and Efficiency | ? | |
| 8 | Aesthetic and Minimalist Design | ? | |
| 9 | Error Recovery | ? | |
| 10 | Help and Documentation | ? | |
| **Total** | | **??/40** | **[Rating band]** |

Be honest with scores. A 4 means genuinely excellent. Most real interfaces score 20-32.

#### Anti-Patterns Verdict

**Start here.** Does this look AI-generated?

**LLM assessment**: Your own evaluation of AI slop tells. Cover overall aesthetic feel, layout sameness, generic composition, missed opportunities for personality.

**Deterministic scan**: Summarize what the automated detector found, with counts and file locations. Note any additional issues and flag any false positives.

**Visual overlays** (if browser was used): Tell the user that overlays are now visible in the **[Human]** tab.

#### Overall Impression
A brief gut reaction: what works, what doesn't, and the single biggest opportunity.

#### What's Working
Highlight 2-3 things done well. Be specific about why they work.

#### Priority Issues
The 3-5 most impactful design problems, ordered by importance.

For each issue, tag with **P0-P3 severity**:
- **[P?] What**: Name the problem clearly
- **Why it matters**: How this hurts users or undermines goals
- **Fix**: What to do about it (be concrete)
- **Suggested command**: Which command could address this (from: craft, teach, extract, document, shape, critique, audit, polish, bolder, quieter, distill, harden, onboard, live, animate, colorize, typeset, layout, delight, overdrive, clarify, adapt, optimize)

#### Persona Red Flags

Auto-select 2-3 personas most relevant to this interface type (consult [personas](personas.md)). For each selected persona, walk through the primary user action and list specific red flags found:

**Alex (Power User)**: No keyboard shortcuts detected. Form requires 8 clicks for primary action. Forced modal onboarding. High abandonment risk.

**Jordan (First-Timer)**: Icon-only nav in sidebar. Technical jargon in error messages ("404 Not Found"). No visible help. Will abandon at step 2.

Be specific. Name the exact elements and interactions that fail each persona.

#### Minor Observations
Quick notes on smaller issues worth addressing.

#### Questions to Consider
Provocative questions that might unlock better solutions.

**Remember**:
- Be direct. Vague feedback wastes everyone's time.
- Be specific. "The submit button," not "some elements."
- Give concrete suggestions. Cut "consider exploring..." entirely.
- Prioritize ruthlessly. If everything is important, nothing is.
- Don't soften criticism. Developers need honest feedback to ship great design.

### Persist the Snapshot

Write it to `.impeccable/critique/`:

```bash
IMPECCABLE_CRITIQUE_META='{"target":"<user phrasing>","total_score":<n>,"p0_count":<n>,"p1_count":<n>}' \
  node .claude/skills/impeccable/scripts/critique-storage.mjs write <slug> <body-file>
```

Then read the trend:
```bash
node .claude/skills/impeccable/scripts/critique-storage.mjs trend <slug> 5
```

Append a single line:
> **Trend for `<slug>` (last 5 runs): 24 -> 28 -> 32 -> 29 -> 32**
> Wrote `.impeccable/critique/<filename>`.

### Ask the User

After presenting findings, use targeted questions based on what was actually found. Ask 2-4 questions maximum with concrete options.

### Recommended Actions

List recommended commands in priority order, based on the user's answers. Only recommend commands from the impeccable command set. End with `/impeccable polish` as the final step if any fixes were recommended.

> You can ask me to run these one at a time, all at once, or in any order you prefer.
>
> Re-run `/impeccable critique` after fixes to see your score improve.
