# Code Guidelines

This guideline aims to provide useful answers about our software standards and concepts, allowing many people to use and collaborate with our software development. It helps to avoid accidents,

This document can help with:
- Technical specifications
- Tips to allow easier and maintainable code
- Performance improvements
- Shipping methods
- And etc.

When expanding or updating these guidelines, take in mind that:
- It should be comprehensive
- Write and point keywords to help with searches
- Point supported and necessary tools
  - You'll not remember all the rules, the tool will/should know
- Add examples when necessary
- Flexible and adaptable to many languages and projects when possible
- Should be created with taste and responsiveness
- Add reasons for the rules, it's hard to follow something that is not understood
- References are always a good thing to understand the concepts
  - Use good references, internet is a democratic place, but language authors, books and open source projects/communities are huge preference

## General

- Generally, unused (never executed or commented-out) code is not allowed to be added to a project.
- If unused (commented) code is to be committed, it must serve a purpose and have a note explaining why it is there
- Write short, to-the-point methods that encapsulate a very specific behavior, rather than long procedural functions.
  - Express ideas directly in code
  - Express intent
    - Don't say in comments what can be clearly stated in code
- Prefer compile-time checks over run-time checks
- Follow the project code style, it helps to understand and write code
  - Consistent style speeds up learning
- Low-level, tricky, close-to-the-hardware, error-prone, expert-only code/features should only be used when encapsulated over higher-level facilities and abstraction layers.
- Don't leak !

## Code Practices

### Encapsulate Magic Variables
Replace unexplained numeric literals with named constants and enums. This clarifies intent for reviewers and future maintainers.

Bad:
```cpp
start_communication(0, 1, 232);
```

Good:
```cpp
start_communication(vehicle_id, component_id, Messages::RequestStatus);
```

### Minimize Function Arguments
Reduce parameter lists by using setter methods or aggregate initialization. Rather than passing numerous values to constructors, apply individual setters or designated initializers for improved readability and maintainability.

Use setter methods:
```cpp
vehicle->setNumberOfTires(4);
vehicle->setColor(Colors::Blue);
```

Use C++20 designated initializers:
```cpp
Vehicle vehicle = {
    .tires = 4,
    .color = Colors::Blue,
    .weight = 1200
};
```

Use user-defined literals (C++11+) for clarity:
```cpp
auto distance = 613_km;
auto weight = 1.2_tn;
```

### Encapsulate Code Blocks
Break functions into smaller, focused methods with descriptive names. This approach eliminates the need for explanatory comments, as the function name does the job for free.

### Comment Judiciously
Avoid redundant comments that merely restate code. One of the most important skills about writing comments is knowing when not to write them. Reserve comments for:
- Complex logic requiring external context (like datasheets)
- Non-obvious algorithms or business rules
- Links to relevant documentation or specifications

Avoid comments that:
- Restate what the code clearly does
- Describe obvious operations
- Become outdated and misleading

## Documentation

Code should be well documented. Strive to make it easy for a new developer to pick up where you left off. Well documented patches will also facilitate and expedite code review and the software development process.

- All methods should be documented
- All class members should be documented
- When a variable or method involves specific dimensions/units, the units involved should be made totally clear via explicit names or comments
- Document temporary variables at their declaration wherever it may be helpful to someone else
- C++ projects should use doxygen-style comments
- Python scripts should use Docstrings
- TypeScript/JavaScript projects should use JSDoc for classes, functions, methods, interfaces, and enums

## Testing

- Tests should be made for many things, but not everything (creating tests should result in less work, not more!)
- Every project should have some level of continuous integration
- Run tests frequently. Ensure all tests pass for every commit

## Deployment

Code may be hosted on github or amazon s3. Contact Jacob to obtain keys.

## Portability

Code should be developed with a high level of abstraction and with portability in mind. Put some thought and consideration into the future and plan your code before you write it. Consult with your teammates!

- For desktop GUIs, Windows, Mac and Linux should be targeted (use Qt)
- For embedded applications, multiple (if not any and all) targets should be considered (eg. SBCs for companion, uCs for sensor drivers)
- Use a transparent build system to expose all dependencies and requirements to build a project. Don't rely on eclipse to generate your makefiles; avoid closed vendor tools and compilers like `arm-attolic-eabi-gcc`. Anyone should be able to clone one of our projects and build it with readily available opensource toolchains.

## Dependencies

- Pin all dependencies to exact versions in dependency files (`package.json`, `requirements.txt`, `Cargo.toml`, etc.)
- Keep dependencies, toolchains, and compilers up to date with the latest stable releases

## Modern Best Practices

Take time to maintain your education on modern best practices for your software projects.

- Use C++14 or newer standard for C++ projects
- Use Python 3.11+ for Python projects
- Use Rust for new systems programming and backend services
- Use TypeScript for web applications
- Generally keep our projects, dependencies, toolchains, and compilers up to date with the latest stable releases

## What should be avoided
- Most programmers don't know what "everybody knows".
  - Add comments in code and commits to help new programmers and review.
- Legacy code should be dammed, new features are here to help.
- Archaic or foreign code styles, we are in 21st century.
  - Do not write "Pseudo-Java" (1990s)
  - Do not write "C with Classes" (1980s)
  - Do not write "C" (1970s)
  - Avoid naked news, deletes when possible
    - RAII
    - Use ownership abstraction
- Don't sacrifice:
  - Generality: Do not create specific code without abstraction layers.
  - Performance: When and where is necessary.
  - Simplicity: Be simple when possible, break code steps if necessary. Can your code be understood by a reasonable peer in reasonable time? Avoid clever tricks.
  - Portability: Take in mind that the code runs and could run in different platforms.

## References

### CppCon Talks
- [Kate Gregory - Naming is Hard: Let's Do Better (2019)](https://www.youtube.com/watch?v=MBRoCdtZOYg)
- [Kate Gregory - Simplicity: Not Just For Beginners (2018)](https://www.youtube.com/watch?v=n0Ak6xtVXno)
- [Kate Gregory - What Do We Mean When We Say Nothing At All? (2018)](https://www.youtube.com/watch?v=kYVxGyido9g)
- [Kate Gregory - 10 Core Guidelines You Need to Start Using Now (2017)](https://www.youtube.com/watch?v=XkDEzfpdcSg)
- [Walter E. Brown - Whitespace ≤ Comments << Code (2017)](https://www.youtube.com/watch?v=NLebZ3XT92E)
- [Lars Knoll - Qt as a C++ Framework (2017)](https://www.youtube.com/watch?v=YWiAUUblD34)

### API Design
- [The Little Manual of API Design - Jasmin Blanchette](https://people.mpi-inf.mpg.de/~jblanche/api-design.pdf)
- [Qt API Design Principles](https://wiki.qt.io/API_Design_Principles)
- [Designing Qt-Style C++ APIs - Matthias Ettrich](https://doc.qt.io/archives/qq/qq13-apis.html)

### Patrick posts
- [How to rock: First tips](https://patrickelectric.work/blog/2020/how-to-rock-first-tips/)
