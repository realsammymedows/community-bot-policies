# Privacy Policy for Community Bot

**Last updated: November 17, 2026**

Community Bot is run by Sammy (`sammymedows`) for the Medow Mafia community. It runs the Community Day player queue, subscriber roles, the stream schedule, moderation reports, optional feedback forms, stream-information commands, emote requests, and the **Apple Coins** community points program, including account setup, earning, spending and the Apple Coins pages on the Medow Mafia website. Discord also processes your activity under [Discord's Privacy Policy](https://discord.com/privacy).

## Operator and contact

The operator is Sammy, an individual streamer in California, United States. For privacy questions or requests, email **sammymedows@gmail.com** or send a Discord direct message to **sammymedows**.

The bot runs on the operator's computer. Some records are stored on the operator's network storage. Moderation reports and feedback may also be delivered to the operator's separate Roark Discord server.

## Information used

| Feature | Information used | Purpose |
|---|---|---|
| Queue and Squad Link | Discord user IDs, display names, voice-channel IDs, join times, queue position, game counts, paired-player IDs, invitation message IDs, and any Apple Coins entry ticket or skip used | Keep the queue, organize pairs, display participants, and move selected players between voice channels |
| Roles and permissions | Server and owner IDs, member role IDs and names, permission flags, and membership information looked up for specific members | Check queue, Apple Coins and feature access, maintain subscriber roles and restrict moderator controls |
| Commands | Command text and supplied arguments, caller ID and display name, role/permission information, and temporary cooldown timestamps | Return information and enforce permissions and cooldowns |
| Schedule | Operator-entered schedule text, dates and stream titles, public broadcast links/times, channel IDs, and the schedule message ID | Publish and update the stream schedule |
| Moderation | AutoMod rule/channel details, flagged account ID and name, account/server membership age, relevant role names, flagged text only if Discord provides it, and moderator decisions | Report suspected advertising and support moderator decisions |
| Optional feedback | User ID, Discord username and display name, submission time, topic, experience text, and answer text | Deliver identified feedback to Sammy |
| Apple Coins | Account setup and linked-account records, balances and a history of every coin added or spent, and the activity used to earn coins (described below) | Run the Apple Coins program |

Feedback is **identified, not anonymous**. A submitted answer can contain up to 1,000 characters, plus an experience field of up to 100 characters. The bot does not record voice audio. An avatar URL may be used to display the feedback author in Discord; the feature does not download and keep the avatar image.

## Apple Coins

Apple Coins is live. Taking part is optional, but you must set up an Apple Coins account to earn or spend coins.

**Account setup and linking.** Opening Apple Coins setup creates a basic record with your Discord ID, server ID, username and display name. A language choice can be saved before the consent step. Later steps record your consent and progress, watch preferences, the country you choose, Twitch or YouTube handles or links, verified platform account IDs and names, and verification details. Optional game details include edition, platform, launcher, account country or region, server, game UID, character name, and preferred reward account. Do not submit passwords or payment details.

To verify a Twitch or YouTube account, you may be asked to post a short code in one of Sammy's public stream chats, or to confirm through the website. The bot uses the sender's platform ID, name, message reference, source and time to match the code. The code message is public.

**How coins are earned.** Depending on the activity, the bot uses:

- **Stream attendance and streaks:** a `!here` check-in in Sammy's main Twitch or YouTube stream chat, with your platform ID, the stream and the time. Streak records use shared Twitch watch-streak counts and eligible main-stream YouTube chat participation; check-in records are kept separately.
- **Support:** paid and Prime subscriptions, gifted-subscription purchases, YouTube memberships, Super Chats, Super Stickers, Super Thanks and tips, with platform IDs, event IDs, tier, amount and time. Twitch Bits are still recorded but no longer earn new coins; YouTube Jewels gifts do not earn coins. Your chosen country is used for regional reward calculations. These records can include estimates when exact payment information is unavailable.
- **24/7 watching:** presence in the chat viewer list of Sammy's 24/7 Twitch channel, read from the operator's stream software, recorded as time intervals with your Twitch ID.
- **Moderator activity:** for members with the moderator role, messages in Discord channels that ordinary community members can see, and moderator messages in the main Twitch and YouTube chats. For **Discord**, the bot uses only the message ID, author ID, time, message type, whether the channel is community-visible and whether the author has the moderator role. **The Discord moderator-reward path currently does not receive or store ordinary message text.** Forms, command interactions and moderation reports are described separately below. For Twitch and YouTube moderator messages, the bot keeps the text only until the message is processed; it then keeps a one-way fingerprint (hash) of the wording, with no automatic deletion period, so the same wording does not earn twice in the same half-hour.
- **Past support:** when you activate or link an account, the operator's saved records of earlier subscriptions, gifts, tips and similar support may be matched to your verified platform IDs to add coins for past support. These records come from Twitch, YouTube, the operator's stream software logs and exports from tip and payment services. They also cover people who never signed up.
- **Owner adjustments and reversals:** the operator can add or correct coins, and coins earned from a payment that is later refunded can be taken back. Each change is recorded with a reason.

For ordinary viewers in Twitch and YouTube chat, the bot keeps only whether a message was a `!here` check-in, not the message text. It does not keep a conversation archive of Discord, Twitch or YouTube chat.

**Spending coins.** Coins can be spent on Community Day queue entry tickets and skips, and on predictions. The bot records each purchase, prediction and result. Spending in stream games is not turned on.

**Public replies.** The bot may post short public replies in Twitch or YouTube chat, such as a check-in confirmation that names you.

**Medow Mafia website.** You can sign in on the Medow Mafia website with Discord to see your own Apple Coins profile, balance and history, claim coins for past support, and send reports. The website asks the bot for your records over an authenticated connection. The website runs on cloud hosting (DigitalOcean) and is reached through Cloudflare. The website stores sign-in session records (including a hashed session token, your Discord ID, expiry and avatar URL), short-lived login verification state, and your saved country for the schedule. A secure session cookie keeps you signed in. It also stores build favorites, shared builds with their owner's ID and display name, and build-code reports with your Discord ID and report text. Apple Coins issue reports contain your Discord ID, the selected reason and your message, up to 2,000 characters. These reports are saved on the website server for private review; the current website does not send build-code reports to Discord.

**Private owner spreadsheet.** The operator keeps a private Google Sheets spreadsheet, restricted to the owner, listing consented Apple Coins members who have a verified Twitch or YouTube account. It includes Discord and platform IDs and names, the country you chose, coin totals and support history. Verification codes and chat messages are not included.

**Leaderboards.** There is currently no public coin leaderboard.

## Commands and message reading

Native Discord commands such as `/builds`, `/coins`, `/commands`, and `/command` receive the text supplied in the command interaction. They do not require access to ordinary channel conversations. Restricted commands require the configured moderator role, server ownership, or Administrator permission. The command handler does not save command text, fetch past channel messages, or send command text to an AI service. It keeps bounded cooldown records in memory.

**Discord's Message Content access is currently off for this bot.** Without it, Discord does not give the bot the text of ordinary channel messages. The bot can still receive content intentionally supplied through forms or command interactions, and messages that Discord makes available when they are addressed to it. The schedule feature checks messages from the operator in its schedule channel. The bot does not use Presence access to monitor online status, and it does not download a full server membership list; it looks up specific members when needed.

If Discord approves Message Content access and the operator turns it on in the future, it may be used to:

- recognize `!commands` in the server (this feature is currently off);
- include up to 600 characters of AutoMod-flagged text in moderation reports;
- **optionally**, check whether a Discord moderator message repeats the same wording in the same half-hour, so it earns once. This check is **not active for Discord**, is not needed for moderator rewards, and will not be turned on automatically. The operator will update this policy before turning it on.

There is no per-member switch to stop message delivery if this access is turned on. Discord message content is not used to train AI models.

## Storage and retention

- **Queue state:** Account IDs, voice-channel information, queue order, game counts, pairings, and invitation references are saved locally so a restart can restore the session. Opening or closing Community Day resets session records. Leaving the queue does not erase all records, such as game counts, purchases or logs.
- **Apple Coins records:** Profiles, current and former links, game records, consent and progress records, verification codes and their status, balances, the history of coins added and spent, earning activity, purchases, predictions, claims, reversals and related audit records are saved in local databases. Coin history is kept so balances can be checked and corrected; it has no automatic deletion period.
- **Short-lived records:** Pending earning events are stored until processed, then their content is removed; finished entries are deleted after about 2 days and failed entries after about 30 days. References used to reject duplicate verification messages are cleaned after about a day. Some code text is cleared when a code is cancelled, used or conflicts. Command cooldowns are held in memory only.
- **Website records:** Sign-in sessions expire after 7 days and login verification state after 10 minutes; expired rows are cleaned when a new sign-in starts. Saved schedule countries, shared builds and website issue and build reports have no automatic deletion period. Favorites remain until removed. These records are stored on the website server, separately from the bot's coin ledger.
- **Configuration:** Server, channel, role, and message IDs, exclusion IDs, schedule details, and settings remain until changed or removed.
- **Feedback:** Identified feedback is appended to topic files on network storage and sent to the operator's feedback channel in Roark. There is no automatic deletion period.
- **Ledger and logs:** Queue actions, pair changes, Community Day changes, moderation events, and errors are recorded in the bot's log file and an append-only activity ledger on network storage. Records can include names, account IDs, timestamps, action summaries and moderation details. They have no automatic deletion period.
- **Copies, exports and backups:** The operator makes local exports, backups and test copies of these records when updating or checking the bot. Deleting a live record does not automatically remove every copy.
- **Discord messages:** Queue displays, command replies, moderation reports, and feedback copies remain until edited or deleted. Discord's own retention practices also apply.

Records without an automatic deletion period require manual review and removal. The operator handles deletion requests and removes API data when no longer needed for the stated features, subject to applicable legal requirements; absence of an automatic timer is not a promise to retain data forever. Stopping or removing the bot does not automatically delete files, backups, activity records, or existing Discord messages.

## Where information goes

- **Discord:** responses, messages, role changes and voice-channel actions.
- **Twitch and YouTube:** the bot connects to read the relevant chats and events and to post public replies; Twitch subscriber lists for Sammy's channel are read through Twitch's API. These services process data under their own privacy practices.
- **The operator's own systems:** the operator's computers, stream software (Streamer.bot), control tools and network storage; the Roark Discord server for reports and feedback.
- **Service providers:** DigitalOcean and Cloudflare (website hosting and connection), Google (the private spreadsheet), and AI assistants from OpenAI and Anthropic, which the operator uses to build, maintain and check the bot. When doing that work, those assistants can process stored records on the operator's behalf. Approved emote requests can also be processed by OpenAI's ChatGPT/Codex and image generator in the operator's emote drafting workflow, which is currently paused.

The queue is shown in the community server, copied into the shared `!list` stream-chat response, and can be shown on stream. A local network feed gives participant names and queue information to stream tools; it has no login and anyone able to reach it on the network can read it.

The operator does not sell personal information or share it with advertisers or data brokers. Information is used to run the features described here.

## Emote requests

An emote request saves your Discord ID and display name, the emote name, description and notes, submission time, optional reference images, and review/workflow details. Up to two reference images can be downloaded and stored, with filenames, file type, size and checksums. The request card and images are posted in the request channel and are visible to people with access to that channel. Requests and review history are stored in a local database. Approved requests, including the requester's name/ID and images, are copied to the operator's network design queue for the AI drafting workflow described above. There is no automatic deletion period; rejection does not erase a request.

## Choices and requests

You can choose not to invoke commands, submit feedback or emote requests, set up Apple Coins, or add optional linked accounts and game details. Opening Apple Coins setup still creates the basic Discord record described above. Queue buttons let you leave or skip a session; they do not erase stored information. Restarting setup, changing a linked account, or removing a game can cancel or archive records rather than delete their history.

Depending on applicable law, you may have rights to access, correct, delete, restrict or object to processing, obtain a portable copy, withdraw consent where applicable, or complain to a privacy regulator. Send requests to **sammymedows@gmail.com** or Discord user **sammymedows**, identifying your account and the relevant feature. The operator may need to verify that the request concerns your account.

There is no self-service deletion button. Each kind of record (queue records, Apple Coins profiles, links and coin history, past-support records, game details, emote requests, feedback, reports, ledger entries, logs, exports and backups) is handled separately when you make a request. Bot controls do not erase copies held by Discord, Twitch, YouTube or other recipients. Updating your Discord profile does not automatically rewrite past records.

## Security

The bot connects to Discord, Twitch and YouTube using encrypted connections such as HTTPS, secure WebSockets and Twitch IRC over TLS. Credentials are kept in the operator's configuration and secret storage, not in the public policy repository. The website's connection to the bot requires a signed key. Access to files and private channels depends on account and permission controls.

**Application-level encryption is not installed yet.** As of November 17, 2026, the bot's databases, settings, logs and exports use ordinary file formats without application-level encryption. The operator's last administrator check (October 18, 2026) found that computer's drive was not encrypted; its current drive-encryption status has not been independently reconfirmed. Local backup and test copies also need to be covered by the storage-protection work. The network storage holding feedback, the activity ledger and the emote queue was not encrypted when checked on October 23, 2026. The website's sign-in, build and issue-report databases also currently use ordinary SQLite files without application-level encryption. Encryption of the cloud server's underlying disk and provider backups has not been verified. Encryption across all stored copies has not been verified. The operator is preparing storage-protection changes and will update this policy once those changes are installed and checked. No storage or transmission method guarantees absolute security.

## Children and changes

Discord requires users to meet its minimum age requirements. The bot is not intended to collect information from children below the applicable age; contact the operator if such information was submitted.

This policy may change with the bot's features. The date above identifies the current version. Material changes will be announced in the community server. Contact the operator with questions.

*Community Bot is independent and is not endorsed by or affiliated with Discord, Inc.*
