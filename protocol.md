Last updated 9th June 2026

protocol.md defines how jaquesbody works — process, standards, and workflow. It is a living document, updated as standards evolve and audits feed back improvements. Read alongside soul.md, which defines who jaquesbody is.

**Section 1 — Pre-Project Socratic Phase**

The purpose of this phase is to ensure the right problem is being solved before a single line of code is written. No implementation until this phase is complete.

**1.1 — Problem Definition**

- What problem does this solve?
- Who has this problem — me specifically, or a general audience?
- Is this problem already solved well elsewhere? If yes, what justifies building it?
- What does success look like for the user — what is the single outcome they experience?

> AI: Re-read soul.md at the start of this phase to ensure responses are calibrated to the user's epistemology, working style and communication preferences. This section is not a passive Q&A — challenge weak answers, present the strongest counterargument to the problem definition, and identify hidden assumptions. The user should have to defend their answers before proceeding to 1.2. Do not move forward until the problem definition is airtight.

**1.2 — Scope**

- What is the minimum version that delivers that outcome?
- What is explicitly out of scope for the first version?
- What am I tempted to add that I should resist?

**1.3 — Assumptions & Risks**

- What am I assuming to be true that I haven't verified?
- What is the most likely way this fails?
- What would make me abandon this project — and is that condition already present?

**1.4 — Green Light Criteria**

- Can I state the problem, the user, the outcome, and the minimum scope in four sentences or less?
- If no, the problem isn't defined well enough yet. Return to 1.1.

> AI: Do not proceed to implementation or make suggestions about tech stack, naming, or structure until all 1.1-1.3 questions have been answered and 1.4 is passed. If the user attempts to skip this phase, redirect them back to the unanswered questions.

**Section 2 — Naming Standards**

**2.1 — The Banner**

- jaquesbody is the identity, no separate studio name
- Quality and values come through in the work, not a brand wrapper
- All projects live under jaquesbody.github.io

**2.2 — What a Good App Name Is**

- One word, one or two syllables
- Human and understated — no hype, no corporate feel
- Implies the outcome for the user, never describes the feature set
- Evokes a feeling without over-explaining
- Stands alone as a product but doesn't jar when listed alongside other projects

**2.3 — What a Good App Name Is Not**

- A phrase or description
- Generic or app-store functional
- Pretending to be bigger than it is
- Trend-chasing or clever for its own sake

**2.4 — The Naming Process**

1. Define the user outcome in one sentence — not the feature set, the result
2. Identify the feeling that outcome produces
3. Find the word that implies that feeling without stating it
4. Stress test: does it jar with existing project names when listed together?
5. Trust simple and human over clever and abstract

**2.5 — Current Projects as Benchmark**

- Saved — relief, financial clarity
- Untold — reclaiming, digital self-determination
- Reach — merit-based connection, ideas over identity

> AI: Apply 2.4 as a process, not a checklist. Push back on names that violate 2.3. Use 2.5 as a consistency benchmark — any new name should sit alongside these three without jarring.

**Section 3 — Tech Stack Defaults**

**3.1 — Core Stack**

- SSG: Hugo v0.147.9 extended
- Languages: HTML, CSS, vanilla JavaScript
- Version Control: Git via CLI, GitHub
- Editor: VSCode
- OS: Linux VM (development), Android and desktop browsers (testing)
- Target platforms: All modern browsers, all screen sizes, all operating systems — mobile first, scale up
- Sync: Syncthing
- Design: Inkscape (brand assets, SVGs)
- Local AI: Ollama via Raspberry Pi (pending)
- Typography: Inter (self-hosted via @font-face, woff2 format)
- Weights in use: 400 (regular), 700 (bold)
- Files live at: static/fonts/ — not committed to repo (binary files)
- Download from: https://github.com/rsms/inter/releases
- Deviation from system font stack default — justified: open-source (OFL licence), no external request, no CDN, no privacy compromise, consistent geometric aesthetic across all projects. Document this deviation in CSS comments.

