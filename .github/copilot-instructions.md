# UX Design Guidelines: Video FX Workflows for Neurodivergent Users

**Target User:** 10-year-old autistic user  
**Context:** Vegas Pro FX automation tools  
**Focus:** Predictability, minimal cognitive load, clear patterns

---

## ACKNOWLEDGED PRIORITIES

1. **Predictability** - Same action = same result, every time
2. **Minimal choices at one time** - Reduce decision paralysis
3. **Clear naming and repeatable actions** - Consistency over creativity

---

## CORE INTERACTION PATTERNS

### Pattern 1: Linear Workflow (Not Branching)
**Principle:** One step at a time, in order

**Good:**
```
Step 1: Choose Video → Step 2: Choose Effect → Step 3: Apply
```

**Avoid:**
```
Main Menu with 15 options at once
└── Overwhelming, unclear starting point
```

**Why:** Branching choices cause decision paralysis. Sequential steps provide structure.

---

### Pattern 2: Preview Before Commit
**Principle:** Show what will happen before it happens

**Good:**
- Show preview thumbnail/video of effect
- "This will add [Effect Name] to your video"
- Undo button always visible

**Avoid:**
- Instant apply without preview
- Destructive actions without warning
- Hidden undo functionality

**Why:** Predictability requires seeing outcomes before commitment. Reduces anxiety about "wrong" choices.

---

### Pattern 3: Consistent Button Locations
**Principle:** Same button = same place, always

**Good:**
- "Next" always bottom-right
- "Cancel" always bottom-left
- "Help" always top-right corner

**Avoid:**
- Changing button positions between screens
- Context-dependent button locations
- Buttons that move based on content

**Why:** Muscle memory reduces cognitive load. User shouldn't hunt for controls.

---

### Pattern 4: Visual + Text Labels (Always)
**Principle:** Never rely on icons alone

**Good:**
```
[Icon: ✓] Apply Effect
[Icon: ↶] Undo
[Icon: ❓] Help
```

**Avoid:**
```
[✓] [↶] [❓]  ← Icon-only buttons
```

**Why:** Symbol interpretation varies. Text eliminates ambiguity.

---

## NAMING CONVENTIONS

### Use Literal, Descriptive Names

**Good Examples:**
- "Add Brightness Effect"
- "Remove Last Effect"
- "Save Video with Effects"
- "Start Over"

**Avoid:**
- "Enhance" (vague)
- "Process" (technical jargon)
- "OK" without context (OK to what?)
- Clever puns or wordplay

**Why:** Literal names are predictable. User should know exactly what happens.

---

### Consistent Action Verbs

Use the same verb for the same type of action:

| Action Type | Verb to Use | NOT These |
|------------|-------------|-----------|
| Adding something | "Add" | Insert, Include, Append |
| Removing something | "Remove" | Delete, Erase, Clear |
| Seeing a preview | "Preview" | View, Show, Display |
| Finalizing | "Apply" | Save, Commit, Execute |
| Going back | "Undo" | Revert, Reverse, Back |

**Why:** Using one verb per action type builds pattern recognition.

---

## MINIMAL CHOICES STRATEGIES

### Strategy 1: Wizard-Style Progression
Break complex tasks into small steps with 2-4 options max per screen

**Example Flow:**
```
Screen 1: "What do you want to do?"
  → Add an effect
  → Remove an effect

Screen 2: "Which effect?" (Show 3-4 at a time, with "More" button)
  → Brightness
  → Blur
  → [More Effects →]

Screen 3: "How much?" (Single slider)
  → Brightness: [||||||||--------] 

Screen 4: "Preview and apply"
  → [Preview] [Apply] [Start Over]
```

**Why:** Each screen = one decision. Manageable.

---

### Strategy 2: Progressive Disclosure
Show advanced options only when needed

**Good:**
```
Basic Mode (default):
  - 3 most common effects
  - Simple controls

[Show More Options] button (if needed)
```

**Avoid:**
```
All 50 effects displayed at once
with all parameters exposed
```

**Why:** Reduces visual clutter and decision fatigue.

---

### Strategy 3: Smart Defaults
Always provide a safe, reasonable default selection

**Good:**
- Default effect strength: 50%
- Most commonly used effect pre-selected
- "Recommended" label on good starting choice

**Avoid:**
- Blank forms requiring all inputs
- No pre-selection forcing choice
- Equal weighting of all options

**Why:** Reduces pressure to make "right" choice. Provides starting point.

---

## REPETITION & PATTERNS

### Make Common Actions Easy to Repeat

**Good:**
- "Apply Same Effect to Another Video" button after first success
- "Do This Again" clearly labeled
- Recently used effects shown first

**Avoid:**
- Having to navigate full menu tree each time
- No memory of previous actions
- Making user rebuild workflow from scratch

**Why:** Autistic users often prefer repetition and routines. Support this.

---

### Consistent Feedback

Every action should have same type of feedback:

**Pattern:**
```
Action Started → Visual indicator (spinner/progress)
Action Complete → Success message + sound (if enabled)
Action Failed → Clear error + what to do next
```

**Good:**
- "Effect applied successfully ✓"
- "Effect not applied. Video file is too large. Try a shorter video."

**Avoid:**
- Silent failures
- Generic "Error" messages
- Different feedback styles for similar actions

**Why:** Predictable feedback = learning what actions do.

---

## POTENTIAL CONFUSION / OVERLOAD FLAGS

### 🚩 RED FLAGS TO AVOID

1. **Multiple Steps Happening at Once**
   - Avoid: "Applying 5 effects simultaneously..."
   - Do: Show progress for each effect, one at a time

2. **Ambiguous State Indicators**
   - Avoid: Grayed-out buttons without explanation
   - Do: "This button is disabled because: [reason]"

