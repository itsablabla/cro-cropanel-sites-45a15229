# Unexpected higher charge on rural page — dev spec
Site: nomadinternet.com · Priority 7 · Medium · Effort: Low (0.5-2 days)

## Problem
The rural-internet page shows a price of $214.89 that does not appear on any other page, suggesting an additional cost visitors may not anticipate.

## Evidence (from the live site)
> Prices shown on the page: $99.95/month $129.95/month $99.95 $99.95 $214.89 $99.95/month

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: $214.89 appears only on rural page.

## Required change
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Identify what $214.89 represents; remove or clearly label as bundled/one-time cost.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Identify what $214.89 represents; remove or clearly label as bundled/one-time cost.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_unexpected_higher_charge_rural` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
