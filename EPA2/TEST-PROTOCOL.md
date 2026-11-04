# TEST-PROTOCOL - CM-501 EPA 2

Date: 4 November 2026

Pages: `menu.html` and `contact.html`

Source: the original `epa2-starter.zip` supplied for this repair.

The starter was compared with the student's supplied assessment checklist before editing. The assessment PDF was not available, so checking its exact wording is still pending. The original content, fonts, fixed 1100px layout and brown colour scheme were kept. CSS changes are limited to accessibility and keeping the three menu columns after removing the layout table.

## 1. Problems found in the original pages

| # | Page | Original problem | WCAG 2.2 criterion | Repair |
|---|---|---|---|---|
| 1 | Both | No document language. | 3.1.1 Language of Page | Added `lang="en"`. |
| 2 | Both | Both titles say "Home". | 2.4.2 Page Titled | Used separate Menu and Contact titles. |
| 3 | Both | Header, navigation, content and footer are generic divs. | 1.3.1 Info and Relationships | Used `header`, `nav`, `main` and `footer`. |
| 4 | Both | No way to skip repeated navigation. | 2.4.1 Bypass Blocks | Added a skip link to `#main`. |
| 5 | Both | Navigation uses divs with mouse click handlers. | 2.1.1 Keyboard | Replaced them with normal links. |
| 6 | Both | CSS removes all focus outlines. | 2.4.7 Focus Visible | Removed that rule and added a visible outline. |
| 7 | Both | Body text is pale grey on white. | 1.4.3 Contrast (Minimum) | Darkened text within the original palette. |
| 8 | Both | Navigation and footer text/icons have poor contrast. | 1.4.3 Contrast (Minimum), 1.4.11 Non-text Contrast | Used a light cream colour on the existing brown background. |
| 9 | Menu | Category headings skip from h1 to h4. | 1.3.1 Info and Relationships | Changed category headings to h2. |
| 10 | Menu | Menu items are unrelated divs in a layout table. | 1.3.1 Info and Relationships | Used three unordered lists; kept three columns with basic CSS. |
| 11 | Menu | Prices and item names have low-contrast inline colours. | 1.4.3 Contrast (Minimum) | Kept the exact prices as text; removed pale colours and obsolete `font` tags. |
| 12 | Menu | Today's Special is only in an image with no alt text. | 1.1.1 Non-text Content | Added the exact offer, price and time as HTML text. The repeated banner is decorative with `alt=""`. |
| 13 | Menu | The coffee image has no alternative text. | 1.1.1 Non-text Content | Added a short description. |
| 14 | Contact | Phone and email are only in an unlabelled image. | 1.1.1 Non-text Content, 1.4.5 Images of Text | Replaced the image with the same details as `tel:` and `mailto:` links. |
| 15 | Contact | Form fields only have placeholders. | 1.3.1 Info and Relationships, 3.3.2 Labels or Instructions | Added visible labels linked to each existing control. |
| 16 | Contact | Required fields and expected formats are unclear. | 3.3.2 Labels or Instructions | Marked name/email as required and the remaining fields as optional; used email, date and tel types. |
| 17 | Contact | Personal-data inputs do not identify their purpose. | 1.3.5 Identify Input Purpose | Added name, email, birthday and telephone autocomplete values. |
| 18 | Contact | Send is a clickable div; `form.submit()` bypasses normal constraint validation. | 2.1.1 Keyboard, 4.1.2 Name, Role, Value, 3.3.1 Error Identification | Used a submit button. Native HTML validation provides missing-field and email-format error messages. |
| 19 | Contact | Map iframe has no title. | 4.1.2 Name, Role, Value | Added `title="Map of Munich"`, matching the existing map. |
| 20 | Both | Social icon links have no accessible names and only point to `#`. | 2.4.4 Link Purpose (In Context) | Named the links and pointed them to the platform homepages. No café account was supplied. |

Also added the HTML doctype and viewport metadata. These changes alone do not prove accessibility conformance.

## 2. Checks actually performed

Checks were carried out with AI-operated local tools on 4 November 2026. They are not a student's manual keyboard or screen-reader test.