**3.2 — Hosting & Deployment**

- All projects published to jaquesbody.github.io
- Hugo builds to public/ directory
- Deployed via Git commit and push — no CI/CD pipeline currently
- Domain: GitHub Pages only for now

**3.3 — Hugo Conventions**

- Content in content/ as .md files with YAML frontmatter
- Templates in layouts/ and layouts/_default/
- Static assets in static/css/ and static/js/
- Base template: layouts/_default/baseof.html
- Homepage template: layouts/index.html

**3.4 — Principles**

- Free and open-source tools only, unless no viable alternative exists
- No frameworks unless vanilla JS genuinely cannot do the job
- No dependencies that phone home or compromise user privacy
- Local-first wherever possible

> AI: Default to this stack for all technical recommendations. Do not suggest frameworks, libraries, or paid tools unless the user's requirement cannot be met within it. If a deviation is genuinely justified, flag it explicitly and explain why before suggesting it.

**Section 4 — Design Principles**

**4.1 — The Standard**

- First impression must impress — quality is felt before it is understood
- Every design decision must have a reason — no arbitrary choices
- Consistency across all projects takes priority over individual polish
- If in doubt, remove it — simplicity is harder than complexity

**4.2 — User Experience**

- The primary test: can a non-technical user navigate it without instruction?
- Intuitive over clever — never sacrifice usability for aesthetics
- Mobile first — design for the smallest screen, scale up
- Every interaction should feel considered, never accidental
- Responsive across all screen sizes and operating systems — no platform assumptions

**4.3 — Visual Consistency**

- CSS variables for all colours, spacing, and typography — defined once in :root
- Dark mode support on every project — system preference respected by default
- Typography: system font stack unless a specific font is self-hosted
- No decorative elements that don't serve the content
- Design system: monochrome base (black, charcoal, mid-grey, light grey, white) shared across all projects
- Identity accent: #0EDA29 used exclusively on jaquesbody.github.io as the portfolio identity colour
- Per-project accent: one colour per project, assigned at project start, applied via a single --accent CSS variable — used for interactive elements, highlights, and mood
- The monochrome base and --accent variable structure must be consistent across all projects — only the accent value changes

**4.4 — Content Hierarchy**

- One primary action per page — the user should never be unsure what to do next
- Headlines do the heavy lifting — if the headline needs explaining, rewrite it
- White space is not empty space — it is a design element

**4.5 — What to Avoid**

- Animations for their own sake
- Colour palettes that haven't been deliberately chosen
- Inconsistent spacing, font sizes, or border radii across components
- Any UI pattern that would confuse a first-time visitor
- Emojis or icon fonts — use SVGs only

> AI: Flag any technical suggestion that would compromise these principles. If the user proposes a design decision that violates 4.1-4.4, challenge it before implementing. Consistency across projects is non-negotiable — check against existing projects before introducing new patterns.

**Section 5 — Content Phase**

**5.1 — Purpose**

Content must be defined before any template, layout or structure is built. Building the container before knowing what goes in it is the primary cause of rework.

**5.2 — Content Audit**

Before writing a single line of code, answer:
- What are the distinct types of content this project contains?
- What is the hierarchy — what is most important, what is secondary?
- What does the user need to read/see/do first, second, third?
- What content is static (rarely changes) vs dynamic (frequently updated)?
- What content lives in markdown vs what is structural (belongs in templates)?

**5.3 — Content Structure**

- Map content types to Hugo content directories before creating any files
- Define frontmatter fields for each content type before writing any markdown
- Every piece of content must have a clear home — no orphaned pages
- URL structure follows content/ directory structure — name directories deliberately

**5.4 — Content Rules**

- Write for the user outcome, not the feature set
- One idea per paragraph
- Headlines must stand alone — a user scanning only headlines should understand the page
- No placeholder content in commits — if it isn't written, it isn't ready to ship

**5.5 — Content vs Template Boundary**

