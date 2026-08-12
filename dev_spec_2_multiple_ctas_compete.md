# Multiple CTAs compete for attention — dev spec
Site: nomadinternet.com · Priority 2 · High · Effort: Medium (2-5 days)

## Problem
Multiple near-identical coverage-check CTAs appear together, making it unclear which action advances the visitor versus which is a repeat, muddying the expected next step.

## Evidence (from the live site)
> 7 distinct calls to action compete on the same page: “CHECK COVERAGE”, “CHECK IF IT WORKS AT MY ADDRESS”, “SEE MY OPTIONS”, “GET STARTED”, “START CHAT”, “SEE WHAT I QUALIFY FOR”, “CHECK MY COVERAGE”.
> CHECK COVERAGE
> CHECK IF IT WORKS AT MY ADDRESS
> SEE MY OPTIONS
> CHECK MY COVERAGE

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Multiple competing CTAs on homepage.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Reduce to one primary coverage-check CTA; move secondary actions like START CHAT to supporting role.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Reduce to one primary coverage-check CTA; move secondary actions like START CHAT to supporting role.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_multiple_ctas_compete` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
