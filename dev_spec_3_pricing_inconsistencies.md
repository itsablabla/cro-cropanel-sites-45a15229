# Pricing inconsistencies across pages — dev spec
Site: nomadinternet.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
The same plans display different price formats and values across pages, undermining trust in the stated cost.

## Evidence (from the live site)
> Prices shown on the page: $99.95/month $129.95/month $99.95/Mo $99.95/month $129.95/month $99.95
> Prices shown on the page: $99.95 /month $129.95 /month $99.95/mo $0.00 $99.95 $99.99
> Prices shown on the page: $99.95/month $129.95/month $99.95 $99.95 $214.89 $99.95/month

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Inconsistent price formats and values across pages.

## Required change
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Standardize price display format and value for each plan across all pages.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Standardize price display format and value for each plan across all pages.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_pricing_inconsistencies` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
