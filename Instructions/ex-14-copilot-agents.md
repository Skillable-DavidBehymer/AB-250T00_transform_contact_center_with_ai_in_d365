---
lab:
    title: 'Exercise 14 - Configure the Customer Assist Agent and Copilot features'
    description: 'Verify Copilot prerequisites, connect knowledge sources, configure Customer Assist Agent for representative assistance, add a prompt plugin, and review Copilot analytics.'
    duration: '35 minutes'
    level: 300
    islab: true
---

# Exercise 14 - Configure the Customer Assist Agent and Copilot features

> [!NOTE]
> **Trial availability note**: The Customer Assist Agent and Copilot features covered in this exercise are generally available in Dynamics 365 Contact Center trials. The **Quality Assurance Agent** and **Service Operations Agent** bonus tasks at the end of this exercise may require additional capacity credits or specific trial configurations — complete them if available in your environment, and skip if not.

Contoso Coffee's agents handle complex troubleshooting questions across dozens of coffee machine models. Without AI assistance, they spend significant time searching for the right answer. In this exercise, you will configure Copilot to surface relevant knowledge articles automatically during conversations, set up the Customer Assist Agent for real-time representative guidance, add a prompt plugin that surfaces warranty information, and use the Copilot analytics report to understand adoption.

This exercise should take approximately **35** minutes to complete.

## Before you start

You must have completed **Exercises 01 and 13**. Copilot data movement must be enabled, and at least one published knowledge article must exist (the LCD Screen Troubleshooting article from Exercise 13).

## Task 1 - Verify Copilot prerequisites

1. In **Copilot Service admin center**, in the left navigation under **Support experience**, select **Productivity**.

1. Next to **Copilot settings**, select **Manage**.

1. On the **Copilot settings** page, confirm that the **Copilot side pane: let service team members chat with AI** checkbox is selected. If it is not, select it and then select **Save**.

1. Verify that **Cross-region data movement** is enabled for the environment. If it is not, open **Power Platform admin center**, select the **Contact Center Trial** environment, select **Settings** > **Features**, and enable it.

   > [!NOTE]
   > The **Cross-region data movement** option is only shown for non-US regions. For US-based trial environments, Copilot AI models are already hosted in region and no additional configuration is needed.

## Task 2 - Connect knowledge sources to Copilot

Copilot can only suggest relevant articles if it knows where to look. You will enable the Dynamics 365 knowledge base as a Copilot knowledge source through the Customer Support agent settings.

1. On the **Copilot settings** page, scroll to the **Agents within Copilot** section.

1. Next to **Customer Support**, select **Settings**.

1. On the **Customer Support** page, select the **Overview** tab.

1. In the **Instructions** field, enter the following custom prompt instructions:

   ``` plaintext
   You are assisting Contoso Coffee support representatives. Respond in a professional and friendly tone. Provide clear, concise guidance based on the knowledge base. Use bullet points or numbered steps when explaining troubleshooting procedures. If the knowledge base does not contain a clear answer, advise the agent to escalate the issue to Tier 2 support.
   ```

  > [!NOTE]
  > Custom instructions tell Copilot how to behave when responding to users. By specifying the tone, format, and escalation guidance here, you ensure that every Copilot response is consistent with Contoso Coffee's support standards — without agents needing to craft detailed prompts themselves. Instructions are applied to all **Ask a question** responses generated from the Dynamics 365 knowledge base.

1. In the **Knowledge sources** section, select the **Use your organization's knowledge base as knowledge source** checkbox.

1. Select **Save**.

  > [!NOTE]
  > This enables Copilot to use your published Dynamics 365 knowledge articles to answer agent questions and draft responses. The number of articles currently indexed is displayed next to the option.

## Task 3 - Configure Copilot features for agents

Copilot features are enabled per experience profile, so agents only see the capabilities relevant to their role.

1. In the left navigation under **Support experience**, select **Workspaces**.

1. Select **Manage** next to **Experience profiles**.

1. Select **Contoso Support Representative**.

1. In the **Copilot AI features** section, select **Edit.**

1. Enable the following features:

   | Feature | Setting |
   |---------|---------|
   | Ask a question | **On** |
   | Intent-based suggestions | **On** |
   | Write an email - help pane | **On** |
   | Live conversation summary | **On** |
   | Suggested actions view | **On** |
   | Case-based knowledge creation | **On** |

   Uncheck to disable the remaining features.

1. Select **Save and close**.

   > [!NOTE]
   > Features not enabled here will not appear in the agent's workspace, even if they are configured globally. Enabling only the features your agents need keeps the workspace focused and reduces distraction.

## Task 4 - Configure the Customer Assist Agent for representative assistance

> [!NOTE]
> The Customer Assist Agent may not be available in all trial environments. If you don't see it in your left navigation, skip this task and continue with Task 5.

