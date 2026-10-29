
# Git Commit Style

    Code: conv/git-commits
    Version: 3.0.0
    Author: Muthu Kumar <muthukumar@thefeathers.in>
    Org: Feathers Studio

## 1. Specification

Version 3.0.0 of `conv/git-commits` extends [Conventional Commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) with the following additions.

### 1.1. Format

A commit message MUST follow this structure:

    <type>[optional scope]: <description>[:]

    [optional body]

    [optional trailers]

The commit description, body, and trailers MUST be separated by a single empty line.

The trailing colon in the description MUST be present if a body follows. It MAY be omitted if the description is followed only by trailers or if no further content follows.

The trailing colon explicitly marks the description as introducing a body, making the message structure easier to recognise.

### 1.2. Description

The commit description MUST use the present tense and MUST NOT use the imperative mood.

This convention treats the commit message as a description of what the commit does, rather than an instruction for what it should do.

For example, `feat: adds validation` is valid, whereas `feat: add validation` and `feat: added validation` are not.

The description SHOULD be concise and clearly describe the change.

### 1.3. Body

The body MAY provide additional context, reasoning, or details about the change.

The present-tense and non-imperative requirements for the description DO NOT apply to the body. The body SHOULD use natural language appropriate to its purpose.

### 1.4. Commit Types

One of the following recommended commit types SHOULD be used:

- `feat` — adds a new feature
- `fix` — fixes a bug
- `refactor` — changes code without adding a feature or fixing a bug
- `chore` — makes miscellaneous repository changes
- `build` — changes the build process or CI pipeline
- `docs` — changes documentation
- `perf` — improves performance
- `test` — adds or updates tests
- `version` — creates a new version tag; the description MUST be a semantic version
- `merge` — creates a merge commit; the scope MUST reference the merge request or pull request
- `revert` — reverts a previous commit; the scope MUST be the hash of the original commit, and the description MUST match the original commit's description

### 1.5. Trailers

One or more of the following recommended trailers MAY be used:

- `Fixes: <issue-number-or-ticket-reference>`
- `Co-authored-by: <name> <<email>>`
- `Signed-off-by: <name> <<email>>`
- `BREAKING-CHANGE:`
- `TODO:` — indicates that further commits are required to complete the change

Trailers MUST follow the body, if present, and MUST be separated from it by a single empty line. If no body is present, trailers MUST be separated from the description by a single empty line.

## 2. Examples

### 2.1. Description Only

    feat: adds validation

### 2.2. Description and Body

    chore: removes deprecate() calls:

    There is no need to log deprecation warnings to the console
    anymore. Users have been warned via release notes, and the
    v5 breaking change will be minor.

### 2.3. Description and Trailers

    feat: resists session racing using refcounting

    Fixes: #1372

### 2.4. Description, Body, and Trailers

    fix: prevents duplicate session creation:

    Concurrent requests could create multiple sessions for the
    same user. The new locking mechanism prevents this race.

    Fixes: #1372
