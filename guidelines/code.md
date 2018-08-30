# Code Guidelines

## General

- Generally, unused (never executed or commented-out) code is not allowed to be added to a project.
- If unused (commented) code is to be commited, it must serve a purpose and have a note explaining why it is there
- Write short, to-the-point methods that encapsulate a very specific behavior, rather than long procedural functions.

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
