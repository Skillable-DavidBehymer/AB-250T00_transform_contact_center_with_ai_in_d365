---
lab:
    title: 'Exercise 08 - Test and validate your channel configuration'
    description: 'Send a test chat conversation through the Contoso Chat Widget, verify routing to the Contoso Support Queue, accept the conversation in the agent workspace, and confirm routing rules applied correctly.'
    duration: '20 minutes'
    level: 200
    islab: true
---

<!-- NOTE: This exercise has been merged into Exercise 06. The content below is preserved for reference only. -->

# Exercise 08 - Test and validate your channel configuration

> **Note**: The content of this exercise has been incorporated into **Exercise 06 - Configure the live chat widget** as Tasks 6, 7, and 8. You do not need to complete this exercise separately.

## Before you start

You must have completed **Exercises 04, 05, and 06**. You will need two browser windows or tabs:
- **Window 1**: Copilot Service workspace (agent view)
- **Window 2**: The chat widget test page (customer view)

## Task 1 - Open the agent workspace and set your presence

Before a conversation can be assigned to you, your presence must be set to an available status.

1. Open **Copilot Service workspace** from the application selector.

1. In the top-right corner of the workspace, check your status. Select **Available** from the status options. When your status is Available, you will see a green check mark.

    > **Note**: The routing engine only assigns conversations to agents with an available presence status. If you remain offline, conversations will queue but not be assigned.

## Task 2 - Send a test chat conversation

1. In a new browser tab, open **Copilot Service admin center**.

1. In the left navigation under **Customer support**, select **Channels**.

1. Select **Manage** next to **Chat**. Select **Contoso Chat Widget**.

1. Scroll to the **Code snippet** section and select **Copy** to copy the embed snippet to your clipboard.

1. Open **Notepad** (or any plain text editor) and paste the snippet.

1. Select **File** → **Save As**. Set **Save as type** to **All Files**, name the file `test.html`, and save it to your desktop.

1. Open **File Explorer**, navigate to your desktop, and double-click `test.html` to open it in your browser. The Contoso chat widget should appear in the corner of the page.

1. The pre-chat survey appears. Complete it:
   - **Consent question**: Accept
   - **First name**: `Alex`
   - Select **Submit**.

1. Type the following message in the chat window: `I need help with my Contoso coffee machine. The LCD screen is blank.`

1. Submit the message.

## Task 3 - Accept the conversation in the agent workspace

1. Switch back to the **Copilot Service workspace** tab.

1. A notification should appear indicating a new incoming conversation. Select **Accept**.

    > **Note**: If no notification appears after 30 seconds, verify that your presence is set to **Available** and that your administrator account is a member of **Contoso Support Queue**. Check the queue membership in Copilot Service admin center → Queues → Contoso Support Queue.

1. The conversation opens in a new session. In the communication panel, you can see the customer's message. (If it didn't open automatically, select **My work items (1)** from the lefthand pane, and select the **Visitor 1** work item.)

1. Review the **Conversation details** panel — confirm the customer's name (Alex) is populated from the pre-chat survey response.

1. Type a reply: `Hi Alex, I can help you with that. Let me look into your LCD screen issue.`

1. Send the reply and confirm it appears in the chat window on the test page.

<!-- REVIEW (Derik): Is "Conversation diagnostics" available in trial environments? It doesn't appear under Customer support > Routing in our trial. If not available, this task needs to be replaced or removed. -->

<!--
## Task 4 - Verify routing rule application

Routing rules run automatically before the conversation is assigned. Verify the classification and routing rules behaved correctly.

1. In the conversation session, look at the **Conversation details** section. Check the **Queue** field — confirm it shows **Contoso Support Queue**.

1. Navigate to **Copilot Service admin center** → **Customer support** → **Routing**.

1. Select **Manage** next to **Conversation diagnostics**.

1. Find the test conversation (search by the channel or timestamp). Review the diagnostics to confirm:
   - The **Work classification** step ran **Contoso Classification Rules**
   - The **Route-to-queue** step ran **Contoso Route-to-Queue Rules**
   - The conversation was routed to **Contoso Support Queue**

1. Close the test conversation by selecting **End** in the communication panel, then **End conversation**.
-->

1. Type a closing message to Alex: `I've looked into the LCD screen issue. Try holding the power button for 10 seconds to reset the display. If the problem persists, please contact us again and we'll arrange a replacement.`

1. Send the message and confirm it appears on the test page.

1. On the test page, type a reply as Alex: `That worked, thank you!`

1. Back in the Copilot service workspace, in the text box, select **Select text from a list of replies.** (This appears as a speech bubble with a lightning bolt.)

1. From the list of Quick replies, select **Have I answered all of your questions today?** and press **Send.**

1. As Alex, in the widget, reply `Yes.`

1. Close the test conversation by selecting **End** in the communication panel, then **End conversation**.

1. A conversation summary will appear, generated by Copilot. Ensure the summary matches what you expect.

1. Select **Close** to close the conversation. 

## Verification

This exercise is complete when:
- A test chat conversation successfully reached the **Copilot Service workspace** as an incoming notification
- The conversation was routed to **Contoso Support Queue**
- You were able to accept, reply, and close the conversation
