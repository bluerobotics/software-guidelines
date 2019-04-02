# Documentation

## General Recommendations

- Be mindful that we cater to users and enthusiasts from many countries and languages. Use language that translates well, and avoid idioms
- Write documents that are concise and punctual
- Use markdown for documents whenever possible; don't use special/plugin formatting. Markdown is preferred because it is lightweight and portable among hosting/templating platforms
- [hyperlinks](https://en.wikipedia.org/wiki/Hyperlink) are cheap, use them! Use markdown anchors to refer to section headings. Both are easy to use with markdown
- Try to maintain one source of documentation, avoid documenting the same thing in two places
- Use version control (git) for documents whenever possible
- All Blue Robotics documentation patches should be peer reviewed, just like code

## Documentation Locations

- [ArduSub gitbook](http://ardusub.com)
    This repository is owned and maintained by Blue Robotics. This repository contains:
    - General ArduSub firmware documentation and instructions
    - Blue Robotics companion documentation
    - QGC + ArduSub + companion integration and usage instructions
    - Developer examples for interacting with ArduSub via MAVLink/MAVProxy
- [ArduPilot wiki](http://ardupilot.org/ardupilot/)
    This [repository](https://github.com/ArduPilot/ardupilot_wiki) is owned and maintained by the ardupilot organization. It contains documentation for ardupilot generally, as well as documentation for the other ardupilot vehicles (copter, plane, rover, but not ArduSub).
- [QGroundControl gitbook](https://docs.qgroundcontrol.com/en/)
    This repository is owned and maintained by the mavlink organization. It is the official documentation for QGroundControl users. This is where documenation on QGroundControl usage should generally go.
- [MAVLink website](https://mavlink.io/)
    This repository documents the MAVLink binary communication protocol used by QGroundControl, Companion, and ArduPilot. Here, you can find the message definitions and information about how to develop MAVLink enabled applications.
- [gh-pages](https://pages.github.com/)

    Github employs a feature called gh-pages to host project websites. The source for the website is maintained in a separate branch of the repository named `gh-pages`. If the branch exists, the website can be accessed via the url http://*username*.github.io/*repository*. Project pages in the Blue Robotics organization are also available at https://docs.bluerobotics.com/*repository*.

    gh-pages sites is a good place to host doxygen documentation for a project.

    Blue Robotics currently has the following projects with gh-pages sites:
    [ping-viewer](https://docs.bluerobotics.com/ping-viewer)
    [ping-arduino](https://docs.bluerobotics.com/ping-arduino)
    [ping-python](https://docs.bluerobotics.com/ping-python)

- Repository READMEs

    Each repository should have a README in the root directory. This README is displayed on the project's home page. The README should contain information about what the project does, how to install it, and how to use it. CI status information should be added to the top of the README. Additional READMEs may exist in project subdirectories, which will be displayed when the directory is opened in github.

- Blue Robotics documentation

    The Blue Robotics wordpress website has documentation pertaining to Blue Robotics products, and is targeted at Blue Robotics customers. This is where *product* documentation should go. There are three tabs of interest for the product documentation:
        - Description: High level product description and features
        - Technical Details: Specifications, drawings, models and datasheets
        - Learn: Educational resources, documentation, instructions, example usage and tutorials

    If the product is related to one or more software projects, the product *Learn* tab should link out to the software documentation. 

- This repository
    This repository contains guidelines on how we develop things at Blue Robotics. Preferred methods, processes and development tools may also be described here, as well as tips and tricks.
