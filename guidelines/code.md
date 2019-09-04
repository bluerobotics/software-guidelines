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

## Documentation

Code should be well documented. Strive to make it easy for a new developer to pick up where you left off. Well documented patches will also facilitate and expedite code review and the software development process.

- All methods should be documented
- All class members should be documented
- When a variable or method involves specific dimensions/units, the units involved should be made totally clear via explicit names or comments
- Document temporary variables at their declaration wherever it may be helpful to someone else
- Large projects and apis should use doxygen-style comments, and old projects should be brought up to this standard
- Python scripts should use Docstrings

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

## Modern Best Practices

Take time maintain your education on modern best practices for your software projects.

- Use at least c++11 or newer standard for c projects
- Use python3 for python projects
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
  - Simplicity: Be simple when possible, break code steps if necessary.
  - Portability: Take in mind that the code runs and could run in different platforms.
