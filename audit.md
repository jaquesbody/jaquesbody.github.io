Project: Phase 1 — Portfolio Homepage (jaquesbody.github.io)
Audit triggered: 13th June 2026
Trigger reason: version complete


**1. What went well**

- The Phase 0 design system was built and committed before any project
  work began. This was the protocol working correctly — it saved
  significant rework during Phase 1 because tokens, spacing, and dark
  mode were already resolved.
- CSS variable architecture is solid. :root is well-structured,
  commented, and the accent pattern (undefined in the base, injected
  per project) is exactly right. This will scale cleanly across all
  future projects.
- Privacy posture is clean. No external fonts, no CDN, no analytics,
  no tracking scripts, no external JS dependencies. Every script and
  link tag is local. rel="noopener noreferrer" on all external links.
  This was deliberate and it held.
- The baseof.html title logic is correct: falls back to
  "jaquesbody: portfolio" when no page title is set, appends
  "| jaquesbody" when one is.
- Accessibility basics are present: aria-label on nav, social links,
  logos; aria-hidden="true" on decorative SVGs.
- Dark mode implemented correctly via prefers-color-scheme — token
  swap only, no layout duplication.
- The Inter font deviation from the system font stack default is
  documented in a CSS comment and in protocol.md. This is the correct
  way to handle a deviation.
- The site deployed and a non-technical user can navigate it without
  instruction. The single outcome (potential employer concludes: worth
  talking to) is achievable from the live page.


**2. What went wrong**

- .hugo_build.lock was committed to the repo. It is explicitly listed
  in .gitignore and explicitly prohibited in protocol.md Section 6.5.
- Commit messages before the final two commits do not follow protocol.
  "Fresh start: Basic Hugo site", "Create hugo.yml", "Clean slate
  before rebuild" are all capitalised and do not follow the lowercase
  present-tense format. A wip: commit was left unresolved in the
  history.
- The .under-construction CSS block was duplicated in main.css — a
  direct result of the CSS save failure and re-append without removing
  the original block.
- --text-muted was referenced via inline styles in baseof.html but
  was not defined in main.css. The footer copyright line and email
  element fell back to inherited colour. A bug that made it to
  production.
- Inline styles were present in baseof.html — style="padding: 1px;"
  on the GitHub icon link, style="color: var(--text-secondary);" on
  the footer email, style="color: var(--text-muted);" on the copyright
  line. All three should have been handled in main.css via classes.
- SVG icon sizes were inconsistent across the footer: X 24x24, Nostr
  23x23, GitHub 28x28. Root cause: Nostr viewBox has an offset
  (52 47 160 160) requiring a workaround size of 22x22. GitHub path
  weights render too thin at 24x24 requiring 28x28. All three need
  normalising in Phase 2 via Inkscape.
- config.toml is named config.toml, not hugo.toml per protocol
  standard. To be corrected at Phase 2 project initialisation.
- var used in main.js instead of const.
- navigator.clipboard.writeText() had no .catch(). Silent failure on
  clipboard permission denial.
- No null check on data-copy attribute in main.js.


**3. Root cause of each failure**

- .hugo_build.lock committed — knowledge gap. File was tracked before
  .gitignore was configured. git rm --cached was not applied. A git
  status check before staging would have caught it.
- Commit message violations — protocol not established at project
  start. Early commits predate formalised protocol. Fix: treat
  protocol.md as a pre-flight check at session start, not a reference
  consulted after the fact.
- Duplicate CSS block — CSS save failure during build led to full
  re-append without removing the original block. A git diff review
  before committing would have made this visible.
- --text-muted undefined — token used in baseof.html without being
  added to :root in main.css. Would have been caught by a browser dev
  tools check during pre-commit review. Visual check was not thorough
  enough.
- Inline styles — vibe-coding pattern. Path of least resistance during
  iteration. No pre-commit CSS audit performed.
- Inconsistent SVG sizes — Nostr SVG sourced with non-standard viewBox
  offset. GitHub path weight issue. No visual consistency check
  performed against the icon set before committing.
- config.toml naming — Hugo default on initialisation. No step in the
  workflow enforces a rename. Protocol gap.
- var in main.js — vibe-coded output accepted without review.
- No .catch() — vibe-coded output, edge case not flagged at output
  time and not caught during review.
- No null check — same root cause as above.


**4. Brutal review**

The site looks good. The design system is genuinely well-built. But
the code quality underneath the visual layer has several issues that
would not pass a professional review, and most of them are traceable
to the same pattern: vibe-coded output was accepted without a
systematic review step.

The build checklist had "Hugo dev server — full review before commit"
ticked. That review was either not thorough enough or it was a visual
check only. A visual check is not a code review. The --text-muted bug,
the duplicate CSS block, and the inline styles all made it to
production. None are subtle — they would be visible in a 10-minute
file review.

