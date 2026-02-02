# Align Mockphine repo structure with Proxyman-style layout

This ExecPlan is a living document. The sections Progress, Surprises & Discoveries, Decision Log, and Outcomes & Retrospective must be kept up to date as work proceeds.

PLANS.md is not present in this repository at the time of writing, so this plan is the sole execution guide.

## Purpose / Big Picture

After this change, the Mockphine repository presents a public-facing structure that mirrors the Proxyman issue-tracker layout: a visible issue template folder, a screenshots folder, a root .gitignore, and a README that orients contributors and users. The release tooling continues to function, but the top-level structure is easier to scan, and issue filing is guided by templates. A maintainer can point users to the README for support guidance, while contributors can find screenshot assets and issue templates in predictable locations.

## Progress

- [x] (2026-02-01 18:20Z) Recorded current root layout and kept release tooling in place while adding Proxyman-style folders.
- [x] (2026-02-01 18:22Z) Added .github/ISSUE_TEMPLATE with minimal issue templates.
- [x] (2026-02-01 18:22Z) Added screenshots/ with a tracked placeholder so the folder exists in git.
- [x] (2026-02-01 18:23Z) Added a root .gitignore appropriate for this repo’s tooling.
- [x] (2026-02-01 18:24Z) Updated README.md to describe the new structure and how to file issues, while keeping release workflow notes intact.
- [ ] (2026-02-01 18:25Z) Validate GitHub issue templates are visible after pushing changes.

## Surprises & Discoveries

None yet.

## Decision Log

- Decision: Keep existing release tooling (package.json, scripts/, .github/workflows/release.yml, plans/) in place and add the Proxyman-style public-facing folders around it rather than moving or deleting tooling.
  Rationale: The release workflow depends on the current paths and this repo is already documented as release-only; adding the missing structure satisfies the “Proxyman-style” layout without breaking releases.
  Date: 2026-02-01 18:00Z

## Outcomes & Retrospective

Not started yet.

## Context and Orientation

The current repository root contains .github/workflows/release.yml for the release pipeline, package.json plus scripts/generate-latest-json.mjs for release metadata, plans/ for ExecPlans, and README.md describing release tooling. The Proxyman repository’s root layout (as observed on GitHub) contains .github/ISSUE_TEMPLATE, screenshots/, .gitignore, and README.md. This plan adds those public-facing folders and files to Mockphine while retaining the existing release pipeline and scripts.

## Plan of Work

Add a new .github/ISSUE_TEMPLATE directory and create three Markdown templates named 1-bug-report.md, 2-question.md, and 3-feature-request.md that capture required details for issues, questions, and feature requests. Add a screenshots/ directory and place a tracked placeholder file (such as screenshots/.gitkeep or screenshots/README.md) so the folder appears in the repository even before images are added. Create a root .gitignore that ignores OS files and Bun/Node outputs like .DS_Store, node_modules/, bun.lockb, and dist/. Update README.md with a short “Support & Issues” section that points users to the issue templates and a brief “Screenshots” note that assets live under screenshots/, while preserving the existing release workflow documentation.

## Concrete Steps

Work from the repository root /Users/cuongnguyen/Documents/github/Mockphine.

Create the issue template folder and files:

  mkdir -p .github/ISSUE_TEMPLATE
  cat > .github/ISSUE_TEMPLATE/1-bug-report.md <<'EOF'
  ---
  name: Bug report
  about: Report a problem or regression
  title: "[Bug] "
  labels: [bug]
  ---
  
  ## Summary
  
  ## Steps to reproduce
  1.
  2.
  3.
  
  ## Expected behavior
  
  ## Actual behavior
  
  ## Environment
  - OS:
  - App version:
  - Update channel (if applicable):
  
  ## Logs or screenshots
  EOF

  cat > .github/ISSUE_TEMPLATE/2-question.md <<'EOF'
  ---
  name: Question
  about: Ask a question about Mockphine releases or updates
  title: "[Question] "
  labels: [question]
  ---
  
  ## Question
  
  ## Context
  EOF

  cat > .github/ISSUE_TEMPLATE/3-feature-request.md <<'EOF'
  ---
  name: Feature request
  about: Suggest an improvement or new feature
  title: "[Feature] "
  labels: [enhancement]
  ---
  
  ## Problem to solve
  
  ## Proposed solution
  
  ## Alternatives considered
  
  ## Additional context
  EOF

Create the screenshots folder and placeholder:

  mkdir -p screenshots
  touch screenshots/.gitkeep

Add a root .gitignore (merge with existing if present):

  cat > .gitignore <<'EOF'
  .DS_Store
  node_modules/
  dist/
  bun.lockb
  .env
  .env.*
  .cache/
  EOF

Update README.md to include the new structure while preserving release content. Edit README.md and insert a short section near the top describing that this repo contains release tooling and issue tracking, add a “Support & Issues” section that points contributors to GitHub issues (and mentions the templates), and add a “Screenshots” note that assets live under screenshots/.

## Validation and Acceptance

Run the following from /Users/cuongnguyen/Documents/github/Mockphine and confirm the new structure is present:

  ls -a

The output should include .github, screenshots, .gitignore, README.md, and the existing release tooling files. Visit the repository’s Issues page on GitHub to confirm the three issue templates appear. The README should still document the release workflow and also mention how to open issues and where screenshots belong.

## Idempotence and Recovery

Creating the new folders and files is safe to repeat; re-running the commands overwrites template and .gitignore files. If you need to back out, remove the new files (.github/ISSUE_TEMPLATE/*.md, screenshots/.gitkeep, .gitignore edits) and restore README.md to its previous content.

## Artifacts and Notes

Expected root layout after changes (example):

  .github/
    ISSUE_TEMPLATE/
      1-bug-report.md
      2-question.md
      3-feature-request.md
    workflows/
      release.yml
  screenshots/
    .gitkeep
  .gitignore
  README.md
  package.json
  plans/
  scripts/

## Interfaces and Dependencies

No new external dependencies are required. GitHub issue templates are plain Markdown files placed in .github/ISSUE_TEMPLATE. The release workflow continues to depend on bun and scripts/generate-latest-json.mjs, so those paths must remain valid. The README should reference the issue templates and screenshots folder by their repository-relative paths.

Change Note (2026-02-01 18:00Z): Initial ExecPlan created to align Mockphine’s folder structure with Proxyman-style layout while preserving release tooling.
Change Note (2026-02-01 18:25Z): Updated progress to reflect completed folder additions and README edits; validation pending GitHub visibility.
