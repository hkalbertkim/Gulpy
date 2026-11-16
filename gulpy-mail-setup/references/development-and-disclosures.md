# Development and disclosures

## Authorship and deliverable

Prepared for Albert Kim's individual Gulpy entry to the UGREEN AI NAS Hackathon. The Uliya-native workflow was newly authored on November 15, 2026, using the official creation kit. This package contains original Gulpy orchestration instructions and supporting Markdown references only.

The project title and long-term ambition concern running a mail server on a NAS. This version's implemented Skill scope is mail-readiness planning, authorized source review, report saving, and evidence-aware readback. It does not claim native mail-service administration.

## Prior foundation is separate

KORA Reach, created by Albert Kim, is an existing MCP-based execution layer for AI-to-computer interaction. The frozen Gulpy Linux preview 0.1.0-preview.1 contains a separate mail-management direction. Neither its runtime nor its source is included in this Skill ZIP, and this Skill does not call it.

The supplied freeze/checkpoint record reports 109 Debian automated tests and additional packaging/configuration checks for that separate preview. Those results are historical evidence for the Linux preview, not tests of this Uliya Skill or a live UGREEN NAS. Real mail-container startup, SMTP/IMAP delivery, hosted-chat-to-NAS operation, and UGREEN deployment were unverified in that record.

The frozen proposal and Linux source are preserved separately. Any differences between their planned capabilities and the current authoring catalog are reported in the development report rather than silently editing the frozen materials.

## Third-party technology

- UGREEN Uliya Skill Kit 0.7.7-en: official authoring specification, catalog, and local static checker from the [UGREEN Starter Kit](https://ai.ugreen.com/pages/hackathon-starter-kit). The kit is a development resource; its code and archive are not redistributed in this Skill. Its use is subject to the official terms linked by UGREEN; no additional license grant is asserted here.
- Docker Mailserver: [upstream project](https://github.com/docker-mailserver/docker-mailserver), referenced by the separate Linux preview. Its repository uses MIT licensing; bundled components such as Postfix and Dovecot have their own licenses. No source, container image, or executable from that stack is included here.
- MCP: the protocol used by prior KORA Reach. No MCP client, external endpoint, or KORA runtime is invoked by this Skill.
- ChatGPT, Claude, and compatible local AI environments: development or product-interface context, subject to their applicable terms. The Skill uses its already-authorized host model and does not select, install, or reconfigure one.

## Data flows

Runtime work is limited to the platform's registered file, document, and knowledge experts. Inputs can contain authorized domain names, planned mailbox addresses, quotas, and sanitized source excerpts. The report is saved only to a user-selected NAS directory. This package defines no external upload, public sharing, message sending, or background telemetry.

The host platform determines its model data flow. Do not claim that all inference is local merely because source files or saved reports are on the NAS. Review only data permitted for that host environment.

## AI assistance

AI assistance was used for workflow design, drafting, technical analysis, local checking, scenario review, and packaging. Earlier project imagery used AI assistance, but no imagery or generated runtime evidence is included in this Markdown Skill package.

## Ownership and validation disclosure

The separate frozen Linux mail source includes a Krako Labs copyright notice. Do not change that notice or infer individual ownership from a founder role. This package does not redistribute that source. The entrant must ensure any submission ownership declaration accurately reflects applicable rights; this document does not resolve ownership or assignment.

Local official static checks and clearly labeled offline scenario exercises can validate package structure and instruction behavior. They do not prove device installation, actual expert execution, saved NAS files, live mail delivery, or acceptance by the organizer. Target-device validation remains a separate step if selected for the final round.
