# Train your resources

To get the most out of Astronuts products, you would need to **train** Astronuts on your connected data.
This tutorial will guide you through the process of training Astronuts on your Git repositories.

The training process is similar for other data sources like Jira, Confluence, Bitbucket etc.

<tip>
    <p>
        You have full control over the training process and can choose the data you want to train on.
        Training allows you to get contextual information specifically for your context and perform RAG
        (retrieval augmented generation) based inferences with LLMs
        (Large Language Models), e.g., models from OpenAI (GPT4) and Meta (Llama3).
        Training happens on <b>private LLM instances</b> hosted by us, and your data is never shared with anyone.
        Most of Astronuts' features and capabilities are built on top of LLMs and RAG.
    </p>
</tip>

<procedure title="Train Astronuts on your Git repositories" id="connect-git-repos">
    <step>
        <p>Access the training page on your dashboard by navigating to <a href="https://dashboard.astronuts.io/intellidocs>"><b>Intellidocs | Train</b></a> from the sidebar.</p>
    <img src="intellidocs-training.png" alt="intellidocs training" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Locate the repository that you want to train. You can click the <b>Previous</b>
        and <b>Next</b> buttons to navigate through the table of your connected repositories.</p>
                <img src="intellidocs-training.png" alt="train git repo for intellidocs" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>Start the training process by selecting the <b>Train</b> action from the context menu.</p>
        <tip>
            <p>
                We recommend that you perform training in a <b>controlled way</b>.
                Releasing a large number of training jobs simultaneously may lead to jobs
                getting rejected by the system.
                Additionally training is an expensive operation and may lead to high costs if not managed properly.
                Please review the pricing pages
                to know more about your <b>training costs</b> and how you are charged for training.
            </p>
        </tip>
         <img src="intellidocs-training.gif" alt="start intellidocs training" border-effect="line" width="321" thumbnail="true"/>
    </step>
    <step>
        <p>The training will continue in the background and will show a <b>green check mark</b> once training succeeds.</p>
        <tip>
            <p>
                Training may take from seconds to minutes depending on various factors like the size of your Git repository and the current system capacity
                to perform training at Astronuts' end.
            </p>
        </tip>
         <img src="training-success-status.png" alt="intellidocs training success status" border-effect="line"/>
    </step>
    <step>
        <p>Repeat the above process for training additional resources.</p>
        <tip>
            <p>
                You can control various aspects of the training process from the <a href="https://dashboard.astronuts.io/intellidocs>"><b>Intellidocs | Settings</b></a> page.
            </p>
        </tip>
         <img src="intellidocs-settings.png" alt="intellidocs ai training settings" border-effect="line" width="321" thumbnail="true"/>
    </step>
</procedure>
