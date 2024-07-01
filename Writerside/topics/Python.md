# Python

## Steps to Run Astronuts Code Quality Checks on your Python Project {id="python-code-quality-steps"}

<video src="https://youtu.be/EPU5-iRt97w" preview-src="python_video_thumbnail.png" /> {id="python-code-quality-setup-video"}

## Astronuts Python Reporter {id="astronuts-python-reporter"}

Astronuts Reporter is a powerful tool that generates test reports. It's designed to be easy to use.

## Installation {id="python-installation"}

To install Astronuts Reporter, open your terminal and run the following command:

### Using Pip {id="python-installation-pip"}

```bash
pip install astronuts-python-reporter
```

This command installs Astronuts Reporter as a development dependency in your project.

## Integration with CI/CD Workflow {id="python-integration-ci-cd"}

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
```
Note* : There is no need to specify build systems and languages used in the project as we use our auto detection system to detect that.
<br></br>

For more info you can check
the [Astronuts Code Quality Action](https://github.com/marketplace/actions/astronuts-code-quality-action).

For more reference on how to use Astronuts Reporter, you can check
the [Astronuts Reporter](https://pypi.org/project/astronuts-python-reporter/).

For more info on the workflow file, you can check
the [GitHub Actions Workflow Sample](https://github.com/astronuts-app/samples/blob/main/.github/workflows/build_python_sample.yml).
