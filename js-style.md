# JavaScript style

#### Code: `conv/js-style`

#### Version: 1.0.0

## Specification

This is a light specification for formatting and styling JavaScript and TypeScript code. We hope to cover only the minimum for sensible formatting, and let tools such as `Prettier` and `deno fmt` handle the rest.

-   MUST use <kbd>Tab ⭾</kbd> to indent lines of code.
-   MUST use semicolons to terminate statements. Do not rely on ASI to infer semicolons.
-   MUST use trailing comma for multi-line objects, arrays, and function calls.
-   SHOULD use double quotes for strings by default, unless the string contains double quotes.
-   SHOULD prefer template literals over single quotes when necessary.

A [`.prettierrc`](./assets/.prettierrc) is provided that implements these requirements.
