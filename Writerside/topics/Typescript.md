# Typescript

#### Steps to Run Astronuts Code Quality Checks on your Typescript Project {id="steps-to-run-astronuts-code-quality-checks-on-your-typescript-project"}

<video src="https://youtu.be/fRIiY8tqhAo" preview-src="javascript_video_thumbnail.png" /> {id="typescript-code-quality-setup-video"} 

### Install Astronuts Reporter {id="install-astronuts-reporter-typescript"}

To install Astronuts Reporter, open your terminal and run the following command:

<tabs>
    <tab id="npm-install" title="npm">
        <code-block lang="bash">
            npm install @astronutsapp/astronuts-reporter --save-dev
        </code-block>
    </tab>
    <tab id="pnpm-install" title="pnpm">
        <code-block lang="bash">
            pnpm install @astronutsapp/astronuts-reporter --save-dev
        </code-block>
    </tab>
    <tab id="yarn-install" title="yarn">
        <code-block lang="bash">
            yarn add @astronutsapp/astronuts-reporter --save-dev
        </code-block>
    </tab>
</tabs>

This command installs Astronuts Reporter as a development dependency in your project.

## Integration with CI/CD Workflow {id="integration-with-ci-cd-workflow-typescript"}

Now for astronuts to run the code quality checks on your project, you need to add the following steps to your CI/CD
workflow file:

Step 1 : Add the following command to your workflow file to generate the reports.

```bash
- name: Generate Astronuts Reports
  run: npx astronuts-generate
```

Step 2 : Run Astronuts Code Quality Checks on your Python Project.

```bash
- name: Run Astronuts Code Quality Checks
  uses: astronuts-app/astronuts-code-quality-action@v4
```


For more info you can check
the [Astronuts Code Quality Action](https://github.com/marketplace/actions/astronuts-code-quality-action).

For more reference on how to use Astronuts Reporter, you can check
the [Astronuts Reporter](https://www.npmjs.com/package/@astronutsapp/astronuts-reporter).

For more info on the workflow file, you can check
the [GitHub Actions Workflow Sample](https://github.com/astronuts-app/samples/blob/main/.github/workflows/build_typescript_sample.yml).