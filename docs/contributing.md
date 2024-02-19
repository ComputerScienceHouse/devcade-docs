# Contributing to Devcade
So, you'd like to contribute to Devcade? Thats great, we'd love the help! 

This document should serve as a bit of a guide to help you get started with the project as a whole, as well as to the documentation site more specifically if thats what you're here for. Note that most of the things mentioned here are guidelines, they should be followed but not following them isn't going to end the world either. This project is split into a handful of parts and therefore a handful of separate repositories so, while this will give you an overview and a more general guide, you should refer to the documentation of each part for more specifics. For reference, each of the repos are linked below:

# Parts of the project
- [Onboard](https://github.com/ComputerScienceHouse/devcade-onboard) - The launcher and menu for the arcade cabinet itself.
- [Website](https://github.com/ComputerScienceHouse/devcade-website) - The homepage of the project and the place to upload and manage games.
- [Library](https://github.com/ComputerScienceHouse/Devcade-library) - The C# library for games to use in order to interact with the cabinet.
- [API](https://github.com/ComputerScienceHouse/devcade-api) - The API the website and onboard use to interact with the database and games storage.
- [Template](https://github.com/ComputerScienceHouse/Devcade-game-template) - The Monogame template for a Devcade game.
- [Flatpakify](https://github.com/ComputerScienceHouse/devcade-flatpakify) - The helper tool to bundle games into flatpaks.
- [Documentation](https://github.com/ComputerScienceHouse/devcade-docs) - The docs site to consolidate and host all relevant documentation.

# Useful resources
- If you aren't reading this from there already, you should check out our [documentation site](https://devcade.csh.rit.edu/docs#/). It's where we host all of the relevant documentation for each part of the project as well as any documentation or guides that don't fit in any single repository.
- If you've found a bug or just want to request a feature, please create an issue on github on the relevant repo.
- We don't have many public avenues of communication yet but in the meantime if you have questions or want to reach out, feel free to email us at devcade@csh.rit.edu.

# Testing
Currently, most parts of the project don't have any automated testing or CI. Each repo should however have instructions on running it locally to manually ensure that everything is working at the very least. Please refer to the readme of each repo for those instructions and the contributing guide of each repo as they become available for any specifics in testing the project.

# Environment
As mentioned above, details on running each part of the project locally should be included in the readme of each repo. Any environment variables needed or other details on setting up a development environment should be included there as well.

# Submitting changes
If you have made changes to the project and would like to contribute them upstream, you should create a pull request on the relevant repo. There are no templates for pull requests available at this time but you should include the following:
- A summary of any changes being submitted
- Any issues these changes address or other reasons for the changes
- Any known new issues created by the changes or other additional changes that need to be implemented for these changes to be effective
Once submitted and ready for review, one or more members of the Devcade core team will review it and respond accordingly. Do note however that all of the core team are college students with classwork, other projects, and lives outside of this. So please understand if PRs aren't always reviewed in a timely manner.

# Reporting bugs or requesting features
If you have noticed a bug, issue, incorrect or outdated documentation, or just want to suggest a new feature, please make an issue on the relevant repo. Please label your issue accordingly and check that the issue doesn't already exist before posting. Once again, there are no templates for issues at this time but please include as much detail as you can. Some things that are helpful to include are:
- A descriptive title
- Under what circumstances a bug occurs
- Any steps needed to reproduce the bug
- What went wrong, as in what actually happened
- What was supposed to happen or what did you expect to happen any why
- If applicable, include any screenshots or other resources relevant to the issue
- If submitting a suggestion, explain why the feature should be added

# Style guides
Given that this project involves several languages across its repos, there are a couple of style guides to go along with each language. Depending on what language you are working in, we hope that you would do your best to keep to the following guidelines:

## Rust
- All rust codebases should use rustfmt, in most cases through cargo fmt with default settings. 
- Ideally all functions and structs should have /// doc comments.

## C#
- Any C# codebases should use top syntax for curly braces, also known as same line or one true brace style where opening curly braces are placed on the same line as the function or control statement separated by one space. 
- Indentation should be done with 4 space characters
- Ideally all classes, methods, and properties should have XML /// doc comments

## Python
- All python codebases should use Pylint defaults
- Ideally docstrings should be used for all methods and classes

## Other
Style and formatting standards for other languages have not been established yet or are not used in the project. If a language is used or introduced that does not have a style guide here, try to follow what exists already if applicable until a standard it settled on.

# Code of conduct
Currently this project has no direct code of conduct but it should inherit a couple by default. As always be kind to others as a base line but as a project within the Computer Science House(CSH) organization, and by extension within the Rochester Institute of Technology(RIT), the following codes of conduct should be relevant to varying degrees:
- [RIT Code of Ethical Conduct and Compliance](https://www.rit.edu/policies/c000)
- [RIT Code of Conduct for Computer Use](https://www.rit.edu/policies/c082)
- [CSH Code of Conduct](https://coc.csh.rit.edu/)

# Where to ask for help
If you want to contribute or are otherwise interested but are stuck somewhere, your first place of inquiry should be in the comments of any relevant PR or issue on github. If this is not applicable or for another method of contact, reach out to devcade@csh.rit.edu.