# GitHub code quality action

## Astronuts Code Quality Action {id="astronuts-code-quality-action"}

Astronuts Code Quality Action is a GitHub action that runs Astronuts code quality scans on your projects. It supports multiple programming languages and integrates with various build systems.

## Features {id="code-quality-action-features"}

- **Code Quality Analysis**: Analyzes source code for code quality issues such as bugs, code smells, and security vulnerabilities.
- **Multi-Language Support**: Supports multiple programming languages including Java, TypeScript, JavaScript, and Python.
- **Build System Integration**: Integrates with various build systems including Gradle, Maven, npm, and pip.
- **Configurable**: Can be configured to fail the build if code quality analysis fails.

## Supported Languages {id="code-quality-action-supported-languages"}

Astronuts Code Quality Action supports the following languages:

- [Java](Java.md)
- [TypeScript](Typescript.md)
- [JavaScript](Javascript.md)
- [Python](Python.md)

Click on a language to see detailed instructions on how to set up and run Astronuts Code Quality Checks for that specific language.

## Supported Build Tools {id="code-quality-action-supported-build-tools"}

Astronuts Code Quality Action supports the following build tools:

- Gradle
- Maven
- npm
- pip

## Inputs {id="code-quality-action-inputs"}

These are some of the supported input parameters of the action:

- `sourceLanguage` - **_(Required)_** The programming language of the source code to be analyzed.
- `rootDir` - _(Optional)_ The root directory of source code. If unspecified, it's auto-detected.
- `buildSystem` - _(Optional)_ The build system. If not specified, the action tries to auto-detect one.
- `failOnError` - _(Optional)_ If set to true, the build will fail if the code quality analysis fails. Build will pass silently otherwise.

## Example usage {id="code-quality-action-example-usage"}

```yaml
uses: actions/astronuts-code-quality-action@v4
with:
  sourceLanguage: 'java'
  buildSystem: 'gradle'