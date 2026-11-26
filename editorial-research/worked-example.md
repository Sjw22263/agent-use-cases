# Worked example: the audit that caught the wrong three

*Explicitly fictional. The company, standard, documents, figures and back-test below are invented for illustration. Nothing here was run against a real system, and no result in this file is a live test.*

## The brief as it arrived

> From the author, by email:
>
> "The compliance checker worked. I ran it over 14 subcontractor method statements from last year's
> audit and it found 11 of the 14 problems our auditor found. 79 per cent, first try, no tuning.
> I want a case study up this week: *AI can audit compliance documents*. Can you draft it?"

Supporting material supplied: a back-test spreadsheet with the 14 documents, the auditor's original findings as ground truth, the agent's output per document, and a run log. The author is a civil engineering documentation lead; the fictional standard is an industry safety code with numbered clauses.

## What the agent did with it

Read the back-test rather than the summary. The 11 hits are real and reproducible: the records are dated, the ground truth predates the run, and the agent's outputs are stored per document. That part is solid, and the author is entitled to it.

Three things in the same file cut against the headline.

The three misses are not a random 21 per cent. Two of them are the findings the original auditor marked as critical: an exclusion-zone omission and a lifting plan that referenced a superseded clause. The agent caught formatting and cross-reference defects and missed the two that would end a career. A hit rate treats all defects as equal; auditing does not.

The agent cited two clause numbers that do not exist in the standard. Not misread clauses: absent ones, in otherwise fluent findings. In the back-test this was harmless because the author knew the standard. In use it is the whole risk, because the failure mode is confident invention, not silence.

The back-test used clean text extracted from the author's own archive. Subcontractors submit scanned PDFs, and nothing in the record tests that path.

None of this makes the work unpublishable. It makes the headline unpublishable.

## The proposition handed back

```text
Title:        Where a clause-checking agent earns its place, and where it does not
Claim:        A clause-matching agent is a usable triage layer over compliance documents only when
              every citation it produces is validated against the standard's index; measured as an
              auditor it fails, because it misses the consequential findings and invents clauses
              fluently.
Evidence:     14-document back-test against a prior human audit, ground truth recorded before the
              run, per-document outputs and run log retained. 11 of 14 known findings flagged.
Contrary:     The 3 misses include both findings the original auditor marked critical. Two cited
              clause numbers do not exist in the standard. Inputs were clean extracted text; real
              submissions are scanned PDFs, untested. No baseline for human review time, so "faster"
              is unquantified.
Audience:     Compliance, safety and quality leads being sold document-review automation; the
              primary reader has to decide whether to put this between a subcontractor and a site.
Form:         Technical note with the back-test table. Not a case study: no deployment, no baseline,
              no outcome. Companion post carrying the citation-validation point and linking the note.
Verdict:      Narrow. Drop "AI can audit compliance documents". Publish the triage-layer claim with
              the miss profile and the invented citations shown, not buried.
Unverified:   Behaviour on scanned submissions; whether citation validation catches all invented
              clauses; human review time baseline; whether the ground truth was itself complete.
Disclosure:   Subcontractor identities and the project must come out. Clause text is likely
              copyright; cite numbers, quote nothing. A piece reporting that your own tool missed
              two critical findings is a commercial judgement, not an editorial one.
Decision:     Publish the narrowed technical note now, or hold for a week and run the scanned-input
              and citation-validation tests first so the note can state the real limit?
```

## The claim, before and after

**Before:** "Our AI compliance checker caught 79 per cent of defects in subcontractor safety documentation. AI can audit compliance documents."

**After:** "In a 14-document back-test against a prior human audit, a clause-matching agent flagged 11 known findings and missed 3, including both the auditor had marked critical. It also cited two clauses that do not exist in the standard. As a triage layer with every citation validated against the standard's index, it is worth running. As an auditor, it would have passed the documents that mattered."

The second version is longer, less quotable, and the only one the records support. It is also the more useful piece, because the reader's real question is not whether this works but where it breaks, and the answer here is specific: it breaks confidently, on the findings that count, in a direction that looks like competence.

## The judgement call

The tempting move was to publish the 79 per cent with a caveat paragraph near the end. That is the version that gets shared and the version that misleads, because a hit rate implies the misses are interchangeable with the hits. Reweighting the claim around the miss profile costs the headline and keeps the piece defensible in front of a safety engineer, which is the only audience that matters for this subject.

The agent did not invent a counterargument to appear rigorous. All three objections came out of the author's own file. If the misses had been minor and the citations clean, the honest editorial answer would have been "pursue as written", and that is what it would have said.

## Verification, and what is left for the human

How the published version would be verified before it ships: re-run the back-test with citation validation enabled and report both numbers; run the same 14 documents as scanned PDFs and report that result or state plainly that it was not tested; have a second reviewer confirm the ground-truth findings were complete; check every clause number quoted in the article against the current standard, because an article about invented citations containing an invented citation is a particular kind of failure.

What stays with the author: whether to publish a result that includes their own tool missing both critical findings; clearing any quoted standard text; and whether to hold the piece for a week to get the scanned-input answer. The agent's recommendation is to hold for the week, because the untested input path is exactly what the primary reader will ask about first. The author decides. The ledger records the original "AI can audit compliance documents" framing as rejected, with the reason, so it does not come back in six months wearing a different title.
