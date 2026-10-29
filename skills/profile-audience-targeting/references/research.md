# Shared research rules

## Brief, identities and criteria

Read the full offer, problem/premise, company ICP, person Role, exclusions, time
window, participant kinds and limits. Respect independent criteria per case. The
seed relationship is not an ICP criterion. Do not gate a source on buyer fit.

Use actual observed profile URLs/provider IDs; never generate them from names.
Link aliases only with evidence. Resolve current employer to an exact company
identity; a name similarity is insufficient. Native tools can establish identity
through linked official biographies/team pages without requiring a provider ID.
Preserve conflicts between sources instead of selecting a convenient one.

For every required company and person criterion record `met`, `not_met` or
`unknown`, explanation and evidence. Missing criteria do not pass. Hard failures
give `not_fit`; incomplete/conflicting evidence gives `needs_evidence`; complete
required fit plus verified relevant participation and requested freshness gives
`candidate`; proven stale evidence is `outside_window`, unknown freshness is
`needs_evidence`. Keep fitStatus separate from time eligibility. Actor words,
topic relevance, ICP, Role, buyer pain and intent are separate judgments. A reaction
by itself does not establish need, stance, intent or outreach consent.

Honor geography at the configured entity. Person location is not company location.
An office does not prove a required lending/underwriting operation. Keep employee
band and associated profile count distinct; do not choose whichever crosses the
threshold. Historic employment is not current; conflicting dates/current flags
need a bounded exact-person check. Cached facts may support retrospective replay;
their original observation time and age remain visible.

## Acquisition modes and evidence

Native search/open can discover sources and qualify people, and can collect
interactions where the full evidence is publicly visible. Reliable LinkedIn
activity collection must pass the capability preflight below. Declare any
connected-tool requirement explicitly. Native tool costs are unknown unless
exposed; no external API spending is not "zero total cost".

Declare the skill, brief/version, source set, time interval, seen identities,
per-source limits and tool mode. Do not mix cached API identity/fit facts into a
native-only result. Reusing the accepted brief is fine. Preserve acquisition mode
per fact, not only in a run label. Raw engagements or novel URLs are not qualified
people; report actual coverage and unique matches with unknowns separately.

On access denial or rate limiting, record blocked status and respect retry guidance.
Do not cycle through alternate endpoints/accounts to evade a 999/429 restriction.
Continue independent public evidence work; disclose any inaccessible source.

Spend only within the run's explicit budget; log requests before execution and
keep authoritative receipts. Cache reuse does not reset observation time. Unknown
charges after timeout remain unknown and reserve budget. No outreach, CRM writes,
account connections or monitoring schedules are created by either skill.

## Activity access preflight

Before promising tracking, verify a tool can retrieve the required activity and
exact identities. For LinkedIn audience targeting this means source-authored posts
plus their comment/reaction actors; for engagement targeting it means the source's
outgoing comments/reactions plus each exact post/comment target and author. A
profile lookup or posts-only API does not supply outgoing activity. Validate actual
returned fields, pagination and event timestamps, not just an endpoint name.

Reliable LinkedIn tracking requires a connected activity collection tool; an API
is preferred where available and authorized, within authorized spend. A user-provided
export or connected browser with the same evidence can also satisfy the contract.
A connected browser means a user-authorized session or tool already supplied by
the host, not a login performed in the agent research browser. Native web search remains useful for seed discovery, official company evidence and
Role qualification. Publicly observable native activity can support explicitly
partial findings, but search snippets alone are not a reliable tracking baseline.
Do not claim native and API acquisition have equivalent coverage, timestamps or
identity evidence. Exports must also supply the required fields.

If no suitable connected tool is available, return a specific missing-capability
status for that path. Do not ask the user to sign in to an agent research browser
as a workaround. Do not assume browser authentication or install/connect a service
without the applicable authorization. Preserve independent useful native work;
blocked collection is not zero prospect fit, `not_fit`, or `outside_window`. Provider fallbacks for incomplete
fields must be bounded and recorded, not used to evade access denial.

## Time and coverage

Publication time, event time and observation time are different facts. Preserve
relative dates as relative or explicitly bounded intervals; do not manufacture an
exact date from a vague label. Unknown reaction time remains null. The exact target publication
(comment publication for comment reactions) and source observation can bound an event only if the exact target was resolved, and a
window pass requires the entire interval inside that window. ID-derived dates
alone do not establish a verified published/event date.

Record blocked, failed, capped, exhausted and not_reached separately per source and
participant type. A native page's first visible comments are a sample. Counts do
not identify hidden reactors; missing actors on a partial page are not evidence
of removed engagement. A skill can return a useful partial result without complete
network coverage. It must not claim a successful positive discovery when all
required paths remain blocked or all fit decisions remain unknown.

Normalize time zones before comparing dates. Default clock tolerance is zero;
any explicit nonzero tolerance must be declared before collection, not chosen to
rescue a result. An event/publication time later than its observation beyond that
tolerance, a reversed interval, or conflicting stamps gives freshness unknown,
basis unresolved and a required date_conflict entry in gaps. Do not discard the conflicting stamp
and promote using a publication-to-observation interval. Date-only and relative
stamps retain their full timezone/rounding uncertainty; if this cannot be bounded,
freshness stays unknown. Preserve raw stamps and any explicit normalization.
Absent an independent hard fit failure, unresolved conflicting time means
needs_evidence. Historical or unresolvable-time evidence may be archived without
further retries; it does not become a fresh candidate by repetition.

A date_conflict exclusion is optional when discarding an individual evidence item;
it never replaces the required gap or permits promotion past the conflict.
