# Connect issue management tool

To connect your Issue management tools, take the following steps.
This example assumes that you are connecting your organizational **[Atlassian Jira](https://www.atlassian.com/software/jira)** account.
The steps for other issue management tools are similar.

<tip>
    <p>
        If you don't use an issue management tool yet, you don't need to connect one with Astronuts.
        In that case some features of Astronuts might be unavailable to you,
        especially those which rely on your issue management tool for functioning.
    </p>
</tip>

<procedure title="Connect your Jira account" id="connect-jira-account">
    <step>
        <p>Access your <a href="https://dashboard.astronuts.io/"><b>Dashboard</b></a> or open a browser window and go to https://dashboard.astronuts.io/.</p>
    <img src="account-dashboard.png" alt="start dashboard" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Click on <b>Integrations</b> on the sidebar menu.</p>
        <img src="integrations-settings.png" alt="connect jira from integrations page" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Find your Issue management platform and click on <b>Install</b>.</p>
        <tip>
            <p>
                If you don't see your issue management tool, <a href="mailto:support@astronuts.io">email</a> us,
                or <a href="https://github.com/astronuts-app/astronuts-tracker/issues">create an issue</a> in our tracker.
            </p>
        </tip>
        <img src="install-jira-app.png" alt="install jira app" border-effect="line" width="321" thumbnail="false"/>
    </step>
    <step>
        <p>Review the pre-requisites and click on <b>Install</b> if you meet the pre-requisites.</p>
        <tip>
            <p>
                If you don't have the authority to install apps in your Jira account,
                <a href="Invite-team-members.md">invite someone</a> who has the authority
                or ask them to grant you authority.
                You can come back and install the app later by following the steps mentioned on this page.
            </p>
        </tip>
        <img src="jira-review-pre-requisites.png" alt="review pre-requisites and authority for jira app install" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Select your Atlassian Jira site where you want to install the app. To install, review the permissions being requested by the app and provide your consent by clicking on the <b>Accept</b></p> button.
        <img src="jira-install-and-authorize.png" alt="jira authorize and install" border-effect="line" width="321" 
        thumbnail="true"/>
    </step>
    <step>
        <p>Once the app is installed successfully, you will see a confirmation screen. </p>
        <img src="jira-install-success.png" alt="jira install confirmation" border-effect="line" width="700" 
thumbnail="false"/>
    </step>
    <step>
        <p>To confirm that Astronuts has access to your Jira projects, navigate to 
            <a href="https://dashboard.astronuts.io/intellidocs>"><b>Intellidocs | Train</b></a> from the sidebar, and look for your Jira projects</p>
        <tip>
            <p>
                It might a few seconds for Astronuts
                to connect to your Jira projects depending on the number of repos you have and their size.
            </p>
        </tip>
        <img src="review-jira-projects.png" alt="review connected jira projects" border-effect="line" width="321" 
        thumbnail="true"/>
    </step>
</procedure>
