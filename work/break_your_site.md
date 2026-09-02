# Break Your Own Site — Hardening Review

## Date: 28/08/2026

## Live URL: https://breattah.netlify.app

---

## Testing Checklist

### 1. Form Edge Cases
| Test | What Happened | Verdict |
|------|---------------|---------|
| Submit empty form | Form validation prevents submission with error message "Please fill in all fields." | ✅ Good |
| Submit with invalid email | Validation catches and shows "Please enter a valid email address." | ✅ Good |
| Submit twice fast | Button disables on first click, preventing double submission. | ✅ Good |
| Enter very long text | Textarea handles long input without breaking layout. | ✅ Good |

### 2. Link Checks
| Link | Status |
|------|--------|
| GitHub | ✅ Working |
| LinkedIn | ✅ Working |
| CV | ✅ Now links to LinkedIn (fixed from previous review) |
| Form submit | ✅ Working |

### 3. Browser/Device Testing
| Test | Result |
|------|--------|
| Chrome (Desktop) | ✅ Works |
| Safari (Mobile) | ✅ Works |
| Firefox (Desktop) | ✅ Works |

### 4. Speed Check
| Metric | Result |
|--------|--------|
| Page load time | Fast (single HTML file, no images) |
| Core Web Vitals | ✅ No issues |

---

## What I Fixed (Fix-Now)

| Issue | Fix |
|-------|-----|
| CV link was a placeholder (`#`) | ✅ Replaced with LinkedIn link |
| Form had no status messages | ✅ Added "Sending..." and error messages |
| Submit button was too small | ✅ Increased padding to 0.8rem on mobile |

---

## Known Limitations (Not Fixed Yet)

| Limitation | Why It's a Limitation | When I'll Fix It |
|------------|----------------------|------------------|
| No custom domain | Using Netlify's free subdomain | Will add a custom domain later |
| No analytics | Not tracking visitors yet | Will add before final launch |
| Only one case study | Portfolio needs more projects | Will add after I complete capstone |
| No social share preview | Share link just shows URL | Will add Open Graph tags later |

---

## Basic SEO/Meta Added

```html
<!-- Basic SEO -->
<title>Breattah Okeyo · ML Portfolio</title>
<meta name="description" content="ML practitioner building search ranking models and ML pipelines. FlyRank ML Internship portfolio showing 0.680 → 0.800 precision improvement.">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

Hardening Review Sign-Off
Reviewer: AI Assistant (Simulated)

Feedback: The site handles form edge cases well, all links work, and the basic SEO is in place. The known limitations are reasonable for this stage. The site is ready for launch.

Status: ✅ Passed

---
