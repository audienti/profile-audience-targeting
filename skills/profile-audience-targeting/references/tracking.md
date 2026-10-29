# External tracking state

The host owns persistence and scheduling; these skills do not create a background
job. Read existing state before retries. Keep each case's full brief/version hash.

Keep collection cursors per case, skill, seed and participant type. A successful
page, failed next request and blocked other type remain separate. Never advance a
failed cursor or mark blocked access empty. Resume stable cursors; otherwise
rescan a bounded overlap and disclose coverage gaps. Revisit recent post audiences
on later passes even without new posts. A publication watermark cannot cover new
comments on old posts. Missing actors in a partial page do not prove removal.

Both skills read the same case-level identity ledger, while keeping collection
state separate. The ledger stores verified aliases, prior candidate status and all
source edges. A per-skill set records people previously qualified through that
method. Pin these sets at run start; do not let task execution order determine
attribution. In a joint comparison both methods may find the same campaign-new
person: report one union person plus explicit overlap, not a winner by arrival time.

Use these counts consistently:
- First observed: person evidence first encountered, regardless of qualification.
- Newly qualified: a person transitions to candidate after all required proof.
- Method-new: candidate absent from the pinned method-qualified set.
- Campaign-new: candidate absent from the pinned case-qualified union set.
- Fresh campaign-new: campaign-new AND countsAsFresh=true.
Unresolved URL/opaque-ID aliases make novelty unknown and contribute zero to
new-person metrics until resolved. Changed brief criteria require reassessment.

Keep interaction IDs when available. For reaction snapshots without stable IDs,
use exact target + actor identity + kind to deduplicate observation state. This
cannot prove every removal/re-add or type-change event. For comments without IDs,
retain ambiguous observations; text similarity alone cannot prove a new event.
Store direction and exact target author: outgoing actor is the seed, candidate
is target author; incoming actor is candidate. Never infer reciprocal edges.

Retain original source/crawl and retrieval times. Cached data is not a fresh poll.
Journal paid requests before execution, preserve responses and authoritative cost
receipts, and do not double-count nested provider charges. Timeout remote charges
remain unknown. Keep state/evidence only in the authorized destination.

## Run lineage and commit

A person qualifies if any one finding is a candidate. A person is fresh if any
candidate finding has countsAsFresh=true. Person totals are distinct identities,
not sums of edges or attempts. Topic-qualified people belong to the campaign union
only for the same case/brief and verified identity; a topic observation bank is
not a qualified ledger. An opaque-ID ledger without an alias bridge cannot prove
that a vanity-URL person is absent: novelty remains unknown.

Pin method and campaign ledgers once per runId. Resumes keep those pins and reuse
the same runId with a new attemptId and resumeOf; return cumulative findings,
unique-person totals and a cumulative ledgerDelta. Never sum resumed totals.
For a joint audience/engagement comparison, use the same initial campaign pin,
union the deltas, and disclose overlap. The host merges verified aliases and
qualified identities idempotently using runId + briefHash + identity, preserving
method attribution and distinct evidence. Apply each delta once, recording commit
status and resulting ledger version. A retry may safely reapply the same delta.
The next new run pins the committed ledger. If a commit failed or the previous
run's delta is unavailable, disclose the gap and leave novelty unknown; do not
silently repin an empty ledger. Do not write shared ledgers outside authorization.

Declare each pinned ledger's kind (method-qualified, campaign-qualified-union or
observation-bank). Missing kind makes qualification novelty unknown. Split fresh
unique-person totals into exact-event and interval-only: if a person has any
qualifying exact-event edge, place them in exact-event; otherwise, with a valid
interval edge, interval-only. These disjoint subsets sum to total fresh people.
