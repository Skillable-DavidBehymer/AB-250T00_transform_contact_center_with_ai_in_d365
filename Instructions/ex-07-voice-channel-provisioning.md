---
lab:
    title: 'Exercise 07 - Provision the voice channel'
    description: 'Provision the Dynamics 365 Contact Center voice channel by acquiring an ACS phone number, configuring a voice workstream, and setting up inbound routing.'
    duration: '25 minutes'
    level: 300
    islab: true
---

# Exercise 07 - Provision the voice channel

Contoso Coffee's contact center handles a significant volume of voice calls in addition to chat. In this exercise, you will provision the voice channel by acquiring a phone number through Azure Communication Services (built into your trial), create a voice workstream, and configure it for inbound calls.

This exercise should take approximately **25** minutes to complete.

## Before you start

You must have completed **Exercise 01** (trial environment provisioned). The voice channel is included in the Dynamics 365 Contact Center trial and is backed by Azure Communication Services.

## Task 1 - Acquire a phone number

1. In **Copilot Service admin center**, in the left navigation under **Customer support**, select **Channels**.

1. Next to **Phone numbers**, select **Manage**.

1. Select **+New number.**

1. On the **Features** page, configure:
   - **Country/Region**: `United States`
   - **Number type**: `Toll-free`
   - **Calling plans**: Select both **Receive calls** and **Make calls**
   - **SMS plans**: **Send and receive SMS**
   - **Location**: Select any area code

1. Select **Find numbers** to search for available numbers.

1. Review the **Summary** showing your assigned number, then select **Purchase phone number**. Your trial should automatically gain the phone number.

    > **Note**: The number must be purchased within 15 minutes of being assigned. After purchase, it appears in the phone numbers list with a status of **Ready for setup**.

1. Select **Done** to return to the **Phone numbers** page.

## Task 2 - Create a voice workstream

1. In the left navigation under **Customer support**, select **Workstreams**.

1. Select **+ New workstream**.

1. Select **Inbound**, then select **Next**.

1. In the **Create a workstream** dialog, enter:
   - **Name**: `Contoso Voice Workstream`
   - **Type**: `Voice`
   - **Work distribution mode**: `Push`
   - **Fallback queue**: Select **Create new** and name it `Contoso Voice Fallback Queue`

1. Select **Create**.

## Task 3 - Configure the voice channel settings

1. In the left navigation under **Customer support**, select **Workstreams**, then select **Contoso Voice Workstream**.

1. Select **Set up voice channel**.

1. On the **Channel details** step, enter:
   - **Name**: `Contoso Voice Channel`
   - Select **Next**.

1. On the **Phone number** step, select the phone number you acquired in Task 1, then select **Next**.

1. On the **Language** step:
   - **Primary language**: `English - United States`
   - Select **Next**.

    > [!TIP]
    > If time permits, explore the options on this step before moving on. Try changing the **Hold music** and **Wait music** to a different audio file. In the **Voice profile** section, experiment with the **Voice**, **Speaking speed**, and **Pitch** settings. Use the test phrase field to preview your changes with the text: `Thank you for calling Contoso Coffee support. I'm an AI agent. How can I help you today?`

1. On the **User features** step, configure the following:

   **Customer wait time**
   - Leave defaults.

   **Channel operating hours**
   - Leave defaults (no operating hours restriction).

   **Transcription and recording**
   - **Allow automatic pause and resume when agents hold and un-hold the customer**: **Yes**
   - **Show transcription by default**: **Yes**
   - **Request for user consent**: **Yes**

   **Consult**
   - **External phone numbers**: **On**
   - **External Teams users**: **On**

   **Transfer**
   - **External phone numbers**: **On**
   - **External Teams users**: **On**

   **Post-call survey**
   - Leave defaults.

1. Select **Next**.

1. Select **Create channel.** When the channel is done provisioning, select **Done.**

    The phone number status changes to **Connected** on the **Phone numbers** page.

## Verification

This exercise is complete when:
- A phone number appears in **Channels > Phone numbers** with status **Connected**
- **Contoso Voice Workstream** exists and has the phone number assigned
- The voice channel is configured with English (US), transfer, consult, and recording enabled
