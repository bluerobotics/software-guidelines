# Embedded Development Guidelines

These guidelines apply to embedded and safety-critical firmware projects. Follow project-
specific rules first (e.g., ArduPilot and JSF style guide), then apply the rules below for any gaps.
When these rules conflict with a project standard, the project standard wins.

## General

- Follow the project code style and keep it consistent within each file.
- Prefer small, focused functions over long procedural blocks.
- Prefer compile-time checksm add run-time checks for safety-critical paths.
- Encapsulate low-level or hardware-specific code behind clear interfaces.
- Do not add unused or commented-out code unless it is justified and documented.

## Core constraints (JSF AV-inspired)

- Keep functions under 200 logical source lines.
- Keep cyclomatic complexity at or below 20 (exceptions only for large switch statements).
- Do not use self-modifying code. (Up to discussion)
- Use ISO/IEC 14882:2017-compliant C++ (C++17) or newer, do not rely on compiler extensions.
- When possible, pass the compiler flag to disable extensions (e.g., `-fno-gnu-extensions` for GCC/Clang).
- Use only the basic C++ source character set, do not use trigraphs, digraphs, multibyte
  characters, or wide string literals.

## Preprocessor rules

- Only use `#pragma once` and `#include`
- Do not use `#define` for inline macros or constants, use `inline`, `const`, `constexpr`, or `consteval` instead.
- `#include` only header files (template implementations may be included by headers).

## Header and implementation structure

- `.h` for headers, `.cpp` for implementations.
- Headers contain declarations only, no non-const data or function definitions.
  - Exceptions: inline functions and templates.
- Each `.cpp` includes the headers that define all inline functions, types, and templates it uses.
- Header files should include only what they need, keep implementation-only includes in `.cpp`.

## Style and naming

- Avoid tabs, indent consistently (use 2 or four spaces, be consistent with the project).
- Use braces for all control statements.
- Braces for blocks on their own lines and aligned.
- No spaces around `.` or `->`, and no spaces around unary operators.
- Naming rules follow the project standard. If none is defined, use:
  - `lower_snake_case` for functions and variables
  - `UpperCamel_Case` for classes, structs, enums, and typedefs (e.g., `AP_Compass`)
  - lowercase constants and enumerators
  - uppercase acronyms inside identifiers (e.g., `GCS_MAVLink`)
  - use underscore for private properties

## Class design

- Use `struct` for plain data, `class` for invariants and encapsulation.
- Keep data members private, avoid public/protected data in classes.
- Declare member functions as `const` by default.
- Use `constexpr` or `consteval` for functions and variables that can be evaluated at compile time.
- Do not call virtual functions from constructors or destructors.
- Use member initializer lists for non-static members.
- Declare copy/assignment when owning pointers or nontrivial destructors.
- Base classes with virtual functions must have virtual destructors.

## Documentation

- Document units in names or comments for physical quantities.
- Prefer doxygen-style comments for C++ projects.

## Embedded-specific constraints

- Avoid the C++ standard library (`std::vector`, `std::string`, `std::unordered_map`)
  unless the platform and toolchain explicitly support it and memory costs are measured.
- Prefer fixed-size arrays, if dynamic containers are needed, use project-approved
  alternatives.
- Avoid bit fields, use plain booleans.
- Remove dead code, do not comment out unused code.
- Prefer multiplication over division for unit conversions.
- Use `constexpr` for compile-time constants and lookup tables, use `consteval` (C++20+)
  when a value must be evaluated at compile time.

## Testing and verification

- Tests must exercise safety-critical paths and any new hardware interactions.
- Add logging or assertions that can be compiled out for production builds.
- Ensure CI covers at least one supported target and simulator when available.

## Portability and build

- Target multiple embedded platforms when feasible, avoid vendor-locked toolchains.
- Make dependencies and build steps explicit and reproducible.

## References

- JSF Air Vehicle C++ Coding Standards (Stroustrup): https://www.stroustrup.com/JSF-AV-rules.pdf
- ArduPilot Style Guide: https://ardupilot.org/dev/docs/style-guide.html
