# Profile Audience Targeting

Find ICP and Role matches among commenters and reactors on selected professional profiles’ posts.

An agent skill for Claude Code and Codex. Supply your own company ICP, person Role requirements, source profiles, time window and research budget. The source profile does not need to match the ICP. This skill follows their authored posts → commenters/reactors.

## Install

Add the Audienti marketplace and install this plugin:

```sh
claude plugin marketplace add audienti/plugins
claude plugin install profile-audience-targeting@audienti
```

For Codex:

```sh
codex plugin marketplace add audienti/plugins
codex plugin add profile-audience-targeting@audienti
```

You can also load `skills/profile-audience-targeting/SKILL.md` directly in a skill-compatible agent host. All four references are bundled; no sibling skill is required.

## Use

Ask your agent:

> Use profile-audience-targeting. Track [source profile URL] for the last seven days. My company ICP is [criteria]; my person Role definition is [criteria]. Inspect at most three pages per source, use my connected research tools within [budget], and return qualified people with exact interaction evidence. Use [previous qualified-person ledger], or mark novelty unknown if unavailable.

For audience targeting specify commenters, reactors, or both. Results keep company fit, Role fit, freshness, identity, coverage and previously qualified people separate. Engagement is not evidence of buying intent.

## Required capabilities

Reliable LinkedIn collection requires a connected tool that exposes the selected activity and exact identities. TREG was used in the live verification. TREG and other providers are not bundled, installed or authenticated by this plugin. Discover the available tools in your host, inspect their current schemas and verify the activity fields before execution. Native search supports source discovery and qualification; native-only collection may be partial or blocked. Composio has not been verified for this package.

The audience route requires authored posts and their commenters/reactors. The engagement route requires outgoing activity with exact targets; an incoming reactor list does not substitute for it. Verify current roles and employers independently against the supplied brief. If a capability is unavailable, report it explicitly and retain useful partial work.

## State and boundaries

The skill returns evidence-backed research and tracking deltas. Your host owns durable ledger storage and scheduling. An omitted ledger means unknown novelty, not an empty campaign. This package does not install a scheduler, write a CRM, send outreach or start provider calls on installation.

## Verification

Version 1.0.0 preserves the independently reviewed skill and four reference files. Both routes were executed through an agent using live TREG activity and refreshed profile/company evidence. Two previously researched audience matches were revalidated; this proves the functional paths, not a new-prospect yield or conversion-rate improvement. Reprocessing the same evidence added no duplicate people; this was not a second live poll. Coverage was bounded. Customer-specific test data and provider responses are not distributed.
