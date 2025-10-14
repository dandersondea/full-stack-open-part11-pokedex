# Exercise 11.1

- **Application language:** Python

## Some common steps in a CI setup include linting, testing, and building. What are the specific tools for taking care of these steps in the ecosystem of the language you picked?

- **Linting:**
  - There are a number of options for linting a Python application, with two notable linters being _Flake8_ and _Ruff_. For this application we'll use Ruff as it is fast and includes rules from many tools, including Flake8.
    - Ruff is a replacement for ESLint in the JavaScript/TypeScript ecosystem.
  - To enable consistency of code styling we will also leverage a formatter, in particular _Black_.
    - Black is a replacement for Prettier in the JS/TS ecosystem.
  - To reduce type errors, we will use _mypy_ to enforce static typing checking.
    - Mypy is a replacement for TypeScript in the JS ecosystem.
- **Testing:**
  - For testing we will use _pytest_ as our testing framework. Pytest enables unit, integration, and functional tests, integrates smoothly with VS Code, and offers plugins for customization.
    - Pytest is a replacement for Jest and Vitest in the JS/TS ecosystem.
  - To measure what % of the code is executed during tests, we will also use _coverage.py_.
- **Building:**
  - As Python is an interpreted language it doesn't need to be transpiled or bundled prior to running.
    - As such, "build" in the context of Python often means:
      - Freezing dependencies in reproducible environments ("dependency management"),
      - "Packaging" the code for distribution or production, or
      - Compiling executables.
    - Equivalents of the following are not needed in Python: _Create React App_, _Vite_, _Expo_, _Webpack_, _esbuild_, or _Babel_.
  - For dependency management we will use _Poetry_, though there are a number of other options such as _Pip_ + _venv_, _Pipenv_, _Hatch_, and _uv_.
    - Poetry in this context replaces _npm pack_.
    - With Poetry, _pyproject.toml_ is the equivalent of _package.json_ in the JS/TS ecosystem.
  - For packaging, we will use _Poetry_ as we will already be using it for dependency management. Another option is _Setuptools._
  - For compiling executables we will use _Docker_ to create a Docker image, though _PyInstaller_ and _shiv / zipapp_ are also options.

## What alternatives are there to set up the CI besides Jenkins and GitHub Actions?

- Jenkins and GitHub actions both support Python CI/CD, though other alternatives include:
  - GitLab CI/CD (hosted or self-hosted),
  - Circle CI (hosted),
  - Travis CI (hosted),
  - Azure Pipelines (hosted), and
  - Drone / Woodpecker / Buildkite (self-hosted / hybrid).

## Would this setup be better in a self-hosted or a cloud-based environment? Why? What information would you need to make that decision?

- As this application is being worked on by a team of ~6 people, it is best suited to use a cloud-based CI/CD environment.
- The motivation for this is that the team is small and using a cloud-based CI setup will be less complex, thereby allowing the team to focus on application development and potentially avoiding having to build competencies in CI server management.
- The cloud-based setup will also automatically scale as the application grows, whereas a self-hosted solution would require ongoing work to scale.
- Cloud-based solutions are also often be free for small teams.
- Ultimately though if customization or special hardware (\_e.g. GPUs) is required that is not available in a cloud-based environment, a self-hosted setup is the only option.
