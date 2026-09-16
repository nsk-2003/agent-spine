---
name: implement
description: Implement a piece of work based on a spec or set of tickets.
origin: https://github.com/mattpocock/skills/tree/main/skills/engineering/implement
author:
    - mattpocock
license: MIT
---
Implement the work described by the user in the spec or tickets.

## Process

1. **Read the spec or ticket** fully before writing any code. Understand the acceptance criteria.

2. **Write tests first.** Use /tdd where possible, at pre-agreed seams. Tests should verify external behavior, not implementation details.

3. **Implement the code** to make the tests pass. Follow the project's working rules in `.agents/workingrules.md`.

4. **Update documentation:**
   - Add entries to `docs/design/sourcemap.md` for every new source file.
   - Update `docs/design/packagedesign.md` if the package structure changed.
   - Add Purpose comments at the top of every new file.

5. **Run typechecking** regularly, single test files regularly, and the full test suite once at the end.

6. **Once done**, use /code-review to review the work.

7. **Commit your work** to the current branch.