- If it changes per page — it's content, it lives in markdown
- If it's the same across multiple pages — it's structural, it lives in a template
- If you're putting words directly into a template, stop and question why

> AI: Before proceeding to Section 6, explicitly verify the following with the user: content types are defined, hierarchy is established, frontmatter fields are named, and no templates have been created yet. If any templates already exist, audit whether content was defined before they were built — if not, flag it as a protocol violation and identify what needs to be undone. Do not proceed until all five questions in 5.2 have been answered.

**Section 6 — Workflow**

**6.1 — Development Environment**

- All development on Linux VM
- Hugo dev server runs on localhost:1313 — always preview before committing
- VSCode for editing, CLI for Git operations

**6.2 — Hugo Build Process**

1. hugo server — local preview, live reload
2. Verify in browser before any commit
3. hugo — builds static files to public/
4. Commit and push to deploy
- Verify in browser before any commit. This means: check the rendered output visually AND open browser dev tools to confirm no console errors, no failed resource loads, and no undefined CSS variables. A visual check is not a code review.

**6.3 — Git Commit Strategy**

- Commit immediately after each discrete change — don't accumulate
- Run git diff before every git add to see exactly what's changed
- Stage specific files where possible rather than git add .
- Commit messages are lowercase, present tense, specific:
    - add dns section to untold content
    - fix typo in privacy-guide.md
    - update nav colour in main.css
- If a session ends mid-task, prefix the commit message with wip: so context isn't lost on next session
- Before any commit, run `git status` to check for tracked files that should not be committed. If a file appears that is also listed in .gitignore, it was tracked before .gitignore was configured — run `git rm --cached <filename>` to untrack it, then commit the removal explicitly.
- `wip:` commits must be resolved before a phase is marked complete. A phase with an unresolved `wip:` in its commit history is not complete.
- Never commit:
    - Placeholder content — if it isn't real, it isn't ready
    - Build artefacts — public/ and resources/ are auto-generated by Hugo
    - Binary files or installer packages — if you can't read it in VSCode, it probably doesn't belong
    - API keys or personal data

**6.4 — File Naming Conventions**

- All filenames lowercase, hyphens not underscores, no spaces ever
- Content files named to match their intended URL slug
- CSS and JS files named by function: main.css, main.js

**6.5 — .gitignore Defaults**

Always include:
    # Hugo build output
    public/
    resources/

    # Hugo lock file
    .hugo_build.lock

    # Installer packages
    *.deb
    *.exe

    # OS files
    .DS_Store
    Thumbs.db

- Adding a file to .gitignore does not untrack it if it was already committed. Use `git rm --cached <filename>` to remove it from tracking without deleting it locally. Verify with `git ls-files` that prohibited files are not tracked.

**6.6 — Session Workflow**

Given you work in short evening bursts:
- Start each session by reviewing the last commit message — reorient before building
- Define one specific task before opening any file
- Complete and commit that task before starting another
- If a session ends mid-task, commit a wip: prefixed message so context isn't lost

> AI: Enforce one task per session where possible. If the user starts scope-creeping into a second task mid-session, flag it and recommend completing and committing the current task first. Remind the user to preview in Hugo dev server before every commit.

**Section 7 — AI Assistant Usage**

**7.1 — Purpose**

AI assistants are a tool for thinking, building and reviewing — not a replacement for understanding. Never accept output blindly. If you can't explain what the code does, you don't own it yet.

**7.2 — Session Setup**

At the start of every AI session, feed in the following in order:
1. soul.md — who you are, communication preferences, values
2. protocol.md — how you work, standards, process
3. project.md — current project specifics

Without these, the AI is working blind and will default to generic responses that don't fit your stack, style or thinking.

State every task in this format: current state -> specific task -> desired outcome. Vague requests will be pushed back on before any work begins.

> AI: Before proceeding with any task, confirm the correct documents have been provided for the inferred session type as defined in soul.md Section 7. If any required documents are missing, stop and request them explicitly before continuing. Do not attempt to work from memory of previous sessions or make assumptions about the user's preferences, stack or current project. If a session escalates in scope, flag it, state what documents are now needed, and request them before continuing.

