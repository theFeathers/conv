# Git Commit Style

```
Code: conv/git-commits
Version: 2.0.0
Author: Muthu Kumar <muthukumar@thefeathers.in>
Org: Feathers Studio
```

## Specification

Version 2.0.0 of `conv/git-commits` extends [Conventional Commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0) with the following additions:

-   Commit description and body MUST be in the present tense. `"feat: implements new parser"`, not imperative such as `"implement"`, or `"implemented"`.

-   If the commit has an optional body, the description MUST end with a colon. This MAY be ignored if the description is only followed by footers.

-   Commit description, body, and trailers MUST be separated by a single empty line.

-   One of the recommended commit types SHOULD be used:

    -   `feat` — added new feature
    -   `fix` — fixed a bug
    -   `refactor` — code change that is neither a feature nor a fix
    -   `chore` — miscellaneous changes to the repo
    -   `build` — changes to build process or CI pipeline
    -   `docs` — changes to documentation
    -   `perf` — code change to improve performance
    -   `test` — tests added or updated
    -   `version` — new version tag, description MUST be semver
    -   `merge` — merge commit, scope MUST be a reference to the merge request
    -   `revert` — scope MUST be a hash of the original commit; description MUST be the commit message of the commit being reverted

-   One or more of the recommended trailers MAY be used:
    -   `Fixes: <issue-number-or-ticket-reference>`
    -   `Co-authored-by: <name> <<email>>`
    -   `Signed-off-by: <name> <<email>>`
    -   `BREAKING-CHANGE:`
    -   `TODO:` — further commits are required towards this change

## Format

The commit message MUST be structured as one of the following options:

```text
<type>[optional scope]: <description>[:]
<empty-line>
[optional body]
<empty-line>
[optional trailers]
```

## Examples

```
feat: add validation
```

```
fix: invalidate emotion cache
```

```
chore: remove deprecate() calls:

No need to log deprecation warnings to console anymore.
Users have been warned via release-notes, and v5 breaking
change will be minor.
```

```
feat: resist session racing using refcounting

Closes: #1372
```
