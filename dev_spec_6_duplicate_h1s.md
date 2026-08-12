# Duplicate H1s dilute page focus — dev spec
Site: nomadinternet.com · Priority 6 · Medium · Effort: Low (0.5-2 days)

## Problem
Multiple pages carry three identical H1 headings, so the primary value proposition is repeated instead of a single clear entry point, weakening information scent for first-time visitors.

## Evidence (from the live site)
> The page's main headline reads “Reliable Internet That Works Anywhere in the U.S”.
> The page's main headline reads “Internet That Just Works”.
> The page's main headline reads “Let's Get You the Right Internet”.

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Multiple identical H1s on page.

## Required change
h1: Reliable Internet That Works Anywhere in the U.S.; cta: CHECK COVERAGE; notes: Reduce to one H1 per page; demote others to H2 or supporting copy.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Reduce to one H1 per page; demote others to H2 or supporting copy.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_h1s` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
