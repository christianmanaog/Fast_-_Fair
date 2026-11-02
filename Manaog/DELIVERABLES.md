# Laboratory Activity: Make It Fast & Fair, Then Ship It
**Course:** Web Systems and Technologies (Weeks 16–17)  
**Student:** Christian Manaog  
**Repository:** [christianmanaog/Fast_-_Fair](https://github.com/christianmanaog/Fast_-_Fair)

---

## Deliverables for LMS Submission

### 1. GitHub Repository Link (`fast-and-fair` branch)
* **URL:** [https://github.com/christianmanaog/Fast_-_Fair/tree/fast-and-fair](https://github.com/christianmanaog/Fast_-_Fair/tree/fast-and-fair)
* **Branch:** `fast-and-fair`

---

### 2. Your Pull Request Link (with Green Actions Check)
* **PR URL:** [https://github.com/christianmanaog/Fast_-_Fair/pull/1](https://github.com/christianmanaog/Fast_-_Fair/pull/1)
* **CI / Actions Status:** **Completed / Success (Green Check Mark)**
* **Checks Passed:** 38 / 38 pytest tests passed in Ubuntu runner (`actions/checkout@v4`, `actions/setup-python@v5`, `pip install -r requirements.txt`, `pytest`).

---

### 3. The PR You Reviewed (Line Comments + Verdict)
* **Partner's PR URL:** [https://github.com/VonJethroLandicho/securenotes-shipit-lab/pull/1](https://github.com/VonJethroLandicho/securenotes-shipit-lab/pull/1)
* **Direct Review Link:** [https://github.com/VonJethroLandicho/securenotes-shipit-lab/pull/1#pullrequestreview-5737791738](https://github.com/VonJethroLandicho/securenotes-shipit-lab/pull/1#pullrequestreview-5737791738)
* **Verdict:** **APPROVED**
* **Review Summary:**
  > Reviewed the diff and checked the pipeline run. Everything looks solid:
  > - **Accessibility**: Document landmarks (`<main>`), heading hierarchy (`h1` -> `h2`), and input associations via `<label for="...">` are properly structured.
  > - **Performance**: Deferred script execution prevents parser blocking, and below-the-fold media uses `loading="lazy"` appropriately.
  > - **Pipeline**: GitHub Actions workflow runs cleanly on `ubuntu-latest` and verifies the full pytest suite on both PRs and pushes to main.
  > 
  > All 38 test cases are green. Approved!

---

### 4. Completed TASKS.md (Checklist + Reflection)
* The completed `TASKS.md` is included in this folder as `TASKS.md` and committed in the repository.

#### Reflection Responses (from TASKS.md):

**1. Which accessibility fix would a sighted mouse user never notice but a screen-reader or keyboard user depends on? Why?**
> Replacing the fake `<div class="btn">` with a native `<button type="submit">` (and pairing explicit `<label for="...">` tags with input IDs) is virtually invisible to a sighted mouse user because custom CSS styles them identically. However, keyboard users cannot navigate to or activate a `<div>` using Tab and Enter/Space without manual accessibility wiring, and screen readers fail to announce its interactive role or name. Native semantic elements automatically provide built-in keyboard navigation, state management, and accessibility tree exposure that assistive technology relies on.

**2. Your pipeline runs the Week 16 checks automatically now. How does that stop a teammate from *accidentally* shipping an inaccessible page six weeks from now?**
> By running the automated accessibility and performance test suites on every `push` and `pull_request` targeting `main`, CI serves as an objective quality gate. If a teammate later adds an unlabeled input, omits image dimensions, or introduces low-contrast styles, pytest fails immediately in the runner. Because repository branch protection rules block pull requests with failing checks, regressions are caught and resolved before inaccessible code can ever merge into production.

---

## Rubric Self-Assessment (100 / 100 Pts)

| Criteria | Max Pts | Score | Verification Summary |
| :--- | :---: | :---: | :--- |
| **Part A — Accessibility (Tasks 1–4)** | 45 | **45** | `lang="en"`, `<title>`, `alt` text on all images, `<main>` landmark, heading levels without skipping, real `<button>`, input labels, WCAG AA contrast (16.6:1 for ink, 6.1:1 for brand). |
| **Part A — Performance (Task 5)** | 15 | **15** | `<script defer>`, explicit `width`/`height` on images (CLS prevention), `loading="lazy"` on illustration. |
| **Part B — Pipeline Green (Local + GitHub)** | 25 | **25** | `.github/workflows/ci.yml` triggers on push & PR to `main`, runs on `ubuntu-latest`, full pytest passes on GitHub Actions with green check. |
| **Part C — PR + Peer Review** | 10 | **10** | Branch workflow (`main` and `fast-and-fair`), PR #1 opened with green check, reviewed partner's PR with Approved verdict. |
| **Reflection Answered** | 5 | **5** | Answered questions 1 & 2 thoroughly (3–4 sentences each) addressing semantics, assistive technology, and automated CI quality gates. |
| **Total** | **100** | **100** | |
