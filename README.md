# theFeathers/conv

> Code conventions for theFeathers projects.

## JavaScript

### Project structure

#### Libraries

```text
/lib-js

-- build.sh | build.js  # Build script
-- es5
 ⮡ -- lib-js.min.js    # Exports Babelified es5 ("main":)
   -- lib-js.js         # Optional unminified es5
-- es6
 ⮡ -- index.js         # Exports es6 code
-- index.js             # Entry point to code logic
-- lib
 ⮡ -- b-logic.js       # Contains modular business logic
-- modules
 ⮡ -- module-a.js      # Well contained, lib-agnostic module
-- package-lock.json
-- package.json
-- utils
 ⮡ -- index.js         # Exports all utils
    -- conv.js          # Does one simple task and returns
```