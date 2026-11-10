<div align="center">

# 🍎 Apple Bridge v2

### Your Apple world. One intelligent bridge.

**A private, local-first Model Context Protocol (MCP) integration for macOS, developed by MK Universal Solutions Ltd.**

<p>
  <img alt="Project status: operational private deployment" src="https://img.shields.io/badge/Status-Operational-18794e?style=for-the-badge" />
  <img alt="52 MCP tools" src="https://img.shields.io/badge/MCP%20Tools-52-3066be?style=for-the-badge" />
  <img alt="Platform: macOS" src="https://img.shields.io/badge/Platform-macOS-343a40?style=for-the-badge" />
</p>

**[Overview](#overview) · [Capabilities](#what-it-can-do) · [Architecture](#how-it-works) · [Security](#designed-with-control-in-mind) · [About](#about-this-project)**

</div>

---

> [!NOTE]
> **This is the public project showcase, not a source-code distribution.** The production implementation, infrastructure configuration and development history are maintained in a separate private repository. This repository intentionally contains no live credentials, account mappings, private deployment details or personal data.

## Overview

**Apple Bridge v2** connects an authorised AI assistant with supported Apple services available to a macOS user. It brings together communication, organisation, account-aware discovery and selected local information in a single MCP interface.

The project focuses on making Apple services **useful in real workflows**, not simply exposing a collection of commands. Its private deployment is operational and currently exposes **52 registered MCP tools**.

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
| 💬 **Messages** | Work with conversations, iMessage and SMS routing, and supported message reactions |
| 🌐 **Safari** | Inspect and manage supported browser tabs |
| 📞 **Call history** | Read-only access to call records available to the local macOS user |
| 🔗 **Account discovery** | Discover service accounts and maintain explicitly confirmed person-to-account mappings and aliases |
| ❤️ **SKS PersonalHealth** | Read-only access to selected local health-data projections through a separately managed integration |

The availability of individual operations depends on the active mode, configured services, macOS permissions and connected client. **Not every capability is available in cloud mode, and not all 52 tools have been tested live in every possible scenario.**

## How it works

```mermaid
flowchart TB
    U["Authorised AI client"] <-->|"Approved MCP connection"| B["Apple Bridge v2<br/>52 MCP tools"]
    B --> L["LOCAL mode<br/>macOS user session"]
    L --> A["Mail · Calendar · Contacts<br/>Reminders · Notes"]
    L --> M["Messages · Safari · Call history"]
    L --> H["Optional read-only<br/>SKS projection"]
    B -.-> C["Optional CLOUD mode<br/>supported Apple protocols"]
```

**Local-first, with clear boundaries.** In its primary configuration, the bridge uses the native macOS environment and permissions. The MCP server itself communicates over standard input/output; any remote connection is handled separately by an authorised, securely configured transport.

Optional cloud integrations use supported protocols for a narrower set of services. Local-only operations depend on the host Mac and cannot be assumed to work in the cloud.

## Designed with control in mind

- **Explicit account ownership:** profiles and aliases are confirmed rather than inferred from similar-looking names.
- **Permission-aware access:** local operations rely on the relevant macOS authorisation mechanisms.
- **Safer mutations:** operations that send messages or change data are treated differently from read-only lookups.
- **Fail-closed behaviour:** unknown account mappings and ambiguous targets should not be silently guessed.
- **Tested change control:** the private development repository uses regression and MCP interface smoke tests.
- **Data minimisation:** this public showcase contains no production configuration, personal records, access tokens or service credentials.

> [!IMPORTANT]
> **Account mappings are routing aids, not user authentication.** A connected AI client can receive information returned by its authorised MCP tools. Security therefore depends on both local permissions and the access policy of the client and connection.

## Project snapshot

| | |
|:--|:--|
| **Project** | Apple Bridge v2 |
| **Organisation** | MK Universal Solutions Ltd |
| **Deployment** | Private, operational macOS installation |
| **Interface** | Model Context Protocol (MCP) |
| **Current tool catalogue** | 52 registered tools |
| **Primary approach** | Local-first, account-aware, permission-conscious |
| **Public availability** | Project information only; production source and configuration are not published here |

The public page is a showcase of an independently maintained integration. It is **not a hosted service, a downloadable release or an invitation to connect to the production installation**.

## Foundations and acknowledgements

Apple Bridge v2 builds upon the work of **Carlos Lorenzo**, creator of the upstream [MrGo2/icloud-mcp](https://github.com/MrGo2/icloud-mcp) project. The upstream project is published under the MIT licence. MK Universal Solutions Ltd has developed and integrated additional functionality for its own deployment.

The upstream package and this private customised installation are **not interchangeable**. Installing `mcp-icloud` from npm does not install the private MKUS extensions.

This project is **not affiliated with, endorsed by or an official product of Apple or OpenAI**. Apple, iCloud, iMessage, macOS and other trademarks remain the property of their respective owners.

---

<div align="center">

### Built by MK Universal Solutions Ltd

**Practical integration. Clear boundaries. Real-world operation.**

<sub>Public showcase · Private production system · © MK Universal Solutions Ltd</sub>

</div>
