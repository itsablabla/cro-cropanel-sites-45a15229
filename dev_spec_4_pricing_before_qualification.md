# Pricing appears before qualification — dev spec
Site: nomadinternet.com · Priority 4 · Medium · Effort: Medium (2-5 days)

## Problem
Pricing is displayed before the user completes the coverage check, so the stated monthly cost is not tied to their specific qualification.

## Evidence (from the live site)
> A section heading reads “$99.95 /month”.
> A section heading reads “$129.95 /month”.
> A section heading reads “$0.00 (one-time)”.
> A section heading reads “$99.99 (one-time)”.
> 3 distinct calls to action compete on the same page: “CHECK COVERAGE”, “SEE WHAT I QUALIFY FOR”, “CHECK MY COVERAGE”.

## Current state
h1: Internet That Just Works; cta: CHECK COVERAGE; notes: Pricing shown before qualification.

## Required change
h1: Internet That Just Works; cta: CHECK COVERAGE; notes: Present pricing only after coverage check.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Present pricing only after coverage check.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_pricing_before_qualification` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
