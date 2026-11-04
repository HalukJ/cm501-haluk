# TEST-PROTOCOL — CM-501 EPA 2

**Scope:** `menu.html` and `contact.html` (with a shared navigation and supporting pages).  
**Date:** 4 November 2026.  
**Status:** Implemented local example solution; external assessment tests and student/peer observations are still required.

> **Source limitation:** The course's actual `epa2-starter/` (`menu.html`, `contact.html`, `before.css`, `img/`) was not provided and could not be recovered. The "after" site in this archive is a self-contained, original implementation based on the PDF assessment specification, **not a line-by-line repair of the teacher's original starter**. Accordingly, all original "before" measurements are **unknown**. The issue list below documents the accessibility risks specified by the assessment and how this solution addresses them; it does **not** claim that any specific defect was observed in the unseen starter.

## C1 — Issue list and corresponding implementations

| # | Page | Accessibility issue to address (unseen baseline) | WCAG 2.2 success criterion | Implemented solution and evidence |
|---|---|---|---|---|
| 1 | Menu | Document language not set | 3.1.1 Language of Page | `<html lang="en">` in `menu.html`. |
| 2 | Both | Unclear document title | 2.4.2 Page Titled | `Menu — Campus Café` / `Contact — Campus Café` titles. |
| 3 | Both | Main content difficult to skip and identify | 2.4.1 Bypass Blocks | A focusable skip link, one `<main id="main">` per page. |
| 4 | Both | Navigation built from generic clickable elements | 2.1.1 Keyboard | `<nav aria-label="Main navigation">` containing a list of real `<a href>` links. |
| 5 | Menu | Missing semantic heading hierarchy | 1.3.1 Info and Relationships | One `<h1>Menu</h1>`, `<h2>` category headings. |
| 6 | Menu | Menu items or prices not represented as real text | 1.3.1 Info and Relationships | `<ul><li>` items, text descriptions, and visible price strings in HTML. |
| 7 | Menu | Today's special present in image only | 1.1.1 Non-text Content | The name and total price of the sample special are selectable text; the decorative illustration has `alt=""`. |
| 8 | Menu | Improper missing or redundant image alternatives | 1.1.1 Non-text Content | Each `<img>` has `alt`, descriptive only where it conveys information. |
| 9 | Both | Anonymous social-media link | 2.4.4 Link Purpose (In Context) | Footer link has explicit accessible name "Instagram home page (example external link)". |
| 10 | Both | Invisible keyboard focus | 2.4.7 Focus Visible | Three-pixel `:focus-visible` outline with offset; high-contrast outline on dark header/footer. |
| 11 | Both | Text and background insufficiently distinguishable | 1.4.3 Contrast (Minimum) | Main text, links and controls use tested pairings above 4.5:1 (see C2). |
| 12 | Contact | Unlabeled text fields | 3.3.2 Labels or Instructions | Explicit `<label for>` for each form field and instructions in `aria-describedby`. |
| 13 | Contact | Email/name autofill purpose not marked | 1.3.5 Identify Input Purpose | `type="email"`, `autocomplete="email"`, `autocomplete="name"`. |
| 14 | Contact | Missing identification of required entries | 3.3.2 Labels or Instructions | Text “(required)” in labels, plus native `required` attributes and help text. |
| 15 | Contact | Errors not clearly identified | 3.3.1 Error Identification | Browser-native validation for `required`, email format, and minimum length. **No custom error summaries:** requires human screen-reader verification. |
| 16 | Contact | Fake clickable form submission element | 4.1.2 Name, Role, Value | A native `<button type="submit">`, keyboard accessible. |
| 17 | Contact | Phone/email not copyable or actionable | 1.3.1 Info and Relationships | Address text plus meaningful `tel:` and `mailto:` links. |
| 18 | Contact | Map iframe ambiguous or privacy-invasive | 4.1.2 Name, Role, Value | Third-party iframe omitted; full street address appears as text. |
| 19 | Both | Content lost on narrow/zoomed screens | 1.4.10 Reflow | Grid collapses on small viewports; checked at widths 1280, 640 and 360 CSS pixels. |

**Illustrative content:** The sample menu items, prices and contact details are fictional. They are not confirmed to match the original Campus Café starter and must be reconciled if the real starter becomes available.

