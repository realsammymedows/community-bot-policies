# Privacy Policy for Community Bot

**Last updated: October 19, 2026**

Community Bot is operated by Sammy (`sammymedows`) for the Medow Mafia community. It manages the Community Day player queue, subscriber roles, a stream schedule, moderation reports, optional feedback forms, stream-information commands, optional Apple account setup and verification, and emote requests. Discord also processes your activity under [Discord's Privacy Policy](https://discord.com/privacy).

## Operator and contact

The operator is Sammy, an individual streamer in California, United States. For privacy questions or requests, email **sammymedows@gmail.com** or send a Discord direct message to **sammymedows**.

The bot runs on the operator's computer. Some records are stored on the operator's network storage. Moderation reports and feedback may also be delivered to the operator's separate Roark Discord server.

## Information used

| Feature | Information used | Purpose |
|---|---|---|
| Queue and Squad Link | Discord user IDs, display names, voice-channel IDs, join times, queue position, game counts, paired-player IDs, and invitation message IDs | Keep the queue, organize pairs, display participants, and move selected players between voice channels |
| Roles and permissions | Server and owner IDs, member role IDs and names, permission flags, and relevant membership information | Check queue and feature access, maintain participant subscriber roles and restrict moderator controls |
| Commands | Command text and supplied arguments, caller ID and display name, role/permission information, and temporary cooldown timestamps | Return information and enforce permissions and cooldowns |
| Schedule | Operator-entered schedule text, dates and stream titles, public broadcast links/times, channel IDs, and the schedule message ID | Publish and update the stream schedule |
| Moderation | AutoMod rule/channel details, flagged account ID and name, account/server membership age, relevant role names, available flagged text, and moderator decisions | Report suspected advertising and support moderator decisions |
| Optional feedback | User ID, Discord username and display name, submission time, topic, experience text, and answer text | Deliver identified feedback to Sammy |

Feedback is **identified, not anonymous**. A submitted answer can contain up to 1,000 characters, plus an experience field of up to 100 characters. The bot does not record voice audio. An avatar URL may be used to display the feedback author in Discord; the feature does not download and keep the avatar image.

## Optional account setup and chat proof

Opening Apple account setup creates a basic record with your Discord ID, server ID, username and display name. A language choice can be saved before the setup consent step. Later optional steps record consent and progress, watch preferences, Twitch or YouTube handles or links, verified platform account IDs, and verification details. Optional game details include edition, platform, launcher, account country or region, server, game UID, character name, and preferred reward account. Do not submit passwords or payment details.

To verify a Twitch or YouTube account, you may be asked to post a short code in one of Sammy's configured public stream chats and confirm the matched account in Discord. The bot reads those chats through Twitch IRC or the YouTube API to find codes. It uses the sender's platform ID, name, message reference, source and time. The code message is public. Ordinary messages without a code are ignored by this proof feature rather than saved as a conversation archive. This statement does not describe other stream-chat systems.

Setup profiles, current and former links, game records, consent/progress records, verification codes and their status, and event history are saved in local databases. Codes have an expiry for use; expiry does not mean all code and verification records are deleted. Some code text is cleared when a code is cancelled, consumed or conflicts. Delivery references used to reject duplicate proof events are cleaned after about a day when further events are processed. Other profile and verification records have no automatic deletion period. Local exports and backup copies may also exist.

As of this update, signup and chat proof remain enabled in the restricted pilot. New subscription-history checks and the new Apple rewards launch are paused. Existing history is retained: it can include linked account and channel IDs, subscription months, recorded or estimated tiers, paid/Prime/gift evidence, gifter account IDs, timestamps and review notes. A separate imported evidence index also retains historical platform account IDs and names, subscriber snapshots and subscription events from operator-held platform records and stream logs; those records are not limited to people who completed this signup. Pausing the feature does not erase these records. This setup bot does not currently issue Apple rewards; separate existing stream points continue under their own system.

## Emote requests

An emote request saves your Discord ID and display name, the emote name, description and notes, submission time, optional reference images, and review/workflow details. Up to two supplied reference images can be downloaded and stored, with filenames, file type, size and checksums. The request card and saved reference images are posted in the request channel and are visible to people with access to that channel, not just the operator.

Requests and review history are stored in a local database. Approved requests, including the requester name/ID and reference images, are copied to the operator's network design queue. They can be used by the operator's AI-assisted drafting workflow to create an emote concept. The bot itself does not call an image-generation API or automatically publish an emote to a platform. Generated drafts and workflow records may be kept alongside the approved request. There is no automatic deletion period for these records or saved images; rejection does not erase them.

The separate automated drafting task is paused as of this update; approved files remain stored. When an approved request is processed by the configured AI drafting workflow, it uses OpenAI's ChatGPT/Codex and its built-in image generator. Approved job files, including the requester's name/ID and supplied design material, are made available to ChatGPT/Codex; design text and reference images can also be sent to the image generator. Processing by those services follows their applicable terms and the operator's account settings; this policy does not promise a particular provider retention period or training setting.

## Commands and message reading

Native Discord commands such as `/builds`, `/coins`, `/commands`, and `/command` receive the text supplied in the command interaction. They do not require access to ordinary channel conversations. Responses come from the shared stream-command catalogue. Public responses can contain a supplied target name or the caller's display name. Restricted commands require the configured moderator role, server ownership, or Administrator permission.

The command handler does not save command text or fetch past channel messages. It keeps bounded cooldown records in memory. It does not send command text to an AI service or use it to train models.

Ordinary channel `!commands` require Discord's Message Content permission and are currently disabled. If enabled after approval, the feature examines newly delivered messages in the configured server to recognize commands. It ignores direct messages, bots, webhooks, and other servers. Ordinary messages do not trigger a response. There is no separate per-member switch preventing message delivery when this permission is enabled.

The bot can still receive content intentionally supplied through forms or command interactions, and messages that Discord makes available when addressed to it. The schedule feature checks messages from the operator in its configured channel. The bot does not use Presence access to monitor online status. In its current mode, it uses information from voice events and interactions plus specific-member lookups for relevant participants; it does not download a full server membership list. Guild-wide subscriber-role synchronization is currently paused.

Message Content access also affects AutoMod events. Without it, reports ordinarily contain rule and account details without the message text. If Discord provides flagged text, the moderation feature may include up to 600 characters in its report. Those reports can be retained in Discord, logs, and reporting systems. The command handler's no-storage behavior does not apply to moderation reports or submitted feedback.

## Storage and retention

- **Queue state:** Account IDs, voice-channel information, queue order, game counts, pairings, and invitation references are saved locally so a restart can restore the session. Opening or closing Community Day resets relevant session records. Leaving the queue does not erase all records, such as game counts or logs.
- **Configuration:** Server, channel, role, and message IDs, exclusion IDs, schedule details, and settings remain until changed or removed. Older snapshots may remain in backups.
- **Cooldowns:** Command cooldowns are held in memory with a bounded per-user cache, cleared on restart or eviction.
- **Feedback:** Identified feedback is appended to topic files on network storage. The feature also attempts to deliver it to the operator's feedback channel in Roark. There is no automatic deletion period.
- **Ledger and logs:** Queue actions, pair changes, Community Day changes, moderation events, and errors may be recorded in logs and an append-only network-storage ledger. Records can include names, account IDs, timestamps, action summaries, and moderation details. The ledger writer has no automatic deletion period.
- **Backups:** Operational files may remain in backups until removed. Deleting a live record does not automatically remove every backup copy.
- **Discord messages:** Queue displays, command replies, moderation reports, and feedback copies remain until edited or deleted. Discord's own retention practices also apply.

The command catalogue contains operator-maintained responses and settings plus the current queue text used by `!list`; it is not a viewer-message archive. Records without an automatic deletion period remain until removed by the operator. Stopping or removing the bot does not automatically delete files, backups, activity records, or existing Discord messages.

## Where information goes

The bot sends responses, messages, role changes, and voice-channel actions to Discord. Twitch and YouTube process public chat proof under their own privacy practices; the bot connects to those services to read the relevant chats. Approved emote requests also enter the operator's design workflow described above. It also sends moderation reports and feedback to the operator's Roark server or reporting service and saves the records described above on the operator's computer or network storage.

The queue is displayed in the community server, copied into the shared `!list` stream-chat response, and can be used on stream. A local HTTP feed provides participant names and queue information to stream tools. The feed has no application-level login and listens on the host's network interfaces; devices able to reach it can read it. Its exposure depends on firewall and network settings.

Public replies are visible to people who can view the channel. Feedback and moderation destinations are intended for the operator and authorized reviewers; access follows their channel and storage permissions. The operator does not sell personal information. Information is used to operate the features described here.

## Choices and requests

You can choose not to invoke commands, submit feedback or emote requests, or complete optional account-linking and game details. Opening account setup still creates the basic Discord record described above. Queue buttons let you leave or skip a session; they do not erase all stored information. Restarting setup, changing a linked account, or removing a game from the active list can cancel or archive records rather than delete their history.

Depending on applicable law, you may have rights to access, correct, delete, restrict or object to processing, obtain a portable copy, withdraw consent where applicable, or complain to a privacy regulator. Send requests to **sammymedows@gmail.com** or Discord user **sammymedows**, identifying your account and the relevant feature. The operator may need to verify the request concerns your account.

Saved queue records, signup profiles, former account links, verification and subscription history, game details, emote requests/images/drafts, exports, feedback, reports, ledger entries, logs, and backups need to be considered separately for deletion. Bot controls do not erase copies held by Discord, Twitch, YouTube or other recipients. There is no complete self-service deletion button; contact the operator for a request. Updating a Discord profile does not automatically rewrite historical records.

## Security

The bot connects to Discord through HTTPS and secure WebSockets. Credentials are kept in operator-controlled configuration and secret storage, not the public policy repository. Access to files and private channels depends on account and permission controls.

Operational data is stored in JSON, text, SQLite databases and image files; these features do not themselves provide file encryption. As of October 18, 2026, the operator's computer drive that holds the bot's live files, including its local databases, queue state and settings, does not use Windows drive encryption. The encryption status of the operator's network storage and backups has not been verified, so this policy does not claim those copies are encrypted. No storage or transmission method guarantees absolute security.

## Children and changes

Discord requires users to meet its minimum age requirements. The bot is not intended to collect information from children below the applicable age; contact the operator if such information was submitted.

This policy may change with the bot's features. The date above identifies the current version. Material changes will be communicated in the community server. Contact the operator with questions.

*Community Bot is independent and is not endorsed by or affiliated with Discord, Inc.*
