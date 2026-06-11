# Privacy Policy for Community Bot

**Last updated: June 11, 2026**

This Privacy Policy describes how **Community Bot** ("the Bot", "we", "us") collects, uses, stores, and shares information when you interact with it inside the Discord server in which it is installed. Community Bot is a self-hosted Discord bot that manages a "Community Day" viewer voice-channel queue and renders a weekly stream schedule message.

This policy is specific to Community Bot and is separate from [Discord's Privacy Policy](https://discord.com/privacy), which governs Discord's own handling of your data.

---

## 1. Data Controller

The data controller for Community Bot is:

- **Operator:** Sammy ("sammymedows"), an individual streamer self-hosting the Bot.
- **Jurisdiction:** California, United States
- **Contact:** sammymedows@gmail.com (you may also reach the operator via a direct message on Discord to `sammymedows`).

Community Bot is **self-hosted on the operator's personal computer**. It is not a multi-tenant cloud service. It runs in a single Discord server (the "Medow Mafia" server) and does not collect data from any other server.

The operator has assessed that a Data Protection Officer (DPO) is not mandatory under GDPR Article 37, because the Bot does not carry out large-scale systematic monitoring or process special-category data. The contact above remains the single point of contact for all privacy questions.

---

## 2. What Data the Bot Collects

Community Bot is built to collect the absolute minimum needed to run a voice-channel queue. **The Bot does not read message content** — the Discord Message Content intent is explicitly disabled in code.

### 2.1 Data the Bot processes in memory only (never written to disk)

| Data | Source | Purpose |
|---|---|---|
| Your Discord user ID | Discord gateway (voice state updates, button/select interactions, member cache) | Track who is in which tier voice channel, who is currently in the LIVE channel, who has opted out, and who has been "kept" for the next pull. |
| Which voice channel you are in (channel ID) | Discord gateway `VOICE_STATE_UPDATE` | Decide which tier (0/1/2/3) you belong to in the queue and whether you are in LIVE. |
| Your server display name | Discord member cache | Render your name in the public queue embed in `#the-list`, in the host Control Panel, in the Move/Remove dropdowns, and in the local HTTP `/line` response. **Not written to disk.** |
| Your bot flag (true/false) | Discord member object | Filter bot accounts out of the queue. |
| Your role IDs | Discord member cache | Check whether you hold the configured "blocked" role; if so, silently exclude you from the queue. The Bot reads role IDs only — no role names or other role metadata. |
| Your Discord permission flags (`move_members`, `manage_guild`, `administrator`) | Discord member object | Decide whether you may use the host/mod Control Panel buttons. |
| A voice-join timestamp | Generated locally when you enter a tier voice channel | Order viewers first-come-first-served inside a tier. Held in RAM only; never written to disk. |
| Server ID and server-owner user ID | Discord guild object | Identify the single configured server the Bot operates in, and grant the server owner access to the Control Panel and to hidden tier channels. |

All of the above is **session-scoped**. It is wiped when the Bot process restarts, when the host clicks **Close** or **Open** on Community Day, or when you leave all tier voice channels (your voice-state entry is then dropped).

### 2.2 Data the Bot writes to disk on the operator's machine

| File | Contents |
|---|---|
| `settings.json` | Queue configuration only: open/closed flag, active tiers, group size, random-pull flag, tier-priority flag, hidden-tiers list, and the Discord **message ID** of the public hub message the Bot edits in `#the-list`. **No user IDs, no usernames, no message content.** |
| `channel_snapshots.json` | A snapshot of each tier voice channel's existing Discord permission overwrites (role/member IDs, allow/deny bitfields) taken at the moment the channel was first hidden, so the original permissions can be restored later. In current operation, only **role** overwrites are present; no per-user entries. |
| `schedule.json` | The weekly stream schedule (timezone, weekday defaults, date-specific overrides, the schedule message's channel ID and message ID). **No user data.** |
| `.env` | Bot token and configuration IDs (guild ID, channel IDs, optional `EXCLUDE_USER_IDS` list, and the blocked-role ID). The `EXCLUDE_USER_IDS` entries are Discord user IDs — personal data — placed there manually by the operator to exempt specific users (e.g. the operator and co-hosts) from ever being pulled; they are retained until the operator removes them. Edited by the operator; not modified by the Bot at runtime. |

The Bot does **not** persist usernames, handles, avatars, email addresses, IP addresses, message content, voice audio, attachments, or any history of past sessions or past players.

### 2.3 Privileged intents

Community Bot uses two Discord gateway intents that affect what user data Discord forwards to it:

- **Server Members intent (privileged):** required to maintain the member cache so the Bot can resolve display names and role membership for queued users. Member data received via this intent is held in memory only and is not exported or persisted.
- **Voice States intent:** required to know who enters and leaves the tier voice channels.
- **Message Content intent: OFF.** The Bot cannot read what users type in chat. Its entire user-facing UX is buttons and ephemeral select menus.

---

## 3. Purposes of Processing and Lawful Basis (GDPR Article 6)

| Purpose | Lawful basis |
|---|---|
| Running the viewer queue (tracking voice presence, ordering the line, pulling viewers into LIVE, honouring opt-outs and the blocked role) | **Legitimate interest** (Art. 6(1)(f)) — operating a functional viewer queue inside a server you have voluntarily joined. A balancing test has been carried out; processing is limited to Discord IDs and transient display names, no profiling occurs, and you can opt out at any time via the **Leave** / **Skip Me** buttons. |
| Allowing host/moderators to authorise themselves to use the Control Panel | **Legitimate interest** (Art. 6(1)(f)) — necessary for safe administration. |
| Rendering the weekly stream schedule message | **Legitimate interest** (Art. 6(1)(f)) — no personal data is processed for this purpose. |
| Local HTTP `/line` endpoint exposing the current queue text to Streamer.bot on the LAN | **Legitimate interest** (Art. 6(1)(f)) — needed to surface the queue on the live stream overlay; only display names already visible inside the Discord channel are exposed. |

The Bot performs **no automated decision-making with legal or similarly significant effects** within the meaning of GDPR Article 22, and **no profiling**.

---

## 4. Where Data Is Stored

All persistent files (`settings.json`, `channel_snapshots.json`, `schedule.json`, `.env`) live on the operator's **local personal computer** at `C:\TOOLS\community-bot\`. The Bot is **not** hosted on any cloud provider, VPS, or third-party database. There is no off-site backup of Bot data, no analytics service, no error-tracking service (e.g., Sentry), and no AI/third-party API integration.

In-memory queue state (voice states, line, playing, opted-out, kept users) lives only in the Bot process's RAM and never touches disk.

The operator's computer is located in California, United States. Any data you submit by interacting with the Bot is processed there.

---

## 5. Who Data Is Shared With

Community Bot transmits data to the following recipients only:

1. **Discord, Inc.** — via the standard Discord Gateway (WSS) and REST API. This is unavoidable: the Bot is a Discord application, and operating a queue requires sending message edits, voice-channel moves, channel-permission edits, and component definitions to Discord. The data sent consists of Discord IDs (user, channel, role, guild, message), embed text built from display names and tier labels, button/select definitions, and permission-overwrite bitfields. Discord's handling of this data is governed by [Discord's Privacy Policy](https://discord.com/privacy).
2. **A local HTTP endpoint on the operator's LAN** (`GET /line` on TCP port 8767). This endpoint returns the current public queue as plain text — viewer display names and tier positions — with **no authentication**. Any device on the same local network as the operator's PC that can reach TCP 8767 can read the current line. This information is the same information already visible in `#the-list` inside Discord; no additional data (user IDs, role data, voice metadata) is exposed. The intended consumer is the operator's Streamer.bot instance.

The Bot makes **no other outbound network calls**: no analytics, no telemetry, no crash reporting, no third-party APIs, no webhooks, no cloud sync.

### International transfers

The Bot itself does not transfer data internationally. However, Discord, Inc. is based in the United States and your data is transmitted to Discord's infrastructure as part of any Discord interaction. This transfer is governed by Discord's own privacy framework, which relies on Standard Contractual Clauses and/or the EU-US Data Privacy Framework. Please refer to Discord's Privacy Policy for details.

The operator is established outside the EU/UK and has not appointed an EU or UK representative under GDPR Article 27 / UK GDPR Article 27, relying on the exemption for processing that is occasional, does not include large-scale processing of special categories of data, and is unlikely to result in a risk to the rights and freedoms of natural persons (Art. 27(2)(a)). EU/UK users may direct all inquiries to the contact in Section 11.

---

## 6. Retention

| Data | Retention |
|---|---|
| In-memory queue state (voice state, line, line order, playing, opted-out, kept, played-this-session) | Cleared when the host clicks **Close** or **Open** on Community Day, when the Bot process restarts, or when you leave all tier voice channels (your voice-state entry only). No history of past sessions is kept. |
| `settings.json` | Retained until the operator manually deletes the file or removes the Bot. Contains no personal user data beyond the streamer's own message ID. |
| `channel_snapshots.json` | A snapshot per tier voice channel is overwritten the next time that channel is hidden from a visible state. Retained until the operator manually deletes the file. Contains no user IDs in current operation (role overwrites only). |
| `schedule.json` | Retained until the operator manually deletes the file. Past date-specific overrides are automatically pruned from this file on each render once their date is in the past. Contains no user data. |
| `.env` | Retained by the operator; not modified at runtime. |

When the Bot is removed from the server, or when the operator stops self-hosting it, all in-memory data ceases to exist immediately and all on-disk data can be wiped by deleting the `C:\TOOLS\community-bot\` directory.

---

## 7. Your Rights

If you are located in the European Economic Area, the United Kingdom, or another jurisdiction that grants equivalent rights, you have the right to:

- **Access** (GDPR Art. 15) — request a copy of the personal data the Bot holds about you. In practice, this is at most your Discord user ID and current voice-channel/line position, all held in memory.
- **Rectification** (Art. 16) — request correction of inaccurate data. Display names are pulled live from Discord; update your Discord profile to correct them.
- **Erasure / "right to be forgotten"** (Art. 17) — request deletion of your data. Because almost all data is in RAM, you can effectively erase yourself at any time by clicking **Leave** or **Skip Me** in `#the-list`, by leaving the tier voice channels, or by waiting for the next Community Day close/open or Bot restart.
- **Restriction of processing** (Art. 18).
- **Data portability** (Art. 20) — request your data in a machine-readable format (JSON).
- **Objection** (Art. 21) — object to processing based on legitimate interest. The simplest mechanism is to click **Leave** / **Skip Me** or to not join a tier voice channel.
- **Withdraw consent** (Art. 7(3)) — where any processing is based on consent.
- **Lodge a complaint** with your local data protection supervisory authority. In the EU, a list is available at https://edpb.europa.eu/about-edpb/about-edpb/members_en.

To exercise any right that is not satisfied by the in-app buttons, contact the operator at **sammymedows@gmail.com** or via Discord DM to `sammymedows`. The operator will respond within one month of receiving a verifiable request, in line with GDPR Article 12(3).

### California residents (CCPA / CPRA)

The operator does not currently meet the thresholds that make CCPA/CPRA compliance mandatory. As a matter of good practice, California residents may nevertheless exercise rights to know, delete, correct, and opt out of any "sale" or "sharing" of personal information by contacting the operator at the address above. **The operator does not sell or share personal information** within the meaning of the CPRA.

### Guild owners

If you are the owner or administrator of a Discord server in which Community Bot has been installed, you can purge all guild-level data by removing the Bot from the server and asking the operator to delete the on-disk files associated with your guild.

---

## 8. Security

The Bot runs as a local Python process on the operator's personal computer. Security measures include:

- The Discord bot token is stored only in the local `.env` file and is excluded from backups and source-control sharing.
- No data is transmitted to third parties beyond Discord's own APIs.
- The HTTP `/line` endpoint listens on all network interfaces of the host machine (TCP port 8767) but exposes only the current queue display names and tier labels (information already visible inside Discord). The host machine sits behind a residential NAT router with no port forwarding for 8767, so in practice the endpoint is reachable only from the operator's local network; the operator is responsible for keeping it unexposed to the public internet.
- Access to the host machine is controlled by the operator's local OS account.

No method of transmission or storage is 100% secure. In the event of a personal-data breach that is likely to result in a risk to your rights and freedoms, the operator will notify the competent supervisory authority within 72 hours (GDPR Art. 33) and, where the risk is high, will notify affected users without undue delay (Art. 34).

---

## 9. Children

Discord's own Terms of Service require users to be at least 13 years old (or older where local law requires, e.g. 16 in some EU Member States). Community Bot relies on Discord's age enforcement and **does not knowingly process data of users below the applicable minimum age**. If you believe a user below that age has interacted with the Bot, please contact the operator and any data associated with that user will be removed.

---

## 10. Changes to This Policy

This policy may be updated from time to time to reflect changes in the Bot or in applicable law. The "Last updated" date at the top of the document will always reflect the most recent version. Material changes will be announced in the Discord server where the Bot operates (typically in `#the-list` or the server's announcements channel) with reasonable notice. Continued use of the Bot after an update constitutes acceptance of the revised policy.

---

## 11. Contact

For any privacy question, data-subject request, or complaint about Community Bot:

- **Email:** sammymedows@gmail.com
- **Discord:** DM `sammymedows`

---

*Community Bot is an independent project and is not endorsed by, affiliated with, or sponsored by Discord, Inc.*
