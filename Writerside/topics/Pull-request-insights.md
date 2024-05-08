# Pull request insights

<img src="pull-request-insights.png" alt="pull request insights" border-effect="line" width="321" 
thumbnail="true"/>

## Introduction {id="pull-request-insight-intro"}

Astronuts provides rich insights on your pull requests by making sense of what's contained in a pull requests, its intent and the quality of the changes being pushed by the PR. It also provides suggestions on how to improve the quality of the code being pushed.

## Setup {id="pull-request-insight-setup"}

* To enable pull request insights, you need to [connect your GitHub repositories](Connect-Git-Repositories.md) with Astronuts.
* You can manage further settings for pull request insights from the **Pull Requests | Settings** page.

## How it works {id="pull-request-insight-how-it-works"}

Pull request insights are delivered by the Astronuts AI engine. The AI engine learns from your repositories and provides insights based on the training you perform.

### Pull request summary and context {id="pull-request-insight-summary"}

As soon as a pull request is created by you or someone in your team,
Astronuts analyzes the changes and provides a summary of the changes.
The context and the intent behind the changes help
you save time in understanding the changes and review/approve a pull request quickly.
This is especially useful for large pull requests containing a considerable amount of changes.
An example is shown below.

<img src="pull-request-insights.png" alt="pull request insights" border-effect="line" width="321" 
thumbnail="true"/>

### Related PRs {id="pull-request-insight-related-prs"}

Astronuts also provides a set of pull requests that are related to the current pull request.
This helps you understand the context of the changes and the impact of the changes on the codebase.
The related pull requests are provided in the same pull request comment which contains the summary.
An example is shown below.

<img src="related-prs.png" alt="pull request insights related " border-effect="line" width="700" 
thumbnail="false"/>

### Code quality {id="pull-request-insight-code-quality"}

Astronuts performs static code analysis on the changes in the pull request.
It provides a visual image that helps you assess the impact on engineering metrics, like SQALE and DORA metrics.
Trends in engineering metrics are also provided.
The trends compare metrics from the current pull request with the metrics for your `main` branch.
The visual image is attached to the same pull request comment which contains the summary and related pull requests.

<img src="code-quality-metrics-on-pr.png" alt="pull request insights code quality image " border-effect="line" width="700" 
thumbnail="false"/>

## Labels on pull requests {id="pull-request-insight-labels"}

Astronuts attaches labels to your pull requests indicating the quality of the code changes.
This gives you a quick overview of the quality of the changes being pushed.
The labels are color-coded for easy identification.

<img src="label-approved-astronuts.png" alt="pull request labels" border-effect="line" width="321" 
thumbnail="false"/>

<img src="label-breaking-change.png" alt="pull request labels" border-effect="line" width="321" 
thumbnail="false"/>