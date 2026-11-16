# Capability evidence and limits

Use the official Uliya Skill Kit 0.7.7-en, catalog version 2.2.0 dated 2026-11-05, as the authoring basis. The catalog has nine CLI groups and 84 public Actions. Only the three groups below are needed by Gulpy.

The catalog is source-aligned, not a verified target-device inventory. Permissions, prerequisites, error codes, and stability for the selected Actions are marked unknown. Do not invent them. Runtime authorization and returned facts remain authoritative.

## Supported work

| Intended action | Catalog evidence | Expert | Effect and approval | Acceptance |
| --- | --- | --- | --- | --- |
| Verify a user-supplied path | `ug-filesystem` / `stat` | `file-agent` | Read; catalog approval `none` | Exact returned path, type, relevant attributes, and actual access limitations. |
| Discover selected files under a bounded directory | `ug-filesystem` / `ls`, `find` | `file-agent` | Read; `none` | Actual paths, applied scope, completeness or truncation, and explicit no matches when applicable. |
| Read sanitized text or a saved Markdown report | `ug-filesystem` / `cat` | `file-agent` | Read; `none` | Source path, complete content or byte-range coverage, and any truncation. Saved-report verification across multiple ranges also requires credible evidence of one consistent file version. |
| Identify a document and its scope | `ug-document` / `metadata` | `document-agent` | Read; `none` | Actual source identity, page or content scope when available, and limitations. |
| Review selected documents | `ug-document` / `qa` | `document-agent` | Read; `none` | Source-grounded facts, citations, content coverage, and failures. |
| Save the approved report | `ug-knowledge` / `save-text` | `knowledge-agent` | State change; `workflow` approval | Actual output path and explicit write/read-back confirmation, followed by the requested independent readback. |

These are generation-time mappings, not commands for the parent to execute. Delegate the business task; let the responsible expert select supported Action parameters.

## Operation details that affect correctness

`stat` describes a file or directory. It does not report the NAS model, memory, storage-pool capacity, free disk space, container runtime, service status, or usable mailbox capacity. Directory totals, if provided by a user, also do not establish free disk space.

`ls` and `find` can return incomplete results. Bound discovery to the user-approved root. A missing match does not authorize a broader search. A directory must not implicitly authorize reading every file beneath it.

`cat` can read a byte range. A successful partial read is still partial. Have the expert complete coverage of the same authorized file before claiming a complete comparison. For saved-report verification across multiple ranges, also require credible evidence that all ranges belong to one consistent file version. The catalog does not promise snapshot reads or a shared version identifier. Changed size or modification time can reveal inconsistency; unchanged values alone do not prove consistency. If complete coverage or credible consistency evidence cannot be established, disclose the gap and retain `SAVE_REPORTED`. Do not invent a version field, digest, locking Action, or additional write to obtain that evidence.

`qa` uses actual source documents. Its query carries the original user question unchanged. Coverage and source citations matter; document metadata alone is not evidence that its text was read. Use file reading for known Markdown rather than routing it through an unnecessary search index.

`save-text` accepts literal content or a genuine server-side content reference, not both. Gulpy uses the exact report text. A destination must be a real user-supplied directory or an appropriate text-file path, not a guessed location or the source PDF. This Skill prefers a verified output directory and a new-file policy. The expert may sanitize the filename hint and add a timestamp; use only the returned final path.

A verified save is not knowledge-index readiness. A direct read of the returned Markdown path does not require indexing. Catalog output examples are synthetic shape illustrations; never reuse their paths or assume their keys are fixed parent-facing fields.

## External work this version cannot execute

| Desired mail operation | Capability evidence | Skill behavior |
| --- | --- | --- |
| Install Docker, containers, or a mail server | No matching public Action in the authoring catalog | Plan the deployment requirement; `NOT_EXECUTED`. |
| Create, delete, or change independent mailbox accounts or quotas | No mail-administration Action | Produce the requested inventory and quota policy; `NOT_EXECUTED`. |
| Inspect or change live MX, SPF, DKIM, DMARC, or reverse DNS | No DNS lookup or administration Action | Review sanitized evidence if supplied; live state remains unverified. |
| Test ports, routing, IP reputation, or SMTP/IMAP delivery | No network or mail-probe Action | Record user reports and dated evidence; do not manufacture a test. |
| Provision TLS or configure firewall, relay, or backups | No corresponding administration Action | List the responsible external task and missing authority. |
| Execute KORA Reach or call an external MCP connector | Not part of the public delegation contract | Do not invoke it from this Skill. |
| Select, install, or reconfigure AI models | No model-administration Action | Use the already-authorized host AI environment only. |

Existing file-write capabilities do not make it appropriate to edit production mail configuration. Gulpy writes planning reports only. A future catalog or product UI mentioning mail does not automatically expand this version's scope.

## Primary authoring sources

- [UGREEN Starter Kit](https://ai.ugreen.com/pages/hackathon-starter-kit).
- [Official Uliya Skill Kit 0.7.7-en archive](https://cdn.shopify.com/s/files/1/0630/9416/1602/files/uliya-skill-kit-0.7.7-en.zip?v=1794462613), especially `data/capability-catalog.json`, `docs/skill-development-standard.md`, and the orchestration/completion references.
- [Hackathon rules](https://ugreenhackathon.devpost.com/rules).

These links document authoring evidence. They are not runtime download or execution instructions.
