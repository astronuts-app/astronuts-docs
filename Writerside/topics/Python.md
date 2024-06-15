# Python
## Steps to Run Astronuts Code Quality Checks on your Python Project
## Astronuts Python Reporter
Astronuts Reporter is a powerful tool that generates test reports. It's designed to be easy to use.
## Installation
To install Astronuts Reporter, open your terminal and run the following command:
### Using Pip
```bash
pip install astronuts-python-reporter
```
This command installs Astronuts Reporter as a development dependency in your project.
## Usage
To generate a test report, run the following command in your terminal:
```bash
astronuts-generate
```
This command tells Astronuts Reporter library to start generating test reports.
## Integration with CI/CD Workflow
You can integrate Astronuts Reporter into your build scripts for automatic report generation, which is especially useful
in continuous integration (CI) environments where tests are run automatically.
Step 1 : Install the Astronuts Reporter package in your project.
Add Astronuts Reporter to your **requirements.txt** file:
```bash
astronuts-python-reporter
```
Then, you can install this dependency in your workflow file (e.g., .yml):
```bash
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
        
```
Step 2 : Run the tests and generate a JUnit XML report.
```bash
     - name: Generate reports
       run: |
         astronuts-generate
```
Step 3 : Run Astronuts Code Quality Checks on your Python Project.
```bash
      - name: Run Astronuts Code Quality Checks
        uses: astronuts-app/astronuts-code-quality-action@v4
        with:
          sourceLanguage: 'python'
          buildSystem: 'pip'
```

For more info you can check
the [Astronuts Code Quality Action](https://github.com/marketplace/actions/astronuts-code-quality-action).

For more reference on how to use Astronuts Reporter, you can check the [Astronuts Reporter](https://pypi.org/project/astronuts-python-reporter/).

For more info on the workflow file, you can check
the [GitHub Actions Workflow Sample](https://github.com/astronuts-app/samples/blob/main/.github/workflows/build_python_sample.yml).