3. **Time Pressure**
   - Avoid: Auto-advancing screens, timed actions
   - Do: Let user control pacing completely

4. **Unexpected Popups/Modals**
   - Avoid: Random tutorial tips, promotional popups
   - Do: Put help in consistent location, user-initiated

5. **Inconsistent Terminology**
   - Avoid: Calling same thing "effect" sometimes, "filter" other times
   - Do: Pick ONE term and use it always

6. **Hidden Prerequisites**
   - Avoid: Button doesn't work, no explanation why
   - Do: "You need to select a video first" shown early

7. **Too Much Animation/Motion**
   - Avoid: Spinning, bouncing, constant movement
   - Do: Subtle, purposeful transitions only
   - Note: Some autistic users are sensitive to motion

8. **Sound Without Visual Backup**
   - Avoid: Audio-only notifications
   - Do: Always pair sound with visual indicator
   - Provide sound on/off toggle

9. **Tiny Click Targets**
   - Avoid: Small icons, closely spaced buttons
   - Do: Large, well-spaced controls (min 44x44px)

10. **Automatic Focus Stealing**
    - Avoid: Dialog pops up and grabs keyboard focus
    - Do: Gentle notification, user chooses when to interact

---

## WORKFLOW DECISION FRAMEWORK

When designing any workflow step, ask:

### 1. PREDICTABILITY CHECK
- ✓ Does this action always produce the same result?
- ✓ Can user predict what will happen before clicking?
- ✓ Is there a clear way to undo?

### 2. CHOICE LOAD CHECK
- ✓ Are there 4 or fewer options on this screen?
- ✓ Is there a recommended/default option?
- ✓ Can we defer any choices to later steps?

### 3. CLARITY CHECK
- ✓ Would a literal 10-year-old understand this label?
- ✓ Is there both icon AND text?
- ✓ Does the error message say what to do next?

### 4. CONSISTENCY CHECK
- ✓ Do we use this word/button location elsewhere the same way?
- ✓ Is the feedback pattern same as similar actions?
- ✓ Would user recognize this from previous use?

---

## EXAMPLE GOOD WORKFLOW

**Task:** Add brightness effect to a video

### Step 1: Video Selection
```
Screen Title: "Choose Your Video"

[Large preview boxes, 2 per row]
┌─────────────┐  ┌─────────────┐
│  Video 1    │  │  Video 2    │
│  [thumbnail]│  │  [thumbnail]│
│  (Selected ✓)  │  [Select]   │
└─────────────┘  └─────────────┘

[Next: Add Effect →]  [Cancel]
```
- Only 1 decision: which video
- Visual preview available
- Clear selected state
- Consistent button positions

---

### Step 2: Effect Selection
```
Screen Title: "Choose Effect for Video 1"

Pick one effect:
┌─────────────────┐
│ ● Brightness    │ ← Pre-selected (recommended)
│ ○ Blur          │
│ ○ Color Tint    │
│ [Show More Effects →] │
└─────────────────┘

[Preview]  [← Back]  [Next: Adjust →]
```
- 3-4 options visible
- Recommended option pre-selected
- Preview available before committing
- Back button for safety

---

### Step 3: Adjustment
```
Screen Title: "Adjust Brightness"

Current Setting: Medium ✓ (Recommended)

Brightness amount:
Less  [||||||||--------] More
      ↑
    50% (Default)

[Preview Video]  
[← Back]  [Apply Effect →]
```
- Single control (slider)
- Clear default shown
- Preview button obvious
- Labeled slider endpoints

---

### Step 4: Confirmation
```
Screen Title: "Effect Applied Successfully ✓"

[Video preview showing result]

What next?
┌────────────────────────┐
│ [Apply to Another Video] │
│ [Add Another Effect]     │
│ [Save Video]            │
│ [Start Over]            │
└────────────────────────┘
```
- Clear success message
- Preview of result
- Limited, clear next steps
- Option to repeat pattern

---

## ACCESSIBILITY CONSIDERATIONS

### Visual
- High contrast mode option
- Adjustable text size
- No reliance on color alone (use shape + color)

### Auditory  
- All sounds optional
- Visual equivalents for audio feedback

### Motor
- Large click targets (min 44x44px)
- No required drag-and-drop (offer alternative)
- Keyboard navigation support

### Cognitive
- Adjustable time limits (or none)
- Option to save progress
- Simple language setting (ELI5 mode)

---

## TESTING RECOMMENDATIONS

### Test with actual users:
1. Give task with no instruction
2. Observe without helping
3. Count how many times user says "I don't know what to do"
4. Count backtrack/undo actions
5. Note any signs of stress/frustration

### Success metrics:
- User completes task without asking for help
- User can repeat task faster second time (pattern learned)
- User reports feeling "in control"
- No errors or easy recovery from errors

---

## SUMMARY: GOLDEN RULES

1. **One decision at a time**
2. **Preview before commit**
3. **Same button = same place**
4. **Pictures + words, never pictures alone**
5. **Use literal names, not creative ones**
6. **Provide safe defaults**
7. **Make repetition easy**
8. **Give consistent feedback**
9. **Never surprise the user**
10. **When in doubt, simplify**

---

## IMPLEMENTATION NOTES FOR DEVELOPERS

This document describes UX patterns and decisions, NOT code.

When implementing:
- Prioritize these UX patterns over feature quantity
- Test each decision point for cognitive load
- Maintain consistency even if it means more code
- Document any deviations with rationale
- Involve neurodiverse users in testing when possible

---

**Document Version:** 1.0  
**Last Updated:** 2026-02-01  
**Purpose:** Guide development of Vegas Pro FX automation tools for neurodivergent users
