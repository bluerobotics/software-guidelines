# Style Guidelines

When contributing to projects owned by other entities, adhere to any guidelines set forth by those entities (eg. ardupilot). The style guidelines for projects owned by Blue Robotics is documented here.

## Code

- In any case, use a consistent style within a particular file or project. 
- Use braces and hanging indentation for all conditional and loop statements; no one-liners
- Use camelCase
 - Lead with lowercase for variables and methods (eg. `myMethod`)
 - Lead with uppercase for classes (eg. `MyClass`)
 - Private members should be prefixed with an underscore (eg. `_myPrivateVariable`)
- When naming files, variables, methods etc. avoid abbreviations and ambiguous/vague identifiers; be verbose to the point that it is totally clear (eg. minTemperature instead of minTemp, degreesC rather than degC, firmware instead of fw). There _may_ be exceptions for abbreviations that are *especially common and clear* like `min` and `max`. The point is to leave behind absolutely zero ambiguity and to increase readability and understanding, at the small price of a few extra characters.
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
- Use a consistent project structure for all projects
 - General project structure:
   - `src/` project source code
   - `lib/` submodules, libraries
   - `doc/` project documentation
   - `README.md` project homepage
   - `.gitignore`
   - `.travis.yml`
   - `.appveyor.yml`
 - Python package
 - Arduino library

## Language-specific
- c / c++
  - Use `()` instead of `(void)` for functions with no parameters
  - Do not add `;` after method definitions
- Python
  - Use python3
  - Use [typehints](https://www.python.org/dev/peps/pep-0484/)
  - Use [PEP8](https://www.python.org/dev/peps/pep-0008/) guidelines when they do not disagree with our own
- Javascript
  - Semicolons are required after every statement

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

- [google style guide](https://google.github.io/styleguide/cppguide.html)
