# Tap test, step by step

1. Fresh browser context, 390x844, no cookies.
2. Accept nothing. Note any banner that appears and whether it overlaps the button's box.
3. Read the button's bounding box: width and height in CSS pixels.
4. Tap the center once. Watch 5 to 10 seconds for navigation, a new tab, a dialog, a scroll or a DOM change.
5. If nothing happens, repeat in two more fresh pages before calling it dead (the YC check, 2026-10-28, used 3 tries).
6. Note console errors, and keep only the ones whose stack points at the site's own code.
