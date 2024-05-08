# Jira OAuth2 integration

<img src="github-app-marketplace-listing.png" alt="github app on marketplace" border-effect="line" width="321" 
thumbnail="true"/>

## Introduction {id="jira-app-intro"}

The [Astronuts for Jira](https://marketplace.atlassian.com/apps/1232071/astronuts-for-jira)
is a powerful way to create/manage tickets. It enables you to directly create tickets 
from [errors](Error-monitoring.md) directly received on slack observed in your application 
server logs.

<img src="slack-ticket-creation.png" alt="slack ticket creation" border-effect="line" width="321" 
thumbnail="true"/>


## How it works {id="jira-app-how-it-works"}

* The GitHub app for Astronuts connects your Astronuts account with your organizational GitHub account. You can [install the app](Connect-Git-Repositories.md) from the Astronuts dashboard from the **Settings | Integrations** page.
* Once installed, the app learns from your connected repositories based on training that you perform. You can [train Astronuts on your repositories](Setup-AI-Training.md) by navigating to **Intellidocs | Train** from the sidebar.
* The app also posts [comments on your pull requests](Pull-request-insights.md) and attaches labels indicating code quality.