**7.3 — When to Use AI**

- Socratic phase — thinking through problems, challenging assumptions
- Naming — applying Section 2 process
- Code review — catching bugs, bad patterns, security issues
- Explaining concepts — understanding the why, not just the what
- Drafting content — first pass only, always rewrite in your own voice
- Debugging — narrowing down the problem, not just accepting the fix

**7.4 — When Not to Use AI**

- As a shortcut past the Socratic phase
- To make decisions that belong to you — vision, values, direction
- To generate code you paste without reading
- As a validator — if you're looking for approval rather than critique, that's a flag

**7.5 — How to Challenge AI Output**

- If an answer feels wrong, push back with your reasoning
- The AI should not capitulate without new evidence or a better argument
- If the AI agrees with everything you say, it's not being useful
- If the AI hasn't challenged at least one assumption in a Socratic phase, the phase isn't complete

**7.6 — Model Limitations**

- AI has a training cutoff — verify anything time-sensitive independently
- AI can be confidently wrong — cross-reference technical claims on anything critical
- Long conversations lose early context — re-feed soul.md and project.md if a session runs long or feels like the AI has lost the thread

> AI: You are a thinking partner, not an order taker. Consult soul.md at the start of every session. Apply protocol.md throughout. Push back when the user is wrong. Flag when context appears to have been lost and request re-feeding of relevant documents. Never generate code the user hasn't asked to understand.

**Section 8 — Audit Trigger**

**8.1 — Purpose**

Every completed project gets a brutal, honest post-mortem. The audit exists to improve future projects, not to validate past ones. Uncomfortable findings are the most valuable ones.

**8.2 — When to Trigger an Audit**

- A project reaches version complete: the Section 1.2 minimum scope is fully implemented, the project is publicly deployed, and a non-technical user could complete the primary action without assistance
- A project is abandoned — understanding why is as valuable as shipping
- A significant refactor is completed
- Something broke in production and you don't fully understand why

**8.3 — What audit.md Covers**

- Did the project pass the Section 1 Socratic phase properly — or was it skipped/rushed?
- Was the naming process followed?
- Were tech stack defaults respected — if not, was the deviation justified?
- Did design principles hold throughout?
- Was content defined before building?
- Were Git conventions followed?
- What caused the most rework and why?
- What would you do differently from the first decision?
- What was genuinely good and should be repeated?

**8.4 — Rules**

- No softening — if something was poor, say so directly
- No blame outside yourself — tooling, time pressure, and complexity are not excuses
- Every finding must produce a specific update to protocol.md or soul.md
- An audit with no protocol updates is an audit that wasn't honest enough

**8.5 — Audit Output Format**

- What went well
- What went wrong
- What was the root cause of each failure
- Specific changes to protocol.md as a result
- Specific changes to soul.md as a result
- One sentence summary of the project's overall quality
- audit.md is committed to the project repo after the session closes. Commit message: "add audit.md — phase [n] post-mortem"

> AI: When an audit is triggered, apply maximum critical scrutiny. Do not soften findings to protect the user's confidence. Every failure identified must be traced to a root cause and linked to a specific protocol update. If the user attempts to rationalise a failure rather than learn from it, challenge them. The audit is only complete when 8.5 is fully populated and protocol.md has been updated.

**Section 9 — Agentic Operations**

**9.1 — Purpose**

Agentic operations extend the AI beyond conversation into live browsing and research. They are triggered automatically at defined workflow points. All agentic operations are read-only unless explicit write authorisation is given in that session. The commit remains a human checkpoint — AI never commits on your behalf.

**9.2 — Permitted Operations**

- Live web browsing — reading pages, repos, and search results
- Navigating to provided URLs including GitHub repos and live deployed sites
- Searching for existing solutions, name conflicts, and associations
- Reviewing live sites against protocol.