# Result contract (local draft v2)

Return JSON with `schemaVersion:2`, `skill` (invoked skill name), `briefRef`,
`briefHash`, `window`, `toolMode`, `status: completed|partial|blocked`, `seeds`,
`people`, `companies`, `findings`, `excludedEvidence`, `sourcesChecked`, `gaps`,
`progress`, `run`, `ledgerDelta` and `nextAction`. Completed means the bounded pass finished, not that
coverage is exhaustive or contacts may be messaged.

Entities have local references and observed identities (URL/provider ID), with
field-level evidence references and observation times. Aliases require evidence;
local references are not CRM IDs. Unknown fields are omitted, not invented.

Seeds record acquisition `manual|researched`, category (preserve the user's label),
`relationshipTo`, selection reason and evidence. Separate `identityStatus:
verified|unresolved|conflicted` from `selectionStatus: active|proposed|rejected`.
Each relationship claim has `relationshipStatus: supported|unsupported|contradicted`,
its evidence and claimant. A manual seed with verified identity stays active even
when its supplied relationship is contradicted; explicitly disclose that mismatch
and do not relabel it as the user's customer. Never treat supplied as verified.
A researched seed stays proposed until the selection relationship is supported;
researched competitor personnel require verified current employment. Contradicted
employment rejects that researched selection, without asserting anything about
buyer fit. Identity-unresolved seeds cannot produce attributed findings.

Each finding has:

- `id`, `seedRef`, `candidateRef` (person or null), `companyRef` (or null).
- `edge: {actorRef, kind: comment|reaction, interactionId, targetRef}`. Interaction
  ID can be null; never invent IDs or comment permalinks. Target records
  `kind: post|comment`, observed ID/URL, `authorRef`, `enclosingPostRef`, and
  `parentRef` when needed. Preserve repost wrapper/original targets distinctly.
- `direction: incoming|outgoing`. Audience: candidate=edge.actorRef and target
  belongs to the selected seed's authored post. Engagement: seed=edge.actorRef,
  candidate=target.authorRef. Organization targets never become invented people.
- Evidence for the exact edge and identity links. Comments may have short quotes;
  reactions have no quote. A page containing names is not an edge.
- `companyFit` and `personFit`: one entry per required criterion, with
  `criterion`, `status: met|not_met|unknown`, `reason`, `evidenceRefs`.
- Separate `relevance` and `buyerProblem` judgments with reasons/evidence.
  Reaction-only buyerProblem is unknown. Neither implies intent or consent.
- `freshness`: requested interval, publication/event/observation times or bounded
  intervals, `status: in_window|outside_window|unknown`, and
  `basis: exact|interval|unresolved`. Unknown event time stays null. A lower bound
  uses the exact target's publication: a comment reaction uses comment time,
  not just enclosing-post time. Preserve the source snapshot time separately.
- `disposition: candidate|needs_evidence|not_fit|outside_window`. A verified hard
  ICP/Role failure is not_fit. Otherwise unresolved identity/edge/required fit
  or freshness is needs_evidence; proven out-of-window is outside_window;
  candidate requires all required criteria, edge and time rules to pass.
  No requested time limit is an explicit unbounded interval; never silently remove
  a time constraint to promote a historical person.
- `countsAsFresh`: true only for candidate whose exact event time OR entire
  valid event interval lies inside the bounded requested window. Interval-basis
  freshness counts even when event time is null; unresolved dates never count. `fitStatus: met|not_met|unknown` stays separate, so a historic
  fit does not look like a current prospect. Report historical fit separately.
- `novelty: {methodSeenBefore, campaignSeenBefore}` values true/false/unknown,
  pinned seen-set reference and identity-match evidence. Unknown contributes zero
  to new-person counts. Keep distinct edges; deduplicate people by exact identity.
- `toolMode: native|api|mixed|supplied_replay` and per-fact acquisition mode. One
  API-supported required fact makes the qualification non-native. Cached sources
  retain original observation/crawl times and separate retrieval time.

`excludedEvidence` retains evidence refs and a reason: `wrong_author`,
`wrong_target`, `sidebar`, `mention_only`, `organization_target`,
`identity_mismatch`, `unresolved_target`, `self_engagement`, `direction_mismatch`,
`unverified_seed`, `stale_employment`, `date_conflict`,
`repost_original_target`, `audience_contamination`. Do not call an otherwise suitable person not_fit because the
edge failed. Unresolved evidence may also have a null-candidate finding; never
turn multiple unverified names into multiple candidates.

`sourcesChecked` retains target, acquisition mode, inspection/retrieval time,
source/crawl time when available, and `inspected|blocked|failed|not_reached`.
`progress` stores actual per-source/type cursors and `exhausted|capped|blocked|
failed|not_reached`, requests, cache use and known/unknown costs. Reference private
raw evidence separately; no secrets/full provider payloads in portable results.

`run` records stable runId, attemptId, resumeOf (previous attempt or null), briefHash,
and pinned method/campaign ledger references with hashes. Results on resume are
cumulative for that run, never additive report totals. `ledgerDelta` contains
unique candidate personRefs, qualifying findingRefs and the same runId/briefHash,
plus method-new/campaign-new/fresh subsets where novelty is proven. The host owns
idempotent commit and records commit status; an uncommitted delta is not persisted
state. See tracking.md for union, retry and commit semantics.
