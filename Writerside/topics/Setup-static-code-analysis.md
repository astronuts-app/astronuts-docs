# Setup static code analysis

Astronuts performs static code analysis on your Git repositories
to provide insights into your code quality and security.
The static code analysis is run as part of your CI/CD pipeline.
This tutorial will guide you through the process of setting up static code analysis for your repositories.

We will setup static code analysis for a **GitHub repository** in this example
using the **[Astronuts GitHub code quality action](GitHub-code-quality-action.md)**.
The process is similar for other Git providers.

<tip>
    <p>
        This is an important setup and without setting code quality analysis you won't be able
        to see metrics in various parts of the system like your 
        <a href="Engineering-metrics-and-analytics.md" summary="Engineering metrics and analytics"><b>Analytics Dashboards</b></a>
        or <a href="Pull-request-insights.md" summary="Pull request insights"><b>Pull Request insights</b></a>.
    </p>
</tip>

Depending on your Git provider, you can set up static code analysis in different ways.
For example, if you use GitHub,
you would use the **[Astronuts GitHub code quality action](GitHub-code-quality-action.md)**, 
and for BitBucket you would use the **[Bitbucket code quality pipe](Bitbucket-code-quality-pipe.md)**.

If you don't find the tool you need for your specific Git provider,
check the [Astronuts roadmap](https://github.com/astronuts-app/astronuts-tracker/milestones)
or submit a feature request in our [Astronuts issue tracker](https://github.com/astronuts-app/astronuts-tracker/issues)

<procedure title="Static code analysis using GitHub Actions" id="static-code-analysis-using-github-actions">
    <step>
        <p>In your Git repository for which you want to setup static code analysis using <b>GitHub Actions</b>, update your GitHub Actions workflow file with the following lines. Ensure that, this action is executed <b>after</b> your main <b>build step</b> that compiles your code and runs your unit/integration test cases.</p>
        <code-block lang="yaml">
      - name: Run Astronuts Code Quality Checks
        uses: astronuts-app/astronuts-code-quality-action@v3
        with:
          sourceLanguage: 'java'
        </code-block>
            <tip>
            <p>
                For a supported list of programming languages and build tools see the <a href="https://github.com/marketplace/actions/astronuts-code-quality-action" summary="Astronuts GitHub Code Quality action on GitHub">Astronuts GitHub Code Quality action on GitHub</a>.<br/><br/>
                 If you don't see your programming language or build tool,
                check the <a href="https://github.com/astronuts-app/astronuts-tracker/milestones" summary="Astronuts roadmap">Astronuts roadmap</a>
                or create an issue in the <a href="https://github.com/astronuts-app/astronuts-tracker/issues" summary="Astronuts issue tracker">Astronuts issue tracker</a>.
            </p>
        </tip>
    </step>
    <step>
        <p>Typically, you would want the static code quality analysis to run on your <code>main</code> branch and <code>feature</code> branches.
            There is no restriction on which branches you want to run static code quality analysis.</p>
        <p>For example, to run static code quality on the <code>main</code> branch and some specific branches matching certain prefixes, you would typically use these statements at the top of your workflow file.</p>
        <code-block lang="yaml">
         on:
          push:
            branches:
              - main
              - develop
              - feature/*
              - bugfix/*
              - hotfix/*
        </code-block>
        <p>To ensure that the static code quality analysis runs when pull requests are merged to your <code>main</code> branch, you would include the following in your workflow file.</p>
        <code-block lang="yaml">
          pull_request:
            branches:
              - main
        </code-block>
        <tip>
            <p>
                Consider testing the code quality analysis on your personal feature branch before you run it on your <code>main</code>.
            </p>
        </tip>
    </step>
    <step>
        <p>Trigger a build so that the code quality action runs.</p>
        <p>A successful execution of the code quality action would print lines similar to the following in your <b>build output</b>.</p>
        <code-block lang="shell">
            Analysis root directory is '/github/workspace'
            Source code language is 'java'.
            Detected build system is 'gradle'. If this is not correct, supply the build system manually.
            Found 1543 source files in 39 root directories.
            Found 76 test files in 18 root directories.
            Found 2163 binary files in 39 root directories.
            Found 96 test binary files in 18 root directories.
            Found 17 coverage report files.
            Found 18 test report files.
            Performing analysis...
            Analysis successful.
        </code-block>
        <tip>
            <p>
                For a successful static code quality analysis
                using the <a href="GitHub-code-quality-action.md"><b>Astronuts GitHub code quality action</b></a>,
                you must <b>first install</b> the <a href="GitHub-app.md"><b>Astronuts GitHub app</b></a>.
                Doing so,
                authorizes you
                to run the <a href="GitHub-code-quality-action.md">Astronuts GitHub code quality action</a> on your Git repositories. 
            </p>
        </tip>
    </step>
    <step>
        <p>After you ensure that the action ran successfully on your <code>feature</code> branch, you can run the action on your <code>main</code> branch.</p>
        <tip>
            <p>
               Running the <a href="GitHub-code-quality-action.md"><b>Astronuts GitHub code quality action</b></a> on your <code>main</code> <b>and</b> <code>feature</code> branches gives you rich trends and diffs on <a href="Pull-request-insights.md"><b>Pull request insights</b></a>. You can see the impact of your pull request on the overall quality of your repository if the pull request is merged.
            </p>
        </tip>
        <p>When code quality analysis data is available for both your <code>main</code> and <code>feature</code> branch, we attach the following type of image on a comment that the <a href="Pull-request-insights.md">Astronuts Pull Request Insights</a> bot adds to your pull requests.
        </p>
        <img src="pr-code-quality-image.png" alt="pull request code quality" border-effect="line" thumbnail="false"/>
    </step>

</procedure>