| Check | Method | Observed result |
|---|---|---|
| Original content | Compared original and repaired HTML. | All 10 regular menu items, descriptions and prices retained. Special and contact details checked against the original images. |
| Structure and local files | Local HTML inspection and a small source-check script. | One h1 and one main per page; expected landmarks; 3 menu lists/10 items; labels match field IDs; image alt attributes and local references present; no duplicate IDs or onclick handlers. This is not W3C validation. |
| Rendering | Inspected before/after local Edge screenshots at 1280 x 1900. | Original header, fonts, image assets and three-column menu retained. Text is darker; contact details are text; labels add height to the existing form. Inspection images are not included in the submission. |
| Browser structure | Headless Microsoft Edge 156.0.4314.58, local test copies loading the repaired CSS/images. | Correct titles and heading order; 1100px wrapper; both retained menu images loaded. |
| Programmatic focus | Focused skip/navigation links in Edge and inspected computed styles. | Skip link became visible; navigation outline was 3px; skip-link target was `#main`. No physical Tab-key walkthrough was performed. |
| Empty form | Called the native form validity check in Edge. | Invalid; a browser-generated missing-name message was present. |
| Invalid email | Entered a name and `wrong` as the email, then checked validity. | Invalid; a browser-generated email-format message was present. |
| Required fields completed | Entered a name and `student@example.com`; left optional controls empty. | Valid according to browser constraints. No data was submitted. |
| Map | Inspected iframe markup. | Meaningful title present. External network requests were blocked during local rendering, so map content and keyboard behaviour were not tested. |

Contrast was calculated from the CSS hex colours using WCAG relative luminance:

| Text / background | Before | After |
|---|---|---|
| Body text / white | `#b3b3b3`: 2.10:1 | `#595959`: 7.00:1 |
| Headings / white | `#d9c6b4`: 1.66:1 | `#76533b`: 6.84:1 |
| Navigation / brown `#3b2a20` | `#8a6d5a`: 2.87:1 | `#d9c6b4`: 8.25:1 |

Repaired placeholder text `#767676` on white is 4.54:1. These are explicit CSS colour calculations, not a complete pixel or state audit. The original special banner is unchanged artwork; its information is repeated in readable HTML below it.

## 3. Tests still to complete

| Test | What to do | Actual result/date |
|---|---|---|
| Assessment PDF | Compare final files with every requirement in the professor's brief. | NOT COMPLETED: ______ |
| W3C Nu HTML Validator | Validate both pages and record errors/warnings, then fix actual findings. | NOT RUN: menu ______; contact ______ |
| Lighthouse accessibility | Run on both pages; record real results and remaining findings. | NOT RUN: menu ______; contact ______ |
| WAVE or axe | Check both pages and inspect each reported problem. | NOT RUN: ______ |
| Keyboard only | Use Tab/Shift+Tab and Enter; check skip link, navigation, form, native errors, footer and map for visible focus and traps. | NOT COMPLETED: ______ |
| Screen reader | Record tool/version; read headings, menu prices and special; complete the form and inspect error announcements. | NOT RUN: ______ |
| 200% browser zoom | Check reading, controls and clipped or lost content on both pages. | NOT RUN: ______ |
| Session 4 peer test | Record peer initials, date, tasks, difficulties and any resulting repairs. | NOT COMPLETED: ______ |
| GitHub Pages | Open the deployed menu/contact pages and check links/assets. | NOT CHECKED: ______ |

The original fixed-width layout is retained because the starter README assigns layout/responsiveness to EPA 3. Reflow and zoom conformance are not claimed. The form still uses the starter's example URL, so there is no verified working subscription/reservation service. Phone/email links also retain the original example details.

## 4. Limits of automated checks

Source checks can find missing labels and basic structural problems. They cannot show whether a screen-reader user understands the page or hears browser errors clearly. A real keyboard walkthrough, zoom check and peer test are still needed. A score alone would not establish WCAG conformance.

## 5. AI assistance

AI assistance was used to inspect the supplied starter, make targeted HTML/CSS repairs, run the recorded local checks and draft this protocol; student review and the unfinished human tests are still required.
