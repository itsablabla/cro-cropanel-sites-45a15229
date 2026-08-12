# Repeated coverage forms create friction — dev spec
Site: nomadinternet.com · Priority 5 · Medium · Effort: Medium (2-5 days)

## Problem
The same coverage-check form appears multiple times across pages, each requiring the visitor to re-enter their address, adding effort before seeing plan options.

## Evidence (from the live site)
> 7 distinct calls to action compete on the same page: “CHECK COVERAGE”, “CHECK IF IT WORKS AT MY ADDRESS”, “SEE MY OPTIONS”, “GET STARTED”, “START CHAT”, “SEE WHAT I QUALIFY FOR”, “CHECK MY COVERAGE”.

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Repeated coverage forms across pages.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Persist address input across session; pre-fill or skip redundant checks.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Persist address input across session; pre-fill or skip redundant checks.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_repeated_coverage_forms` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
