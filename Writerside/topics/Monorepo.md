# Monorepo

## Steps to Run Astronuts Code Quality Checks on your Monorepo which can contain multiple projects {id="monorepo-code-quality-steps"}
Setup your each project individually
<tabs>
    <tab id="java" title="Java">
        <a href="https://www.astronuts.io/docs/java.html">Setup Astronuts Code Quality Action for Java Project</a>
    </tab>
    <tab id="python" title="Python">
        <a href="https://www.astronuts.io/docs/python.html">Setup Astronuts Code Quality Action for Python Project</a>
    </tab>
    <tab id="javascript" title="Javascript">
        <a href="https://www.astronuts.io/docs/javascript.html">Setup Astronuts Code Quality Action for Javascript Project</a>
    </tab>
    <tab id="typescript" title="Typescript">
        <a href="https://www.astronuts.io/docs/typescript.html">Setup Astronuts Code Quality Action for Typescript Project</a>
    </tab>
</tabs>

## Integration with CI/CD Workflow
You can integrate Astronuts Code Quality action into your build scripts, which is especially useful in continuous integration (CI) environments where tests are run automatically.
Add this to your workflow file to run Astronuts Code Quality Checks on your Monorepo project:

<tabs>
    <tab id="workflow-monorepo" title="build.yml">
        <code-block lang="yaml">
        name: 'Build: Monorepo'
        on:
          push:
            branches:
              - main
              - develop
              - feature/*
              - bugfix/*
              - hotfix/*
            paths:
              - 'java-sample/**'
              - 'javascript-sample/**'
              - 'python-sample/**'
              - 'typescript-sample/**'
          pull_request:
            branches:
              - main
            paths:
              - 'java-sample/**'
              - 'javascript-sample/**'
              - 'python-sample/**'
              - 'typescript-sample/**'
        # Permissions
        permissions:
          contents: read
       # Jobs
        jobs:
          Build-Java:
            runs-on: ubuntu-latest
            defaults:
              run:
                working-directory: ./java-sample
            steps:
              - uses: actions/checkout@v4
              # Setup JDK 21
              - name: Set up JDK 21
                uses: actions/setup-java@v4
                with:
                  java-version: '21'
                  distribution: 'corretto'
             # Setup Gradle
              - name: Setup Gradle
                uses: gradle/actions/setup-gradle@v3
             # Build with Gradle
              - name: Build with Gradle
                run: ./gradlew clean build --console=plain --scan
         # Build Javascript and generate reports
          Build-Javascript:
            runs-on: ubuntu-latest
            defaults:
              run:
                working-directory: ./javascript-sample
            steps:
              - uses: actions/checkout@v4
              - name: Use Node.js 20.x
                uses: actions/setup-node@v4
                with:
                  cache-dependency-path: ./javascript-sample/package-lock.json
                  node-version: '20.x'
                  cache: 'npm'
              - name: Install NPM packages
                run: npm install
              - name: Generate with Astronuts
                run: npx astronuts-generate
          # Build Python and generate reports
          Build-Python:
            runs-on: ubuntu-latest
            defaults:
              run:
                working-directory: ./python-sample
            steps:
              - uses: actions/checkout@v4
              - name: Set up Python
                uses: actions/setup-python@v5
                with:
                  python-version: 3.12.0
              - name: Install dependencies
                run: |
                  python -m pip install --upgrade pip
                  pip install pyclean
                  pip install -r requirements.txt
                  pyclean .
                  astronuts-generate
          # Build Typescript and generate reports
          Build-Typescript:
            runs-on: ubuntu-latest
            defaults:
              run:
                working-directory: ./typescript-sample
            steps:
              - uses: actions/checkout@v4
              - name: Use Node.js 20.x
                uses: actions/setup-node@v4
                with:
                  cache-dependency-path: ./typescript-sample/package-lock.json
                  node-version: '20.x'
                  cache: 'npm'
              - name: Install NPM packages
                run: npm install
              - name: Generate with Astronuts
                run: npx astronuts-generate
          # Preform code quality check on the generated reports
          Code-Quality-Checks:
            needs:
              - Build-Java
              - Build-Javascript
              - Build-Python
              - Build-Typescript
            runs-on: ubuntu-latest
            steps:
              - uses: actions/checkout@v4
              - name: Run Astronuts Code Quality Checks
                uses: astronuts-app/astronuts-code-quality-action@v4
        </code-block>
    </tab>
</tabs>
Note* : There is no need to specify build systems and languages used in the project as we use our auto detection system to detect that.  
<br></br>
For more info you can check
the [Astronuts Code Quality Action](https://github.com/marketplace/actions/astronuts-code-quality-action).

For more info on the workflow file, you can check
the [GitHub Actions Workflow Sample](https://github.com/astronuts-app/monorepo-analysis-test/blob/main/.github/workflows/publish.yml).
