# Style Guidelines

When contributing to projects owned by other entities, adhere to any guidelines set forth by those entities (eg. ArduPilot). The style guidelines for projects owned by Blue Robotics is documented here.

## Code

- In any case, use a consistent style within a particular file or project.
- Use braces and hanging indentation for all conditional and loop statements; no one-liners
- Use camelCase
 - Lead with lowercase for variables and methods (eg. `myMethod`)
 - Lead with uppercase for classes (eg. `MyClass`)
 - Private members should be prefixed with an underscore (eg. `_myPrivateVariable`)
- When naming files, variables, methods etc. avoid abbreviations and ambiguous/vague identifiers; be verbose to the point that it is totally clear (eg. minTemperature instead of minTemp, degreesC rather than degC, firmware instead of fw). There _may_ be exceptions for abbreviations that are *especially common and clear* like `min` and `max`. The point is to leave behind absolutely zero ambiguity and to increase readability and understanding, at the small price of a few extra characters.

### Getter and Setter Naming (Qt Style)

**Getters:** Do NOT use the `get` prefix. Use the bare property name directly.
```cpp
// Bad
std::string getName();
int getWidth();

// Good
std::string name();
int width();
```

**Setters:** Use the `set` prefix.
```cpp
void setName(const std::string& name);
void setWidth(int width);
```

**Boolean getters** follow specific rules:

| Type | Convention | Examples |
|------|------------|----------|
| Adjectives | `is` prefix | `isChecked()`, `isEmpty()`, `isMovingEnabled()` |
| Adjectives on plural nouns | No prefix | `scrollBarsEnabled()` (not `areScrollBarsEnabled()`) |
| Verbs | No prefix, no third person `-s` | `acceptDrops()` (not `acceptsDrops()`) |
| Nouns | Generally no prefix | `autoCompletion()`, `boundaryChecking()` |
| Misleading without prefix | `is` prefix | `isOpenGLAvailable()`, `isDialog()` |

**Setter names** are derived from getters by removing any `is` prefix and adding `set`:
- `isChecked()` → `setChecked()`
- `scrollBarsEnabled()` → `setScrollBarsEnabled()`

- Use [astyle](http://astyle.sourceforge.net/astyle.html)!
    - Use "One True Brace Style" (--style=otbs)
- Regardless of the language, always use double quotes for strings, single quotes for characters
- Maximum line length allowed in any source file is 120 characters

## Whitespace
- Spaces only. Everywhere except makefiles. No tabs.
- Apply whitespace liberally for the sake of readability
- No trailing whitespace. Anywhere. Ever.
- A single newline should exist at the end of every file

## Projects

- Use all lower case and `-` in place of spaces for directory and file names (eg. `src/`, `icon-blue.png`)

## Language-specific
- c / c++
  - Use `()` instead of `(void)` for functions with no parameters
  - Do not add `;` after method definitions
- Python
  - Use Python 3.11+
  - Use [typehints](https://www.python.org/dev/peps/pep-0484/)
  - Use [PEP8](https://www.python.org/dev/peps/pep-0008/) guidelines when they do not disagree with our own
  - Use `uv` as package manager, `black` for formatting, `isort` for imports, `ruff` for linting, `mypy` for type checking
  - Sort dependencies alphabetically in `pyproject.toml`
  - Use async programming with FastAPI, asyncio, aiohttp for I/O-bound operations
- TypeScript / Vue 3
  - Use TypeScript over JavaScript for type safety
  - Use Vue 3 Composition API with `<script setup>` syntax
  - Enable strict mode in `tsconfig.json`
  - Use explicit type annotations for function parameters and return types
  - Prefer `interface` over `type` for object shapes
  - Use `ref()` and `reactive()` for reactive state
  - Use `yarn` over `npm` for package management
  - No semicolons (enforced by ESLint)
  - Use `simple-import-sort` for alphabetically sorted imports
  - Prefer function declarations over function expressions
  - Use optional chaining (`?.`) when possible
  - One component per `.vue` file
  - Use Vuetify theme colors (`primary`, `success`, etc.) instead of hardcoded colors
  - Clear intervals/timeouts in `onUnmounted()` or `beforeDestroy()`

## IDEs
Here you can find some nice configurations to avoid style problems.
### Visual Studio Code (Code)

#### Settings
Style configuration for *code*:
```json
{
    "editor.renderControlCharacters": true,
    "editor.renderWhitespace": "all",
    "editor.rulers": [120],
    "files.insertFinalNewline": true,
    "files.trimFinalNewlines": true,
    "files.trimTrailingWhitespace": true
}
```
- `renderControlCharacters` and `renderWhitespace` helps to avoid multiple whitespaces and unnecessary invisible caracters.
- `rulers` marks the column in the editor to avoid exceeding 120 charcter line width
- `insertFinalNewLines` will add an empty line in the end of the file.
- `trimFinalNewLines` will remove any unnecessary empty lines in the end of the file.
- `trimTrailingWhitespace` remove trailing spaces in file, **this is the most important one**.

## Reference

- [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
- [Qt API Design Principles](https://wiki.qt.io/API_Design_Principles)
- [Kate Gregory - Naming is Hard: Let's Do Better (CppCon 2019)](https://www.youtube.com/watch?v=MBRoCdtZOYg)
- [Vue 3 Style Guide](https://vuejs.org/style-guide/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/)
