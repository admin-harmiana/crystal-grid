# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
Crystal Grid is a mobile game built as a single-file PWA with vanilla JavaScript. It features a streak crystal system, sound design, and haptic feedback experiments.

## Quick Reference
- **Spec**: `docs/STREAK_CRYSTAL_V2.md` — crystal system design document
- **Code**: `src/crystal-grid.html` — entire game in one file (HTML + CSS + JS)
- **Sound**: `src/sound-test.html` — sound system experiments

## Commands

```bash
# Install dependencies
npm install

# Serve game locally
npm run serve
# Opens at http://localhost:3003

# Capacitor (native mobile builds)
npm run cap:sync      # Sync web assets to native projects
npm run cap:ios       # Open iOS project in Xcode
npm run cap:android   # Open Android project in Android Studio
```

## Architecture

**Single-file architecture**: The game lives in `src/crystal-grid.html`:
- CSS variables for theming
- Game state managed through a global state object
- Touch/swipe detection
- localStorage for persistence (high score, settings, unlocks)

## Development Protocol

> Every change requires TWO reviews: first the plan, then the implementation.

### 1. PLAN
Create a detailed plan before writing any code:
- Specific changes to make
- Exact values (timings, colors, positions)
- Expected result

### 2. REVIEW PLAN
Launch 6 independent agents (Task tool, subagent_type="general-purpose"):
- **ARCHITECT** — Technical correctness
- **DESIGNER** — Visual consistency (has veto power)
- **ADVERSARIAL** — Find flaws (must find 2+ or explain why none)
- **OPTIMIZER** — Simplicity, no waste
- **QA** — Edge cases, bugs
- **UX** — First-time player clarity

**Scoring**: 9-10 = APPROVE, 1-8 = REJECT
**Pass**: All 6 agents approve
**Fail**: Revise plan and re-review (max 5 cycles, then escalate to user)

### 3. IMPLEMENT & VERIFY
After plan approval:
1. Implement the approved plan exactly
2. Run 6-agent review on the IMPLEMENTATION
3. Same scoring rules apply
4. If rejected: return to step 1 with fix plan

### 4. TEST IN BROWSER
Verify in real browser (not code review):

```bash
npm run serve
# Opens on http://localhost:3003
```

## Forbidden Actions
- Writing code without approved plan
- Role-playing agents (must use Task tool)
- Skipping browser testing
- "Code looks correct" as verification
- Proceeding past failed reviews

## Completion Criteria
The game is complete when implementation passes 6-agent review AND all browser tests pass.