The Customer Assist Agent provides real-time suggestions and guidance to agents during live conversations.

1. In **Copilot Service admin center**, in the left navigation under **Customer support**, select **AI Agents**.

1. Select **Customer Assist Agent**.

1. Select **Configure** or **Edit settings**.

1. Enable **Real-time representative assistance**: **On**

1. Enable **Conversation summaries**: **On**

1. In the **Knowledge sources** section, confirm the Dynamics 365 knowledge base is listed.

1. Select **Save**.

## Task 5 - Add a prompt plugin

<!-- DERIK: Consider whether this task belongs here. Prompt plugins are still in preview, require Copilot Studio capacity credits that trials may not have, and send learners to a second portal (make.powerapps.com) mid-exercise. For a 300-level contact center config course it's tangential — learners get more value from Tasks 1-4. Options: (1) cut entirely, (2) move to a bonus task, or (3) keep but add a skip note like Task 4. -->

Prompt plugins extend Copilot by letting agents trigger a predefined prompt that retrieves specific information. Creating a prompt plugin is a two-step process: first create the prompt in the Power Apps maker portal using AI Builder, then enable it in Copilot Service admin center.

### Step A - Create the prompt in AI Builder

1. Open a new browser tab and go to [**https://make.powerapps.com**](https://make.powerapps.com).

1. If the **Welcome to Power Apps** dialog appears, select **Get started**.

1. Confirm the **Contact Center Trial** environment is selected in the top-right corner.

1. In the left navigation, select **AI hub**, then under **Discover an AI capability**, select **Prompts**.

   > [!NOTE]
   > If you don't see **AI hub** in the left navigation, select **More** at the bottom of the nav to find it.

1. Select **Build your own prompt.**

1. In the top text box (it should say **Custom prompt** with the date and time), replace the text with your prompt's title: `Contoso Warranty Information`

1. Enter the following in the Instructions text box:

   ``` plaintext
   Summarize Contoso Coffee's standard 2-year warranty coverage for coffee machines. Include what is covered, what is excluded, and how to initiate a warranty claim.
   ```

1. Select **Save**.

### Step B - Enable the plugin in admin center

1. Return to **Copilot Service admin center**.

1. In the left navigation under **Support experience**, select **Productivity**.

1. Next to **Plugins for generative AI (Preview)**, select **Manage**.

1. In the plugin list, find **Contoso Warranty Information** and select it.

1. On the command bar, select **Turn on**.

1. On the **Select access type** screen, select **All agents who have Copilot**, then select **Next**.

1. On the **Define inputs (optional)** screen, leave all fields empty and select **Next**. You'll also see a **Responses** section with a "Don't summarize plugin responses" option — leave this unchecked so Copilot summarizes the response for agents.

1. On the **Plugin data** screen, select **Save this plugin's data in Dynamics 365 Copilot Transcript**, then select **Turn on plugin**.

1. When prompted, select **Publish changes**, then select **Confirm**.

   > [!NOTE]
   > It can take up to 15 minutes for the plugin to become available to agents. Agents access it from the Copilot pane by typing `/` to browse available plugins.

## Bonus tasks (complete if available in your trial)

### Bonus Task A - Configure the Quality Assurance Agent

> [!NOTE]
> The QA Agent evaluates conversations for quality scoring. Verify it is available in your trial before proceeding.

1. In **Copilot Service admin center**, select **Contact Center Agents**, then select **Quality Assurance Agent**.

1. Next to **Quality Assurance Agent**, select **Manage**.

1. Next to **Quality Evaluation**, select **Configure in detail**.

1. Enable the agent and configure connection references if prompted.

1. Under **Evaluation criteria score**, select the **Enable scoring for criteria** checkbox and set a **scoring threshold value** of `70` for chat conversations.

1. Select **Save**.

1. Select **Turn on**.

### Bonus Task B - Configure the Service Operations Agent

> [!NOTE]
> The Service Operations Agent provides conversational configuration assistance and orchestrates playbooks.

1. In **Copilot Service admin center**, select **Service Operations Agent**.

1. Test the agent by typing a configuration question such as `How do I create a new queue?` in the agent chat panel.

1. If a **Connect to continue** dialog prompts you to allow the **D365 Contact Center Admin MCP** connection, select **Allow**.

1. Verify that the agent provides a relevant response.

---

## Verification

This exercise is complete when:

- Copilot is enabled with cross-region data movement confirmed
- The Dynamics 365 knowledge base is enabled as a Copilot knowledge source in the Customer Support agent settings
- Copilot help pane, conversation summary, and draft email are enabled on the **Contoso Support Representative** experience profile
- The Customer Assist Agent is configured with real-time representative assistance on (if available in your environment)
- **Contoso Warranty Information** prompt plugin exists
