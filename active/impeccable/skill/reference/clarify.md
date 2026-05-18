> **Additional context needed**: audience technical level and users' mental state in context.

Find the unclear, confusing, or poorly written interface text and rewrite it. Vague copy creates support tickets and abandonment; specific copy gets users through the task.

## Assess Current Copy

1. **Find clarity problems**:
   - **Jargon**: Technical terms users won't understand
   - **Ambiguity**: Multiple interpretations possible
   - **Passive voice**: "Your file has been uploaded" vs "We uploaded your file"
   - **Length**: Too wordy or too terse
   - **Assumptions**: Assuming user knowledge they don't have
   - **Missing context**: Users don't know what to do or why
   - **Tone mismatch**: Too formal, too casual, or inappropriate for situation

2. **Understand the context**:
   - Who's the audience? (Technical? General? First-time users?)
   - What's the user's mental state? (Stressed during error? Confident during success?)
   - What's the action? (What do we want users to do?)
   - What's the constraint? (Character limits? Space limitations?)

## Improve Copy Systematically

### Error Messages
**Bad**: "Error 403: Forbidden"
**Good**: "You don't have permission to view this page. Contact your admin for access."

**Bad**: "Invalid input"
**Good**: "Email addresses need an @ symbol. Try: name@example.com"

**Principles**:
- Explain what went wrong in plain language
- Suggest how to fix it
- Don't blame the user
- Include examples when helpful

### Form Labels & Instructions
**Bad**: "DOB (MM/DD/YYYY)"
**Good**: "Date of birth" (with placeholder showing format)

**Principles**:
- Use clear, specific labels (not generic placeholders)
- Show format expectations with examples
- Explain why you're asking (when not obvious)
- Put instructions before the field, not after

### Button & CTA Text
**Bad**: "Click here" | "Submit" | "OK"
**Good**: "Create account" | "Save changes" | "Got it, thanks"

**Principles**: Describe the action specifically, use active voice (verb + noun), match user's mental model.

### Help Text & Tooltips
**Bad**: "This is the username field"
**Good**: "Choose a username. You can change this later in Settings."

**Principles**: Add value (don't just repeat the label), answer the implicit question, keep it brief but complete.

### Empty States
**Bad**: "No items"
**Good**: "No projects yet. Create your first project to get started."

**Principles**: Explain why it's empty (if not obvious), show next action clearly, make it welcoming.

### Success Messages
**Bad**: "Success"
**Good**: "Settings saved! Your changes will take effect immediately."

**Principles**: Confirm what happened, explain what happens next (if relevant), be brief but complete.

### Loading States
**Bad**: "Loading..." (for 30+ seconds)
**Good**: "Analyzing your data... this usually takes 30-60 seconds"

**Principles**: Set expectations (how long?), explain what's happening, show progress when possible.

### Confirmation Dialogs
**Bad**: "Are you sure?"
**Good**: "Delete 'Project Alpha'? This can't be undone."

**Principles**: State the specific action, explain consequences, use clear button labels, don't overuse confirmations.

## Apply Clarity Principles

1. **Be specific**: "Enter email" not "Enter value"
2. **Be concise**: Cut unnecessary words (but don't sacrifice clarity)
3. **Be active**: "Save changes" not "Changes will be saved"
4. **Be human**: "Oops, something went wrong" not "System error encountered"
5. **Tell users what to do**, not just what happened
6. **Be consistent**: Use same terms throughout (don't vary for variety)

**NEVER**:
- Use jargon without explanation
- Blame users ("You made an error" -> "This field is required")
- Be vague ("Something went wrong" without explanation)
- Use passive voice unnecessarily
- Write overly long explanations (be concise)
- Use humor for errors (be empathetic instead)
- Assume technical knowledge
- Vary terminology (pick one term and stick with it)
- Repeat information (headers restating intros, redundant explanations)
- Use placeholders as the only labels (they disappear when users type)

## Verify Improvements

- **Comprehension**: Can users understand without context?
- **Actionability**: Do users know what to do next?
- **Brevity**: Is it as short as possible while remaining clear?
- **Consistency**: Does it match terminology elsewhere?
- **Tone**: Is it appropriate for the situation?

When the copy reads cleanly, hand off to `/impeccable polish` for the final pass.
