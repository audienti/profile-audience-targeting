---
name: profile-audience-targeting
description: Find ICP and Role matches among people commenting on or reacting to content by selected influencers, competitor personnel, partners, customers or other professional profiles. Discover suitable source profiles when none are supplied. Requires observable activity and exact participants; reliable LinkedIn tracking needs a connected activity collection tool. Native search supports discovery and qualification.
---

# Profile audience targeting

Find suitable people in a selected profile's audience. The source may be an
influencer or competitor employee who is not an ICP match. Prospect qualification
applies to the audience members, independently of the source profile.

Read [the common research rules](references/research.md),
[seed discovery](references/seeds.md), [tracking state](references/tracking.md) and
[the result contract](references/result.md). These shared files travel with both
skills; neither skill requires the other to execute.

## Follow incoming participation

1. Resolve supplied source profiles or discover a bounded set of sources whose
   audiences plausibly include the target people. Record relationship category
   separately from acquisition method. Follow the full brief, not just keywords.
2. Inspect posts actually authored by that exact source. Establish the original
   post and author, publication date and inspected content. Reposts retain the
   original author and engagement target; ambiguous targets stay unresolved.
3. Inspect actual comments and reactions on the selected post. Reject people from
   another post, sidebars or suggested-profile lists. A matching name is not a
   matching identity. The candidate is
   the comment/reaction actor. Preserve actor profile link/ID, interaction target,
   direction=`incoming`, observation time and event time when known. A reply's
   parent comment and actor must also be retained when relevant. Replies on the
   seed's own posts are part of its audience; replies to its comments on other
   authors' posts are outside this skill's post-audience scope.
4. Resolve the participant's current role and employer using attributable
   evidence, then independently assess company ICP and person Role. The source's
   employer, expertise or buying role never transfers to its audience.
5. Return qualified, needs-evidence and not-fit people with source profile → post
   → interaction → person → employer evidence. Keep repeat observations and
   newly qualified people separate from campaign-new people.

## Collection capability and native support

Resolve the exact supplied source with the available collection tool. Use native
search when needed to discover or disambiguate the source, and inspect publicly
available original posts and comments when they supply the required evidence. Search snippets can locate posts but do not
alone establish an unseen interaction or current role. Public post pages may
expose only a small comment sample. Record visible actor links, not just names.
Reaction counts are not a list of reactors. Login-required content is blocked,
not empty. Do not use search-engine cache mirrors or unrelated domains as identity
proof when the original source cannot be verified.

Prefer source-specific queries and source activity views after selecting the
profile. Topic queries may discover a seed, but subsequent evaluation must follow
that seed's activity rather than silently becoming topic-based prospecting.
Inspect current posts within the configured window. Historical pages can prove
mechanics in a separately labelled exercise; they do not count as fresh yield.

Use a connected collector that passes the shared capability preflight for
reliable LinkedIn tracking. Native-only partial research remains separately
measured. APIs may supply reaction lists, pagination and identity evidence. Retain tool mode
per observation and compare matched scenarios; never mix paid cached results into
a native-only qualification count. A blocked reactor list does not prevent a
useful commenter pass. Do not claim exhaustive coverage with either access mode.

Default bounded pass: up to 3 authored posts per profile, 3 comment pages and
3 reaction pages per post, subject to the smaller person/request/spend ceiling.
Use the brief's participant kinds; default to commenters when unspecified and
include reactions when requested or configured. On repeat
passes revisit recent posts for new participants even when no new post appears.

For people a source engages with on other authors' content, use the separate
`profile-engagement-targeting` skill. Do not merge its denominator or yield with
this audience-targeting pass.

Treat a seed's repost-with-commentary wrapper as eligible only when it has its own
resolved seed-authored target and the interaction attaches to that wrapper.
Engagement on the original belongs to the original author; exclude it as
repost_original_target. An unseparated or merged reactor list is unresolved_target,
not the wrapper's audience. Preserve wrapper and original IDs independently.

If a returned profile ID differs from the observed actor, require an explicit
alias bridge. Without one, keep the observed actor as a separate unresolved person
(needs_evidence, novelty unknown); never inherit another identity's fit or count.
