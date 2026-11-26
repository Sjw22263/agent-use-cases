# Set up an independent decision reviewer

Set up a reviewer that returns a private recommendation on one stated choice. It needs evidence and a return route, not control of the project.

1. **Collect the operator's choices.** Identify the proposal author, decision owner and private recipient. Ask what decision is still open, which conditions are requirements rather than preferences, and which records the reviewer may inspect. In a chat-only setup, the operator can paste the packet and pass the reply to the owner.
2. **Prepare a separate context.** Use a fresh session without the drafting conversation. Label the inputs below; put the recommendation last if practical. If the reviewer helped write the proposal, choose another reviewer rather than describing its assessment as independent.
3. **Enforce access in the platform.** Start with the packet and a reply in the private session. If source inspection matters, optionally attach a reader limited to the named documents. Permit bounded public lookup only for a specified question that could change the verdict; keep private packet details out of queries. Do not attach project-write, shell, approval, messaging or publishing capabilities. If read-only scope cannot be enforced, leave the connection off and use pasted extracts. Confirm the actual tool list and permissions; prompt text is not an access control.
4. **Install the packet and reply formats.** Give the author the packet form and the reviewer the runtime block below. Keep evidence and recommendation separately labelled even when both come from the same person.
5. **Dry-run before activation.** Use a fictional packet: a museum proposes replacing a large-print guide with a kiosk; its requirement is unassisted use; its only note describes a demonstration led by a guide. A satisfactory reply retains the finding about assisted use, holds the replacement and specifies an unassisted attempt rather than claiming it failed. Check the reply against the note and verify that the only output is private advice. If the reply invents a result or treats agreement as sign-off, correct the setup before use.

**Packet for the author**

```text
Decision and owner:
Proposal/version; alternative (including keeping things as they are):
Criterion for choosing; non-negotiable conditions:
Evidence by ID: source or extract, what was observed, under what conditions:
Author's recommendation and reason:
```

**Copyable runtime instructions for the reviewer**

```text
Advise on the choice in the packet. Read the criterion and labelled evidence
before the author's conclusion where possible. State the assumption that
would reverse the recommendation if wrong. Look for a case consistent with
the record where it does not hold. If no material objection survives that
check, support the proposal and explain why.

Separate what a record shows from what someone reports and what you infer.
If the decisive fact is missing, retain what is supported and name the
smallest check and result that would change your advice. If the facts are
adequate but the options favour different priorities, give the choice to
the owner; do not prescribe another test to settle a preference.

Return a private note in this format:
Verdict on [version versus alternative]: [support, revise, hold, or owner choice].
Reason: [criterion, decisive assumption and evidence ID; what to keep].
Confidence and limits: [confidence in what, sources inspected, material not checked].
Next decision: [who chooses; what new observation or priority changes the advice].

Before returning, match each factual reason to a source you actually read.
If a source is unavailable, say which extract is needed. If the question or
criterion is missing, say what can be judged now and ask one focused question.
Never imply that you ran a check. Return advice; do not change the work,
approve it, contact third parties or publish.
```
