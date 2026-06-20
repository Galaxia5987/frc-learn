# Continuous Integration

Continuous Integration(commonly abbreviated as "CI") is the practice of automatic builds, tests, and integration of code changes within a repository.

For our use case, it's a tool that lets us make sure that changes we proposed(by a [Pull Request](./pull-requests.md)) are complaint with the standards we set.

These are automated checks that happen on every PR, before merging.

## What Our CI Pipeline Include?

Each project has it's own CI needs and standards. But for our robot code we have the following checks:

* **Build**: This check makes sure our code with the new changes actually compiles.

* **Format Checks**: Also called "Spotless". This is an automated test that checks whether the new code follows the style guidelines we set. We also have a formatter that formates our code automatically.

* **Unit Tests**: These are optional, and not every codebase has them. This is code checking our code. This guide currently doesn't cover Unit Testing, but you can check what it is [here](https://canvascodebw.medium.com/unit-testing-pros-and-cons-understanding-why-testing-code-is-a-good-practice-47a81d67ccde).
