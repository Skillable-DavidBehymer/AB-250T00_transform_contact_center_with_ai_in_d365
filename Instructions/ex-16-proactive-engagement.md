---
lab:
    title: 'Exercise 16 - Configure a proactive engagement campaign'
    description: 'Enable proactive engagement, create an outbound SMS workstream, configure an AI-led renewal campaign with audience upload and reattempt logic, and review the proactive engagement dashboard.'
    duration: '35 minutes'
    level: 300
    islab: true
---

<!-- DERIK: This lab is currently blocked. When attempting to create a new proactive engagement campaign in the trial environment, an error is returned and the campaign cannot be created. This exercise needs to be revisited once the issue is resolved or a workaround is identified. The content below is preserved for reference. -->

<!--

# Exercise 16 - Configure a proactive engagement campaign

Contoso Coffee does not wait for customers to reach out — their retention team proactively contacts customers whose machine warranties are expiring to offer renewal plans. Without a configured outbound campaign, this means manual outbound calling, missed contacts, and no visibility into which customers have been reached. In this exercise, you will enable the proactive engagement feature, create an outbound SMS workstream, configure an AI-led renewal campaign with reattempt logic, and review the dashboard that shows campaign progress.

This exercise should take approximately **35** minutes to complete.

## Before you start

You must have completed **Exercise 01** (trial environment provisioned). Proactive engagement requires the **Dynamics 365 Contact Center** trial, which includes outbound messaging capabilities by default.

> **Note**: If you completed the voice channel provisioning in Exercise 07, you can optionally configure a voice outbound campaign instead of or in addition to the SMS campaign in this exercise. The steps for voice use the same campaign structure but require an outbound calling number.

## Task 1 - Enable proactive engagement

1. In **Copilot Service admin center**, in the left navigation under **Support experience**, select **Productivity**.

1. In the **Proactive engagements** section, select **Manage**.

1. Set **Enable proactive engagement** to **On**.

1. Select **Save**.

## Task 2 - Create an outbound SMS workstream

An outbound workstream defines the channel, dialing mode, and AI configuration for a proactive campaign.

1. In **Copilot Service admin center**, navigate to **Customer support** → **Workstreams**.

1. Select **+ New workstream**.

1. Enter:
   - **Name**: `Contoso Outbound SMS`
   - **Type**: `Messaging`
   - **Channel**: `SMS`
   - **Direction**: `Outbound`

1. Select **Next**.

1. Select **AI-led engagement** as the engagement type.

1. Set the **Dialing mode** to **Preview** (preview mode allows agents to review customer information before the message is sent).

1. Select **Create**.

## Task 3 - Configure the Contoso Renewal Campaign

1. In the left navigation, select **Proactive engagement** → **Campaigns**.

1. Select **+ New campaign**.

1. Enter:
   - **Name**: `Contoso Renewal Campaign`
   - **Description**: `Outbound warranty renewal outreach for Contoso Coffee machine customers`
   - **Workstream**: `Contoso Outbound SMS`

1. Select **Next**.

1. On the **Audience** step:
   - Select **Upload audience list**
   - Download and use the sample CSV template provided (or create a file with columns: `FirstName`, `LastName`, `PhoneNumber`, `ContractEndDate`)
   - Create a sample CSV with 3–5 rows of test data and upload it

    > **Note**: In a production environment, the audience list would be exported from Dynamics 365 Customer Insights or a CRM query. For this exercise, a manually created CSV is sufficient.

1. On the **Routing** step:
   - **Queue**: Select `Contoso Support Queue`

1. On the **Outcomes** step, create the following outcome reasons:
   - `Renewal accepted`
   - `Not interested`
   - `No answer`
   - `Voicemail left`

1. On the **Reattempt** step, configure:
   - **Maximum reattempts**: `3`
   - **Minimum gap between reattempts**: `24 hours`
   - **Do not reattempt if**: `Renewal accepted` or `Not interested`

1. On the **Frequency limits** step:
   - **Max messages per customer per day**: `1`
   - **Max messages per customer per week**: `3`

1. Review the summary and select **Create**.

## Task 4 - Review the proactive engagement dashboard

1. In **Copilot Service workspace**, in the left navigation under **Analytics**, select **Proactive engagement** (or navigate to **Copilot Service admin center** → **Analytics** → **Proactive engagement**).

1. Review the available metrics in the campaign dashboard:
   - **Contact rate** — percentage of outreach attempts that resulted in a response
   - **Outcome distribution** — breakdown of campaign outcomes (accepted, declined, no answer)
   - **Reattempt queue** — contacts scheduled for a second or third attempt

1. Return to **Copilot Service admin center** → **Campaigns** and select **Contoso Renewal Campaign**.

1. Set the campaign status to **Active** to begin processing the audience list.

    > **Note**: In a trial environment with test data, no actual SMS messages will be sent. The campaign will be queued for processing and you can observe the status update in the dashboard.

## Verification

This exercise is complete when:
- Proactive engagement is enabled
- **Contoso Outbound SMS** workstream exists with AI-led engagement and preview dialing mode
- **Contoso Renewal Campaign** exists with:
  - An uploaded audience list (even if test data only)
  - Routing to **Contoso Support Queue**
  - Four outcome reasons configured
  - Reattempt logic: max 3 attempts, 24-hour minimum gap
  - Frequency limit of 1 message per day / 3 per week
- You have reviewed the proactive engagement dashboard

-->
