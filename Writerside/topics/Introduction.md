# Quick Introduction

Here's the busy person's version of <b>what's Astronuts, what it does, and how it can help you</b>.

## What is Astronuts? {id="what_is_astronuts" collapsible="false" default-state="expanded"}
Astronuts is a suite of tools intended for software engineering teams ranging from solo developers,
pizza sized teams and larger distributed teams.
Its rapidly evolving
and is currently laser focussed on solving problems that engineers and engineering teams face every day.

## How can Astronuts help you? {id="how_can_astronuts_help_you" collapsible="false" default-state="collapsed"}

### Pull Request Insights {id="pr-insights" collapsible="false" default-state="collapsed"}

Provide you detailed context on your Pull requests,
specifically telling you the intent of a pull request, related previous PRs and the code quality of the PR.
We do this by performing static code analysis on the branch that's want to merge with your main branch.
Using a visual image we provide,
you will be able to assess the impact on engineering metrics, like SQALE and DORA metrics.
Learn more about [pull request insights](Pull-request-insights.md).

<img src="pr-insights-and-code-quality.png" alt="code quality metrics pull request static code analysis" border-effect="line" width="321" thumbnail="true"/>


### Engineering Metrics and Analytics {id="eng-metrics-and-analytics" collapsible="false" default-state="collapsed"}

Provide you engineering metrics and trends in your dashboard.
These metrics indicate key aspects of your codebase,
engineering processes and, team to help you make informed decisions.
Learn more about [engineering metrics and analytics](Engineering-metrics-and-analytics.md).

<img src="engineering-metrics.png" alt="engineering metrics and analytics" border-effect="line" width="321" thumbnail="true"/>


### Realtime Error Monitoring and Resolutions {id="realtime-error-monitoring" collapsible="false" default-state="collapsed"}

Provide you real time error monitoring on your production application server logs and provide resolutions.
Learn more about [real-time error monitoring and resolutions](Error-monitoring.md).

<img src="error-monitoring-slack.png" alt="error monitoring and resolutions" border-effect="line" width="321" thumbnail="true"/>

## Who is Astronuts for? {id="who-is-astronuts-for" collapsible="false" default-state="collapsed"}

Not one size fits all, and every team has unique needs. But we did try our best to build out Astronuts in way that it can be useful to a wide range of teams.
### Small teams {id="small-teams" collapsible="false" default-state="collapsed"}

Small pizza sized teams (five to seven engineers) who want to ship fast, save time and produce stable code that works.
Such teams usually don't like process overheads and prefer to focus on shipping features and fixing bugs.
Astronuts quick onboarding and self-service model is perfect for such teams.

### Medium-sized teams {id="medium-teams" collapsible="false" default-state="collapsed"}

Organizations having a large number of polyglot applications developed over the years,
will find Astronuts useful to remove tech debt and reduce time in pull request reviews.
Also, their on-call support teams can expect to fix things much faster in production.

## How it works? {id="how_it_works" collapsible="false" default-state="collapsed"}

- Astronuts seamlessly integrates your tools, teams and processes into one single platform so that you can have a broader and richer context. You build this holistic and contextual knowledge base by connecting your tools like Git repositories (e.g., GitHub, Bitbucket, GitLab etc.) and issue management tools (e.g., Jira), Astronuts constantly learns what your system does and makes sense of it.

- With the power of this extended knowledge base that you, Astronuts can provide you contextual and specific value across the entire software development lifecycle, e.g., in evaluating pull requests, application server log monitoring and running analytics on developer code commits.

- Powered by AI, LLMs, and RAG (retrieval assisted generation), we make sense of what your connected knowledge bases are trying to tell you. Under the hood, we use self-hosted vector databases and large language models to infer answers about the most pertinent questions you have about your codebase, error logs, and processes. 

For more details, see [Astronuts platform architecture](Astronuts-platform-architecture.md).

## Why did we create Astronuts? {id="why_did_we_build_astronuts" collapsible="false" default-state="collapsed"}

We created Astronuts because we thought that other companies might be facing the same problems that we were facing.
We had a bunch of home-grown tools and hacks that we just couldn't live without.
These were tools for solving our code quality, error monitoring, and engineering metrics problems.
We thought that if we could make these tools available to other companies, they might find them useful too.
So we decided to build Astronuts.

## What's the path ahead? {id="path-ahead" collapsible="false" default-state="collapsed"}

Astronuts is a rapidly evolving platform, where we have a bi-monthly release cycle.
We are constantly adding new features and improving existing ones by listening to our customers.

<a href="https://github.com/astronuts-app/astronuts-tracker/milestones" summary="See the Astronuts tracker to know what's planned for the year">Astronuts roadmap</a>