## C2 — Automated checks (what actually ran)

| Test | Menu BEFORE | Menu AFTER | Contact BEFORE | Contact AFTER |
|---|---|---|---|---|
| Local custom structural checks (HTML source) | N/A, source unavailable | 0 flags found | N/A, source unavailable | 0 flags found |
| Local Chromium rendering (1280/640/360 CSS px) | N/A | 3 widths, no horizontal overflow | N/A | 3 widths, no horizontal overflow |
| Internal links and local image assets | N/A | Pass | N/A | Pass |
| Native browser form constraint checks | N/A | Not applicable | N/A | Empty form invalid; incorrectly formatted email invalid |
| W3C Nu Validator — errors/warnings | Not run | Not run | Not run | Not run |
| Lighthouse — accessibility score | Not run | Not run | Not run | Not run |
| WAVE or axe — issues | Not run | Not run | Not run | Not run |

Browser checks were executed using a headless local Chromium instance on **DOM snapshots with the local CSS and SVG assets inlined for testing**, because the test environment blocked direct navigation to `file://` and localhost. They provide evidence of rendering and basic browser behavior, **not certification of WCAG conformance**. The results of the basic local checks are summarized in the table above; no automated WCAG conformance score is claimed.

**Contrast calculations**, using the standard WCAG relative luminance formula and the CSS hex values: primary text on cream `#202d27 / #f7f4ed` = **13.04:1**; muted text on white `#44534a / #ffffff` = **8.13:1**; links on white `#174e70 / #ffffff` = **8.90:1**; white on primary button `#ffffff / #224c3e` = **9.67:1**; white on the header `#ffffff / #17392e` = **12.64:1**. These are representative explicit colors; a full pixel audit including every state was not run.

**Screenshots captured locally:** `evidence/EPA2-menu-1280.png`, `evidence/EPA2-contact-1280.png`, `evidence/EPA2-contact-360.png`. These are **after** rendering screenshots, not W3C/Lighthouse/WAVE reports.

## C3 — Manual checks

### Keyboard walkthrough (partly reproduced in Chromium)

- On `menu.html` and `contact.html`, the first Tab focuses **Skip to main content**. Activating it sets `#main`; browser automation reports PASS.
- Real links and controls have native keyboard-focus semantics; a three-pixel focus outline is configured in CSS.
- `contact.html` has five required controls (name, email, subject, message, consent), all with associated labels. Chromium confirmed that an empty form is invalid and a bad email format is rejected.
- **Human keyboard-only assessment not yet completed:** navigate all links and all form fields in both directions; activate button and verify native error message announcements. Record the result after using your own browser.

### Screen-reader test

**Not performed.** The student's required hands-on NVDA/VoiceOver/Narrator task must be recorded after actual use. Suggested tasks: list headings and landmarks, find the Flat White price, identify the special from text, tab to each labeled contact field, attempt an invalid submission, verify the announcement of errors.

### Zoom to 200%

**Actual browser zoom not performed.** The browser snapshot was checked for reflow at 640 and 360 CSS-pixel viewports as a useful proxy, without overflow. Set actual browser zoom to 200% at the target screen size and verify that all labels, buttons and content stay usable; record observed results.

## C4 — Session 4 peer test

**Not performed; requires a classmate.** Record peer name or initials, date, tasks, problems reported and fixes. No peer findings or subsequent fixes have been invented.

## C5 — Limits of automation

Automated scanners detect many missing labels and syntax errors, but they cannot reliably decide whether link wording makes sense to a person using a screen reader. A menu can have a technically valid image alternative while the special price remains difficult to copy, translate or enlarge; rendering the price as HTML text is more useful. An automated score also cannot demonstrate that an actual keyboard user can complete a task efficiently or that browser-native form errors are announced clearly. Here, the contact form appears semantically correct in static checks, but a real NVDA test and a human assessment are still needed.

## AI-use disclosure

AI assistance was used to **generate this provisional example site**, explain semantic/accessibility choices, and draft a reproducible local check. The student has not yet personally reviewed or orally defended the code; this review and the required human tests must be done before submitting it as their own work, as required by the assessment brief.
