# Gulpy — Your NAS. Your Email Server. Just Ask.

**Turn your NAS into your own email server—managed through the AI chatbot you already use.**

Gulpy's vision is to make self-hosted email accessible to individuals, families, schools, communities, and companies. Instead of learning complex server dashboards, users describe what they want in ChatGPT, Claude, or another compatible AI chat interface. The longer-term architecture connects the AI assistant to the NAS through authorized MCP operations.

**Round 1 status:** The submitted **UGREEN Uliya Skill 0.1.1 is a mail-server planning and readiness Skill**, not a live mail-server installer. It helps you inventory independent email accounts, calculate storage allocations, review approved NAS documents, create a setup plan, and verify a saved report. It does **not** yet create accounts, configure DNS, start an email server, or test email delivery.

<br />

## Contents

- [The problem](#the-problem) — Why self-hosted email is difficult.
- [The Round 1 Skill](#the-round-1-skill) — What is available today.
- [Get the Skill](#get-the-skill) — Open the reviewed 0.1.1 package.
- [Example workflow](#example-workflow) — What the user asks, and what gets returned.
- [Validation and limitations](#validation-and-limitations) — What was checked and what was not.
- [Architecture and roadmap](#architecture-and-roadmap) — How Uliya and KORA Reach relate.
- [Attribution](#attribution) — New hackathon work versus prior technology.

<br />

## The problem

Your NAS has storage and computing power. It could also host your own email service. But even configuring a NAS can be hard without technical knowledge; operating a secure mail server adds domain settings, networking, certificates, storage planning, backups, and ongoing maintenance.

Hosted email often charges per account. Gulpy's goal is to remove per-user software fees for independent email accounts on user-owned infrastructure, without forcing users to switch to a new AI assistant.

<br />

## The Round 1 Skill

**Skill:** `gulpy-mail-setup` · **Version:** `0.1.1` · **Track:** Automate Your Workflow

The Uliya Skill currently:

1. Collects domains, independent mailbox requirements, per-account quotas, and a user-supplied storage budget.
2. Reads **only authorized** NAS files and documents through registered Uliya experts.
3. Produces a mailbox inventory, quota calculations, readiness checklist, and a list of next actions.
4. Requests approval before saving a Markdown report.
5. Reads the saved report back when supported; reports uncertainty rather than claiming an unverified save.

The Skill is intentionally limited to the official Uliya capabilities. It never substitutes arbitrary shell commands, Docker management, or an unconnected MCP runtime.

<br />

## Get the Skill

**[Download the reviewed Skill ZIP](Gulpy_Uliya_Skill_0.1.1.zip)**

The ZIP and the [`gulpy-mail-setup/`](gulpy-mail-setup/) directory contain exactly the six Markdown files of the submitted Skill:

- [`SKILL.md`](gulpy-mail-setup/SKILL.md) — Goal, accepted inputs, capability boundaries, and delegation rules.
- [`references/`](gulpy-mail-setup/references/) — Workflow, plan format, safety, capabilities, and disclosures.

**ZIP SHA-256:**

```text
d912241d1a97bcf17d9fbb39d9ca320e172a0521c633f54e256608dbb9f59031
```

The Uliya runtime must provide the registered experts and appropriate permissions. This repository is not an installable mail server.

<br />

## Example workflow

> “I want separate email inboxes for Anna and Ben at myteam.com. Help me plan the setup on my NAS.”

Gulpy asks for any missing mailbox and storage requirements, checks only the files the user authorizes, and returns:

- A per-account plan and storage total.
- Requirements that are complete, missing, or unverified.
- A report that can be saved to an approved NAS location.
- A readback outcome, without guessing if a save or verification failed.

**An account in the plan is not a created email account.** A saved plan is not evidence that mail delivery works.

<br />

## Validation and limitations

| Check | Recorded result |
| --- | --- |
| Official Uliya Skill Kit 0.7.7-en static checks | 0 errors, 0 warnings |
| gStack 1.98.0.0 package and integrity QA | Passed |
| Fresh offline response scenarios | 10 reviewed; tool observations were simulated |
| Validation/build tool regression checks | 15 passed |
| Actual UGREEN NAS execution | **Not yet tested** |
| Live SMTP/IMAP, account creation, or DNS changes | **Not implemented by this Skill** |

Future production deployment requires supported execution privileges, email services, DNS control, TLS, networking, backups, and abuse protection. The Skill makes no claim of unlimited measured NAS capacity.

<br />

## Architecture and roadmap

**Current Uliya Skill (developed for the hackathon):**

```text
User request
    ↓
Uliya Skill: gulpy-mail-setup
    ↓
Registered Uliya experts
    ├── file-agent / ug-filesystem     → authorized file reads
    ├── document-agent / ug-document   → approved document review
    └── knowledge-agent / ug-knowledge → approved plan save
    ↓
Readback and an explicit verification status
```

**Longer-term Gulpy product vision:**

```text
Existing AI chatbot (ChatGPT, Claude, etc.)
    ↓
Secure, authorized MCP connection
    ↓
KORA Reach execution layer
    ↓
NAS → email server setup, operations, and verification
    ↓
Beyond email: other user-owned services
```

KORA Reach is **existing, separately developed software** that allows AI chat interfaces to control authorized computers through MCP. A separate Linux email-management preview has been developed and tested locally, but **it is not included in this Skill package, and the Skill is not integrated with it**. In the separate preview, 109 local automated tests passed; real NAS and mail-delivery tests remain outstanding.

<br />

## Attribution

**Created by Albert Kim for the UGREEN AI NAS Hackathon 2026, Round 1.**

The Uliya Skill and its workflow were newly developed for this hackathon. KORA Reach predates the hackathon and is disclosed as prior foundation work, not as part of the submitted Uliya Skill. ChatGPT assisted drafting, coding, review, and packaging.

Upstream references: [UGREEN Uliya](https://ai.ugreen.com/), [Model Context Protocol](https://modelcontextprotocol.io/), [Docker Mailserver](https://github.com/docker-mailserver/docker-mailserver), and [gStack](https://github.com/garrytan/gstack). None of their source code or containers is bundled in the submitted ZIP.

The original Gulpy character artwork and frozen Linux preview remain in separate local projects and are not published in this repository.
