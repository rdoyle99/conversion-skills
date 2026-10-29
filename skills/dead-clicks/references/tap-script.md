# Scripted tap test (Playwright outline)

1. New context, viewport 390x844, no cookies.
2. Collect elements matching `a, button, [role=button], [onclick], img, [class*=card]` that are visible.
3. For each: record URL and DOM hash, tap, wait up to 10 seconds, compare. No change = candidate.
4. Re-test candidates in 2 more fresh pages. Dead only if all 3 show no response.
5. Report the selector, the page and a screenshot.
