# Connect Git Repositories

To connect your Git repositories, take the following steps.
This example assumes that you are connecting a GitHub account.
The steps for other Git providers are similar.

<procedure title="Connect your Git repositories" id="connect-git-repos">
    <step>
        <p>Access your <a href="https://dashboard.astronuts.io/"><b>Dashboard</b></a> or open a browser window and go to https://dashboard.astronuts.io/.</p>
    <img src="account-dashboard.png" alt="start dashboard" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Click on <b>Integrations</b> on the sidebar menu.</p>
        <img src="integrations-settings.png" alt="connect git repo from integrations page" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Find your Git provider platform and click on <b>Install</b>.</p>
        <tip>
            <p>
                If you don't see your provider, <a href="mailto:support@astronuts.io">email</a> us,
                or <a href="https://github.com/astronuts-app/astronuts-tracker/issues">create an issue</a> in our tracker.
            </p>
        </tip>
        <img src="install-github-app.png" alt="install github app" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Review the pre-requisites and click on <b>Install</b> if you meet the pre-requisites.</p>
        <tip>
            <p>
                If you don't have the authority to install apps in your organizational account,
                <a href="Invite-team-members.md">invite someone</a> who has the authority
                or ask them to grant you authority.
                You can come back and install the app later by following the steps mentioned on this page.
            </p>
        </tip>
        <img src="git-review-pre-requisites.png" alt="review pre-requisites and authority" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Depending on the tool you are trying to connect, you will see an application-specific page asking you to take actions specific to your Git provider. Choose the options that apply to you</p>
        <tip>
            <p>
                For GitHub, we currently support only organizational Git accounts.
                We plan to remove this restriction in the future.
                Keep a watch on the <a href="https://github.com/astronuts-app/astronuts-tracker/milestones">Astronuts roadmap</a> for updates.
            </p>
        </tip>
        <img src="choose-git-account.png" alt="review pre-requisites and authority" border-effect="line" width="321" 
        thumbnail="true"/>
    </step>
    <step>
        <p>Review the permissions being requested by the app and provide your consent. For example, click on <b>Install & Authorize</b></p>
        <img src="git-install-and-authorize.png" alt="git authorize and install" border-effect="line" width="321" 
        thumbnail="true"/>
    </step>
    <step>
        <p>Once the app is installed successfully, you will see a confirmation screen. </p>
        <img src="git-install-success.png" alt="git install confirmation" border-effect="line" width="700" 
thumbnail="false"/>
    </step>
    <step>
        <p>To confirm that Astronuts has access to your Git repositories, navigate to 
            <b>Intellidocs | Train</b> from the sidebar.</p>
        <tip>
            <p>
                It might a few seconds for Astronuts
                to connect to your repositories depending on the number of repos you have and their size.
            </p>
        </tip>
        <img src="review-git-repos.png" alt="review connected git repos" border-effect="line" width="321" 
        thumbnail="true"/>
    </step>
</procedure>