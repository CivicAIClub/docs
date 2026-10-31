# Civic AI Club docs

This repo holds club-wide documentation for the Civic AI Club at Pomfret School. Project code lives in separate case repos; `developer-onboarding.md` is the beginner Git and GitHub guide.

## Beginner quick start

Full guide: https://github.com/CivicAIClub/docs/blob/main/developer-onboarding.md

1. First time: check Git with `git --version`, set your Git name and GitHub email, accept the club invite, and sign in with GitHub Desktop or `gh auth login`. Clone only your project's repo, open its folder, and read its README setup steps.
2. Start each work session from the latest main, then make a branch:

```sh
git checkout main
git pull origin main
git checkout -b chore/short-description
# Make and check your changes before continuing.
git status
git add .
git commit -m "Describe your change"
git push --set-upstream origin chore/short-description
```

Use `feature/`, `fix/`, or `chore/` as appropriate, with lowercase names and hyphens. Commit small working pieces; do not edit or push main directly.
3. Open a PR on GitHub, fill in the template, and get someone else's approval and passing checks where CI exists. Push review fixes to the same branch. After it is merged, pull main again before starting another branch.
4. If stuck, ask in the case chat, then Keke, then Luke or Cayden. Ask before doing anything drastic.

## Documentation rules

- Use plain, step-by-step English for high school developers learning to work together. Keep the guide's "✅ You're done with this step when" checks.
- Keep `developer-onboarding.md` accurate: branch prefixes are `feature/`, `fix/`, or `chore/`, never `case-x/`; every repo requires a PR with one approval; Cursor rules are committed under `.cursor/rules/`; secrets never go in Git.
- This repo's rule specifically requires `chore/<description>` branches for documentation changes, so the daily loop above uses `chore/`.
- Project code belongs in each project's repo, including `case-a-clc-workflow`, `case-b-music-studio`, `case-c-dei-timeline`, and `case-d-roster-export`.
- The old `Civic-AI-Github-Repository` monorepo is archived. Never point readers at it.
- When a repo, team member, or client changes, update the guide's Repositories table and the org profile README in `CivicAIClub/.github`.
- For Git, branching, PR, or merge-conflict questions, use the full onboarding guide linked above.
- Never add Co-authored-by, Generated with, Made-with, Claude-Session or any other AI attribution line to a commit message or pull request description. When squash merging, delete any such lines GitHub puts in the merge message.

## Setup and checks

Read `README.md` and `developer-onboarding.md`. The README gives no app setup or run commands; do not invent them for this documentation repo.

## Sources

- `README.md`
- `.cursor/rules/civic-ai-docs.mdc`
- `.cursor/rules/commit-messages.mdc`
- `developer-onboarding.md` (canonical guide; quick start based on its fetched source)