The .hugo_build.lock issue is the most concrete protocol violation.
It is not cosmetic — it means a generated file was being
version-controlled, creating noise in future diffs.

The commit history shows a project started before the protocol was
established. The wip: commit left unresolved after phase completion
was not treated as a checkpoint.

The JS is 14 lines and had two error handling gaps. For a portfolio
a potential employer might inspect, this matters.


**4a. Code and Repo Review**

Templates:
- [x] layouts/_default/baseof.html — title block correct, meta tags
      present, font loading correct, accent variable injection present.
      Issues found and fixed: inline styles on three elements,
      --text-muted token undefined, SVG icon sizes inconsistent.
- [x] layouts/index.html — structure confirmed via live site.
      Source not read line by line. Mark as partially reviewed.
- [x] layouts/_default/about.html — renders correctly on live site.
      Mark as partially reviewed.
- [x] layouts/_default/under-construction.html — renders correctly
      on live /soul. Mark as partially reviewed.

Styles:
- [x] static/css/main.css — CSS variables used correctly, Phase 0
      design system applied, dark mode implemented. Issues found and
      fixed: duplicate .under-construction block, --text-muted not
      defined, inline style values moved to classes.

Scripts:
- [x] static/js/main.js — logic correct, no external calls, no data
      leakage. Issues found and fixed: no .catch() on clipboard
      promise, no null check on data-copy, var replaced with const.

Config:
- [x] config.toml — baseURL correct, no telemetry, no third-party
      theme. Issue: named config.toml not hugo.toml. Title capitalised
      — overridden correctly in baseof.html. To be corrected at Phase
      2 initialisation.

Version control:
- [x] .gitignore — all required exclusions present per protocol.md
      Section 6.5. .hugo_build.lock confirmed untracked via
      git ls-files.
- [x] Commit history — early commits violate lowercase present-tense
      format. One wip: commit left unresolved. Final commits follow
      protocol correctly.


**5. Protocol violations**

- Socratic phase: completed. Single outcome, audience, and scope
  defined before building. Held.
- Naming: N/A — portfolio identity is jaquesbody, not a project name.
- Tech stack defaults: respected. Inter deviation documented. No
  frameworks, no CDN, no external dependencies.
- Design principles: mostly held. Inline styles and inconsistent SVG
  sizes were violations of Section 4.3. Both fixed post-audit.
- Content before building: yes. All copy written and in project.md
  before templates were built.
- Git conventions: partially followed. Final commits correct. Early
  commits and unresolved wip: are violations.


**5a. Privacy and Security Review**

External requests:
- [x] No external font requests — fonts self-hosted — PASS
- [x] No analytics or tracking scripts — PASS
- [x] No external JS dependencies — PASS
- [x] No social embed scripts — PASS
- [x] All script and link tags confirmed local only — PASS
- [x] No preconnect or dns-prefetch to external domains — PASS

Data handling:
- [x] No external API calls in JS — PASS
- [x] No localStorage use — PASS
- [x] No cookies set — PASS
- [x] No form inputs — PASS

Meta and head:
- [x] No Open Graph tags — N/A, not required
- [x] Favicon served locally — PASS
- [x] No third-party meta tag scripts — PASS

Links:
- [x] All third-party links deliberate and visible — PASS
- [x] No silent redirects or tracking parameters — PASS

Hugo config:
- [x] No telemetry in config.toml — PASS
- [x] No third-party theme — PASS

Intentional trade-offs:
- Inter self-hosted via @font-face — justified, documented in CSS
  comment and protocol.md. No external request made.


**5b. Audit Feedback Loop**

Phase 1 is the first completed project. No prior audit to feed back
from. This audit initiates the feedback loop. All findings have
produced specific updates to protocol.md and soul-ai.md, committed
before this session closes.


**6. Required updates**

Updates to protocol.md:
- Section 6.2 — expanded pre-commit browser check to include dev
  tools verification of console errors, failed resource loads, and
  undefined CSS variables.
- Section 6.3 — added git status pre-commit check, git rm --cached
  guidance for previously tracked files, and hard rule that wip:
  commits must be resolved before a phase is marked complete.
- Section 6.5 — added note that .gitignore does not untrack already
  committed files, with git rm --cached and git ls-files guidance.
- Section 4a — added duplicate CSS block check to Styles checklist,
  added hugo.toml naming check to Config checklist.

Updates to soul-ai.md:
- Section 2 — added explicit requirement to flag missing .catch() on
  async promises, missing null/undefined checks on DOM attribute
  reads, and use of var where const or let is correct. These are
  mandatory output flags, not optional caveats.


**7. Summary**

A visually clean, privacy-sound first phase that shipped on time, but
with a pattern of accepting vibe-coded output without systematic
review — producing avoidable bugs, duplicate code, and protocol
violations that made it to production.