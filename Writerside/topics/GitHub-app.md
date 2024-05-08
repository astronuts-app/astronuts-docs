# GitHub app

<img src="github-app-marketplace-listing.png" alt="github app on marketplace" border-effect="line" width="321" 
thumbnail="true"/>

## Introduction {id="github-app-intro"}

The [GitHub app for Astronuts](https://github.com/marketplace/astronuts-app) is a powerful way
to harness the full suite of products and services Astronuts has to offer.

It enables you to connect your GitHub repositories with Astronuts
and [get insights on your pull requests](Pull-request-insights.md)
and get [resolutions for errors](Error-monitoring.md) observed in your application server logs.

If you do not use GitHub in your organization, you do not need to connect it with Astronuts.
In that case, some features of Astronuts might be unavailable to you,
especially those which rely on GitHub for functioning,
e.g., [Pull request insights](Pull-request-insights.md).

## How it works {id="github-app-how-it-works"}

* The GitHub app for Astronuts connects your Astronuts account with your organizational GitHub account. You can [install the app](Connect-Git-Repositories.md) from the Astronuts dashboard from the **Settings | Integrations** page.
* Once installed, the app learns from your connected repositories based on training that you perform. You can [train Astronuts on your repositories](Setup-AI-Training.md) by navigating to **Intellidocs | Train** from the sidebar.
* The app also posts [comments on your pull requests](Pull-request-insights.md) and attaches labels indicating code quality.