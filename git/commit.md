# Git commits

Git commits should be atomic, short, and understandable. The format should be as follows:

```txt
[action:scope] message:
long-description
```

---

#### `action` is one of:
- `fix`: fixed something
- `feat`: added a new feature
- `add`: added a file, not a large enough change to be a feature
- `rm`: removed a file or feature
- `refactor`: significant code changes without changing functionality
- `cleanup`: moved things around, not qualified enough to be a refactor
- `doc`: wrote or modified docs
- `ver`: modified versions
- `misc`: miscellaneous commit

---

#### `scope` is the name of the part you touched `[fix:user]`

scope is optional, and can be omitted in small applications if there isn't a lot of scopes to be concerned about

---

#### `message` is a short continuation of your action in given scope

Add `:` in the end if you add a long-desc below your message.

---

#### Examples:

* `[fix:user] could not find valid user`
* `[feat:utils] asyncHandler supports middleware compose`
* `[cleanup:tests] move tests into their own dirs`
