# Team Website: Lab 2 Website

**Live site:** https://EYARAN.github.io/team-website/

## Team
| Name | Registration no. | GitHub username |
|------|------------------|-----------------|
| Partner A | COM/3475/26| Eyaran |
| Partner B | COM/5927/26 | Nyagemi |

## Who drove each part
- Part 0, 2, 4: Partner A
- Part 1, 3: Partner B[cite: 1]

## Personalisation
- Our colours: Custom primary tokens updated[cite: 1].
- Projects we added: Added custom projects and a new git category[cite: 1].
- Extension challenge(s) completed: E1 added[cite: 1].

## Reflection
1. The menu toggle is a <button> because it preserves native keyboard and screen-reader accessibility that a <div> lacks[cite: 1].
2. Removing defer would cause the script to execute immediately during HTML parsing, crashing because DOM elements don't exist yet[cite: 1].
3. textContent treats input as plain text, protecting against Cross-Site Scripting (XSS) injection vulnerabilities possible with innerHTML[cite: 1].
4. Browser validation can be bypassed by users, so backend servers must always validate data for security[cite: 1].
5. Opening via file:// vs http:// changes the browser origin, isolating local storage data[cite: 1].
6. Duplicating code across pages causes maintenance headaches, which is why component frameworks exist[cite: 1].


## Reflection questions

1. **The menu toggle is a `<button>`, not a clickable `<div>`. Name two things you would lose with a `<div>`, and who would be affected.**
   If you used a `<div>` instead of a `<button>`, you would lose native keyboard focusability (the ability to tab to it) and built-in screen reader activation via the Enter or Space keys. Keyboard-only users and individuals relying on assistive technologies would be completely unable to open or close the mobile navigation menu.

2. **What would break if you removed `defer` from the `<script>` tag in `<head>`? Explain why, in terms of how the browser parses HTML.**
   Without `defer`, the browser stops parsing the HTML document the moment it encounters the script tag in the `<head>`, downloads the script, and executes it immediately. At that point, the body elements (like the navigation toggle, year span, and project list container) have not been created in the DOM yet, causing `document.querySelector()` to return `null` and crashing the script.

3. **`renderProjects` uses `textContent` rather than `innerHTML`. What could go wrong with innerHTML if project titles were typed in by visitors?**
   Using `innerHTML` interprets strings as raw HTML and code. If a visitor typed a malicious script tag (such as `<script>maliciousCode()</script>`) into a project title field, `innerHTML` would execute it directly in the browser—leading to a Cross-Site Scripting (XSS) vulnerability. `textContent` safely treats all input strictly as plain text.

4. **Your form checks its input with JavaScript. Why will the server still need to validate the same data once the form is connected to one?**
   Client-side JavaScript validation can easily be bypassed, disabled in browser DevTools, or skipped entirely by automated requests using tools like `curl`. The server must re-validate all incoming data to guarantee data integrity, security, and protection against malicious inputs before processing or storing it.

5. **Your theme choice follows you from Home to Contact, but not from a double-clicked file to Live Server. Explain this using the idea of an origin.**
   An "origin" is defined by the combination of the URL scheme, host, and port (`localStorage` is isolated per origin). When you double-click local files, your browser treats each file path (`file://...`) as a separate or changing origin, whereas Live Server runs everything under a consistent local server origin (`http://127.0.0.1:5500`), allowing them to share the same `localStorage` data pool.

6. **Name something duplicated across your HTML pages. What problem does that duplication cause, and how might it be avoided?**
   The site header (including the navigation menu and logo) and footer are duplicated across `index.html`, `projects.html`, and `contact.html`. This duplication causes maintenance issues because updating the team name or adding a navigation link requires manually editing every single HTML file, which easily leads to inconsistencies. This can be avoided by using server-side includes, templates, or a modern component-based frontend framework.
