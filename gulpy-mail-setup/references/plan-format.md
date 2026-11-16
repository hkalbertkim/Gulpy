# Plan format

Produce a useful report for the requested scope. Do not fill unknown fields with fabricated values. Include only sections that apply, while always stating the execution boundary.

## 1. Requested outcome and scope

State the requested domain count, independent mailbox count, use of aliases or forwarding, quota policy, evidence scope, and whether the user requested saving. Explain that this report plans and reviews setup; it does not create a working mail service.

## 2. Domain and account inventory

Use a per-domain table with these columns: domain, independent mailbox count, naming basis, quota per mailbox and unit, aggregate quota, DNS authority source/status, and unresolved items. Show a uniform quota when it applies to every requested mailbox in that domain; otherwise show `mixed` with the actual quota groups and their mailbox counts. For a zero-mailbox row, show zero requested allocation and keep any future quota policy separate.

When exact addresses are supplied or a naming rule is explicitly approved, include one row per independent mailbox in an account table. Each row contains the domain, address, account type, quota/unit, source, and status `PLANNED`. Do not add credentials. Add aliases in a separate table; they do not increase the independent mailbox count.

Count unique intended mailbox addresses after resolving duplicate entries. Preserve the local part. Domain case differences can identify the same domain, but local-part case differences require clarification rather than automatic merging. Internationalized domain/local-part support is an unresolved runtime requirement unless independently established. Do not silently discard invalid or ambiguous entries.

If only counts are supplied, report the requested count and mark names unresolved. Do not invent domain names or addresses. If the user explicitly requests a generated naming rule, show that rule and generated inventory as planned input, not created accounts.

Counts must be finite nonnegative integers. A zero count means no requested independent mailboxes for that row. Negative, fractional, nonnumeric, or conflicting counts require clarification. Repeated domain rows and disagreement between a supplied count and an explicit address list must be resolved before claiming an exact total; do not silently double-count or invent the missing accounts.

## 3. Quota and storage calculation

Compute each domain allocation by summing the quota of every requested independent mailbox. Use mailbox count multiplied by quota only for a group whose mailboxes share that quota and unit. For mixed quotas, show the per-account sum or the sum of the actual uniform-quota groups; do not replace supplied quotas with a common policy. Sum across domains after any explicit unit conversion. Show arithmetic and units. One GiB is 1,073,741,824 bytes; one GB is 1,000,000,000 bytes. Ask about an ambiguous unit or present both interpretations; do not silently convert the label.

Require a finite positive quota for every requested mailbox before computing a finite complete allocation. Fractional positive quotas such as 0.5GiB are valid. Clarify zero quotas because the intended meaning may be an unusable mailbox or an unlimited policy. Negative, nonnumeric, and non-finite amounts are invalid. An explicit unlimited policy for at least one requested mailbox remains an unbounded allocation, not zero or a guessed finite quota. A missing quota for a requested mailbox remains unknown. In those cases do not compute a finite complete total or claim the budget is sufficient. A zero-mailbox row contributes zero requested allocation regardless of its future quota policy; record that future policy separately without blocking the total for actual requested mailboxes. A budget must be finite and nonnegative; a zero budget is valid but supplies no mailbox allocation.

For illustration only, 10 domains multiplied by 15 mailboxes is 150 mailboxes. At a user-specified quota of 5GiB each, aggregate configured mailbox quota would be 750GiB. That is an allocation ceiling, not measured usage, available NAS storage, a reserved guarantee, or verified hardware capacity.

Compare against a user-supplied budget only when its meaning and units are clear. List any shortfall. Do not default to a guessed overhead percentage. Keep operating-system use, other services, snapshots, backup retention, redundancy, and growth headroom separate until assumptions are provided. Mail software license cost is not the total operating cost.

## 4. Readiness and evidence

Use a table with item, fact, provenance/date, status, and next action. Suggested items are domain ownership/DNS authority, hosting runtime, mailbox inventory, quota budget, TLS, network/routing and port policy, relay requirement, backup plan, and incoming/outgoing acceptance tests.

Use clear evidence labels in prose or table cells:

- `USER_REPORTED`: supplied by the user; not a live check.
- `DOCUMENT_REVIEWED`: found in a cited source; retain its date and coverage.
- `FILE_READ_VERIFIED`: supported by an actual file-expert read with the scope stated.
- `UNKNOWN`: no sufficient evidence is available.
- `BLOCKED`: a known prerequisite is missing; state the source of that knowledge.

These are report labels, not fields guaranteed by a platform API. A file read may verify what a note says without verifying that the note's claim is currently true.

## 5. External work and user next actions

List each requested unsupported operation separately: runtime/mail-service installation, account creation, quota enforcement, live DNS inspection and changes, TLS, network/relay changes, backup configuration, and live mail tests. Mark each `NOT_EXECUTED` by this Skill.

Give a clear owner or next step without writing executable commands or assuming an external integration. For example: obtain DNS authority from the domain administrator, ask the network provider to confirm port policy, or have the authorized runtime operator validate deployment and delivery.

If the user reports that SMTP is blocked, record the reported block and explain that delivery requires an authorized external remedy. Do not claim a port probe occurred. Missing DNS permission must not trigger a request for DNS credentials in chat.

For a domain-authentication checklist, name MX, SPF, DKIM, DMARC, and reverse DNS as external review topics. Do not invent record values, IP addresses, selectors, keys, or a production enforcement policy.

## 6. What happened in this run

List source files actually read, scope limitations, facts still unknown, and mail operations not executed. For an in-chat result, also report planning and artifact labels.

For a report being saved, describe its content and known evidence without claiming the not-yet-observed save/readback succeeded. After saving and verification, the final chat response supplies the actual output path and artifact label. Do not rewrite the report solely to add a circular self-verification claim.

## User-facing completion format

Lead with the useful result: the plan scope and whether it was saved and verified. State the independent mailbox total and aggregate quota when known. Show the actual output path if one was returned. Then explain the main blockers and one concrete next step.

Finish with the boundary: no mail server was installed, no mail accounts were created, and no live delivery was tested by this Skill. Do not imply that an unsaved plan, a saved report, and a running mail service are interchangeable results.
