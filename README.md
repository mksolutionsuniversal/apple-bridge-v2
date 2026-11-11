<div align="center">

# 🍎 Apple Bridge v2

### Your Apple world. One intelligent bridge.

**A private, local-first Model Context Protocol (MCP) integration for macOS, developed by MK Universal Solutions Ltd.**

<p>
  <img alt="Project status: operational private deployment" src="https://img.shields.io/badge/Status-Operational-18794e?style=for-the-badge" />
  <img alt="53 registered MCP tools in LOCAL" src="https://img.shields.io/badge/LOCAL%20Tools-53-3066be?style=for-the-badge" />
  <img alt="11 read-only tools in independent CLOUD" src="https://img.shields.io/badge/CLOUD%20Tools-11%20read--only-286c8e?style=for-the-badge" />
  <img alt="Latest verified basic diagnostics: 9 of 9 OK" src="https://img.shields.io/badge/Diagnostics-9%2F9%20OK-18794e?style=for-the-badge" />
  <img alt="Platform: macOS" src="https://img.shields.io/badge/Platform-macOS-343a40?style=for-the-badge" />
</p>

**[Overview](#overview) · [Capabilities](#what-it-can-do) · [Cloud](#independent-apple-bridge-cloud) · [Tool catalogue](#all-53-registered-mcp-tools) · [Architecture](#how-it-works) · [Security](#designed-with-control-in-mind) · [Status](#verified-operational-status)**

</div>

---

> [!NOTE]
> **This is the public project showcase, not a source-code distribution.** The production implementation, infrastructure configuration and development history are maintained in a separate private repository. This repository intentionally contains no live credentials, account mappings, private deployment details or personal data.

## Overview

**Apple Bridge v2** connects an authorised AI assistant with supported Apple services available to a macOS user. It brings together communication, organisation, account-aware discovery and selected local information in a single MCP interface.

The project focuses on making Apple services **useful in real workflows**, not simply exposing a collection of commands. The primary, macOS-based **Apple Bridge LOCAL** deployment exposes **53 registered MCP tools**, including read-only diagnostics. The independent post-restart check on 10 November 2026 confirmed a working ChatGPT connection and **9/9 basic diagnostic checks OK**.

As of 11 November 2026, MK Universal Solutions Ltd also operates **Apple Bridge Cloud**, a **separate, read-only MCP deployment** with **11 registered tools**. It provides limited access to selected remote accounts when the Mac is unavailable. The two endpoints use separate connections and **do not automatically fail over**.

<details>
<summary><strong>Why build it?</strong></summary>

Many daily activities are spread across Mail, Calendar, Contacts, Notes, Messages and other applications. Apple Bridge v2 aims to give an authorised AI assistant a consistent, controlled way to work with those services while retaining macOS permissions, explicit account selection and user oversight.

</details>

## What it can do

| Area | Capabilities |
|:--|:--|
| 📧 **Mail** | Browse, search, read and manage messages, with explicit account selection for supported operations |
| 📅 **Calendar** | Find calendars and events; create, update and remove events where authorised |
| 👥 **Contacts** | Search and manage contacts, with visibility into supported account containers |
| ✅ **Reminders** | Browse lists, find tasks, create reminders and manage completion |
| 📝 **Notes** | Browse folders, search notes and access supported note operations |
| 💬 **Messages** | Read conversations, send text or supported attachments, select iMessage/SMS routing, safely fall back to SMS for eligible text sends, and target a specific message with a Tapback reaction |
| 🌐 **Safari** | Inspect and manage supported browser tabs |
| 📞 **Call history** | Read-only access to call records available to the local macOS user |
| 🔗 **People & account discovery** | Discover live service accounts, identify ambiguous or stale mappings, and maintain explicitly confirmed person-to-account links and aliases |
| ❤️ **SKS PersonalHealth** | Read-only access to separately received local health projections, including available health status, samples and ECG metadata/data through defined tools |
| 🩺 **Diagnostics** | Read-only checks of MCP registration, host, secure tunnel, local SKS service/projection and Messages bridge readiness |

The availability of individual operations depends on the selected deployment, configured services, permissions and connected client. **The LOCAL catalogue of 53 tools and the separate Cloud catalogue of 11 tools are distinct; registration does not prove every possible functional scenario.**

## Highlights from the latest private build

- **Account-aware workflows:** live discovery across supported Apple services, confirmed person aliases, and explicit account mapping without guessing an owner.
- **Safer message delivery:** `auto`, `imessage` and `sms` routing, with conditional text-only iMessage-to-SMS fallback where the original send is known not to have started. Uncertain sends are not retried blindly.
- **Targeted Tapbacks:** reactions refer to a specific message; bridge readiness is checked separately from real-world reaction delivery.
- **Resilient local operations:** the Messages bridge and SKS health endpoint recovered after a full Mac restart in the recorded acceptance test. The Messages bridge may take several minutes to become ready after login.
- **Privacy-conscious health access:** read-only views of a separately managed local SKS projection; no health records are included in this repository.
- **Built-in diagnostics:** a read-only `diagnostics` tool reports readiness and health-check results without launching Apple applications in basic mode.
- **Independent cloud continuity:** a separately hosted, read-only service allows authorised access to selected Mail, Calendar and Contacts sources without requiring the local Mac to be running.
- **Clear Google routing:** Google Calendar and Gmail, where connected, are handled by ChatGPT’s native Google integrations, not by Apple Bridge Cloud.

## Independent Apple Bridge Cloud

**Apple Bridge Cloud** is a second, independent private production service for limited **read-only** access while Apple Bridge LOCAL is offline. It runs in an isolated Linux container with its own authorised MCP connection and separate secure tunnel. It is **not** a copy of the full macOS feature set, and **no automatic failover** is implemented.

| Capability | Apple Bridge LOCAL | Apple Bridge Cloud |
|:--|:--|:--|
| Hosting | Authorised macOS computer | Independent Linux/Docker environment |
| MCP tools | **53 registered** | **11 registered, read-only** |
| Mail | Supported local Mail functions, including authorised writes | Read/search selected iCloud and private IMAP mailboxes (**5 accounts**) |
| Calendar | Supported local calendar functions, including authorised writes | Read-only selected iCloud calendars (**2 accounts**) |
| Contacts | Supported local contacts functions, including authorised writes | Read-only selected iCloud contacts (**1 account**) |
| Messages, Reminders, Notes, Safari, call history and SKS Health | LOCAL-specific capabilities | **Not available** |
| Connection | Dedicated private MCP connection | Separate private MCP connection |

The Cloud interface provides two service/inventory tools (`about`, `list-service-accounts`) and nine read-only data tools: `list-emails`, `read-email`, `search-emails`, `list-folders`, `list-calendars`, `list-events`, `list-contacts`, `search-contacts` and `read-contact`. Account-scoped operations require an explicit authorised account identifier.

### Google accounts: native ChatGPT integrations

Google accounts are **intentionally not configured in Apple Bridge Cloud**. When the user has authorised the relevant connections, ChatGPT can use its **native Google Calendar and Gmail integrations** to work with those accounts. This routing is performed by the assistant, **not** by the Cloud MCP server; it depends on the client’s available connections and permissions. The Cloud server does not proxy, authenticate or independently connect to Google services.

The deployment is private and is not offered as a hosted public service. This public showcase intentionally omits source code, connection identifiers, account addresses, credentials, private network locations and operational recovery materials.

## All 53 registered MCP tools

The names below describe the **actual MCP tool interface** present in the private production build. They are published for transparency and discovery, **not as API access to the private server**. Tool execution depends on permissions, mode and the connected client's authorisation.

<details>
<summary><strong>Show the full 53-tool catalogue by category</strong></summary>

| Category | Tools | Registered MCP tool names |
|:--|--:|:--|
| Core & connection | 3 | `about`, `check-auth-status`, `set-mode` |
| Mail | 6 | `list-emails`, `read-email`, `send-email`, `search-emails`, `mark-as-read`, `list-folders` |
| Calendar | 5 | `list-events`, `create-event`, `update-event`, `delete-event`, `list-calendars` |
| Contacts | 7 | `list-contacts`, `search-contacts`, `read-contact`, `create-contact`, `delete-contact`, `list-contact-accounts`, `list-contact-groups` |
| Reminders | 7 | `list-reminder-lists`, `list-reminders`, `create-reminder`, `update-reminder`, `complete-reminder`, `delete-reminder`, `search-reminders` |
| Notes | 5 | `list-note-folders`, `list-notes`, `read-note`, `create-note`, `search-notes` |
| Messages | 4 | `list-chats`, `read-messages`, `send-message`, `react-message` |
| Safari | 4 | `list-safari-tabs`, `get-current-safari-url`, `open-safari-url`, `close-safari-tab` |
| People & account mapping | 7 | `set-person-alias`, `discover-person-accounts`, `list-service-accounts`, `list-person-accounts`, `set-person-account`, `remove-person-account`, `search-person-data` |
| Call history | 1 | `search-calls` |
| SKS PersonalHealth | 3 | `get-health-status`, `read-health-samples`, `read-health-ecg` |
| Diagnostics | 1 | `diagnostics` |

</details>

## How it works

```mermaid
flowchart TB
    U["Authorised ChatGPT client"] <-->|"Private MCP connection A"| L["Apple Bridge LOCAL<br/>53 tools · macOS"]
    U <-->|"Private MCP connection B"| C["Apple Bridge Cloud<br/>11 read-only tools · Linux"]
    L --> A["Local Apple services<br/>Messages · Notes · Reminders · Safari · SKS"]
    C --> B["Selected iCloud Mail, Calendar, Contacts<br/>and private IMAP mailboxes"]
    U -.->|"When separately connected"| G["Native Google Calendar / Gmail integrations"]
```

**Local-first, with clear boundaries.** The primary bridge uses the authorised macOS environment and permissions. The independent Cloud service uses its own Linux runtime and read-only account allowlist. Each MCP server uses a separate private connection and transport. Switching between the two requires selecting the appropriate available integration; Cloud does **not** automatically take over an interrupted LOCAL request.

Local-only operations depend on the Mac and are not exposed by the Cloud service. Native Google integrations are separate from both MCP endpoints.

## Designed with control in mind

- **Explicit account ownership:** profiles and aliases are confirmed rather than inferred from similar-looking names.
- **Permission-aware access:** local operations rely on the relevant macOS authorisation mechanisms.
- **Safer mutations:** operations that send messages or change data are treated differently from read-only lookups.
- **Fail-closed behaviour:** unknown account mappings and ambiguous targets should not be silently guessed.
- **Tested change control:** the private development repository uses regression and MCP interface smoke tests.
- **Data minimisation:** this public showcase contains no production configuration, personal records, access tokens or service credentials.
- **Cloud separation:** the independent Cloud endpoint uses a fixed account allowlist, read-only operations, separate credentials and an isolated runtime; it does not expose LOCAL-only features.

> [!IMPORTANT]
> **Account mappings are routing aids, not user authentication.** A connected AI client can receive information returned by its authorised MCP tools. Security therefore depends on both local permissions and the access policy of the client and connection.

## Verified operational status

**Apple Bridge LOCAL:** independent post-restart acceptance was completed on **10 November 2026 (UTC)**. The basic diagnostics and connected-client checks were also repeated successfully on 11 November before the Mac was intentionally switched off for a continuity test.

| Check | Recorded result |
|:--|:--|
| Registered tools through ChatGPT | **53/53 available** |
| Read-only basic diagnostics | **9 OK, 0 warnings, 0 errors, 0 unknown** |
| Server connection | ChatGPT Secure MCP Tunnel responded successfully |
| Local SKS integration | Health endpoint and projection checks passed after restart |
| Messages bridge | Automatically became ready after login; the first attempt timed out and a later scheduled check completed successfully |

**Scope of LOCAL verification:** `about` and `diagnostics(level="basic")` were invoked through the real connected client. This does not establish end-to-end correctness of every tool, that a Tapback reaction was delivered, or ongoing receipt of new health samples.

**Apple Bridge Cloud:** a separate live acceptance on **11 November 2026** confirmed its own ChatGPT MCP connection, the **11-tool read-only interface**, the scoped **5 Mail / 2 Calendar / 1 Contacts** account configuration, working provider metadata reads and rejection of a removed Google Cloud account identifier. The local Mac was unavailable during the continuity checks. This does not imply an automatic failover mechanism or guarantee uninterrupted access to third-party providers.

## Project snapshot

| | |
|:--|:--|
| **Project** | Apple Bridge v2 |
| **Organisation** | MK Universal Solutions Ltd |
| **Deployment** | Two private, independent endpoints: Apple Bridge LOCAL (macOS) and Apple Bridge Cloud (Linux) |
| **Interface** | Model Context Protocol (MCP) |
| **Current tool catalogue** | LOCAL: 53 registered tools; Cloud: 11 read-only tools |
| **Primary approach** | Local-first, account-aware, permission-conscious |
| **Public availability** | README-only project showcase; no production source, credentials or configuration published |

The public page is a showcase of an independently maintained integration. It is **not a hosted service, a downloadable release or an invitation to connect to the production installation**.

## Foundations and acknowledgements

Apple Bridge v2 builds upon the work of **Carlos Lorenzo**, creator of the upstream [MrGo2/icloud-mcp](https://github.com/MrGo2/icloud-mcp) project. The upstream project is published under the MIT licence. MK Universal Solutions Ltd has developed and integrated additional functionality for its own deployment.

The upstream package and this private customised installation are **not interchangeable**. Installing `mcp-icloud` from npm does not install the private MKUS extensions. The tool names on this page are an overview, not a downloadable package.

This project is **not affiliated with, endorsed by or an official product of Apple or OpenAI**. Apple, iCloud, iMessage, macOS and other trademarks remain the property of their respective owners.

---

<div align="center">

### Built by MK Universal Solutions Ltd

**Practical integration. Clear boundaries. Real-world operation.**

<sub>Public showcase · Private production system · © MK Universal Solutions Ltd</sub>

</div>
