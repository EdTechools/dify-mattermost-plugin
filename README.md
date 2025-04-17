**Author:** Jiahua Cui
**Version:** 0.0.2
**Type:** tool

### Overview 👀

> Mattermost is an open-core, self-hosted collaboration platform that provides persistent chat and ChatOps, workflow and toolchain automation, integrated voice, screen, file, and content sharing, as well as AI-enhanced information synthesis. The platform is designed to be fully extensible, supporting a rich ecosystem of third-party applications and integrations. Mattermost can be easily enhanced and customized through open APIs, developer frameworks, open-source customization, and community-driven enhancements.

This plugin contains two tools:

1️⃣ Incoming Webhook Integration:<br />
Enables external integrations to send messages to specific Mattermost channels through the webhook feature.

2️⃣ Bot Account Integration:<br />
Allows sending messages to designated Mattermost channels using bot accounts.

### 1️⃣. Incoming hook tool 🪝

#### Mattermost Configuration ⚙️

> Please refer to this website:
> https://developers.mattermost.com/integrate/webhooks/incoming/

1. In Mattermost, go to Product menu > Integrations > Incoming Webhook.
   > If you don’t have the Integrations option, incoming webhooks may not be enabled on your Mattermost server or may be disabled for non-admins. They can be enabled by a System Admin from System Console > Integrations > Integration Management. Once incoming webhooks are enabled, continue with the steps below.
2. Select Add Incoming Webhook and add a name and description for the webhook. The description can be up to 500 characters.
3. Select the channel to receive webhook payloads, then select Add to create the webhook.
   > You will end up with a webhook endpoint that looks like so:
   > https://your-mattermost-server.com/hooks/xxx-generatedkey-xxx<hr />
   > Treat this endpoint as a secret. Anyone who has it will be able to post messages to your Mattermost instance.

#### Configuring the Mattermost Tool ⚙️

1. Install the Mattermost tool from the marketplace.

2. Add the Mattermost node to your workflow.

3. Paste Incoming Webhook.

---

### 2️⃣. Bot Accounts tool 🤖

#### Mattermost Configuration⚙️

> Please refer to this website:
> https://developers.mattermost.com/integrate/reference/bot-accounts/

1. Go to System Console > Integrations > Bot Accounts.
2. Set Enable Bot Account Creation to true.

> Once set, System Admin can create bot accounts for integrations using the Integrations > Bot Accounts link in the description provided.

##### Using User interface (UI) to create bot accounts

1. Go to the Product menu and select Integrations > Bot Accounts.
2. Select Add Bot Account.
3. Set the Username of the bot. The username must begin with a letter, and contain between 3 and 22 lowercase characters made up of numbers, letters, and symbols including “.”, “-”, or “\_”.
4. (Optional) Upload an image for the Bot Icon. This will be used as the profile image of the bot throughout Mattermost.
5. (Optional) Set a Display Name and Description.
6. (Optional) Choose what role the bot should have. Defaults to Member. If you assign System Admin, the bot will have read and write access for any Public channels, Private channels, and Direct Messages.
7. (Optional) Select additional permissions for the account. Enable the bot to post to all Mattermost channels, or post to all Mattermost Public channels.
8. Select Create Bot Account.
9. Copy the token displayed on the Setup Successful page before you select Done as you won’t have access to the token again once you close the screen.

##### After the bot account is created, make sure to:

1. Copy the generated bot access token for your integration.
2. To add the bot account to teams and channels you want it to interact in, select the team drop-down menu, then select Invite People. Next, select Invite Member and enter the bot account in the Add or Invite People field. Then select Invite Members. You should now be able to add the bot account to channels like any other user.

#### Configuring the Mattermost Tool ⚙️

1. Install the Mattermost tool from the marketplace.
2. Add the Mattermost node to your workflow.
3. Enter the following information:
   - Mattermost server URL (domain and port)
   - Channel ID for message destination
   - Message type (select ephemeral if sending to a specific user, in which case you'll need to provide their user ID)
   - Bot account access token
