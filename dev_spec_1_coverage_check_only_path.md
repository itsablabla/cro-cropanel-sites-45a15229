# Coverage check is the only path — dev spec
Site: nomadinternet.com · Priority 1 · Urgent · Effort: Low (0.5-2 days)

## Problem
Coverage check is the only path

## Evidence (from the live site)
> 7 distinct calls to action compete on the same page: “CHECK COVERAGE”, “CHECK IF IT WORKS AT MY ADDRESS”, “SEE MY OPTIONS”, “GET STARTED”, “START CHAT”, “SEE WHAT I QUALIFY FOR”, “CHECK MY COVERAGE”.

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Coverage form is the only path; fields unreliable.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Ensure coverage form fields render with stable, accessible names and labels.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Ensure coverage form fields render with stable, accessible names and labels.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_coverage_check_only_path` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
