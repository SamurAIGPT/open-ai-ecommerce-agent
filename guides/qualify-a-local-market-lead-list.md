# Qualify a Local Market Lead List

This walkthrough uses the live `local.business_search` capability to build a first-pass list of public local-business listings. It follows the [Local Business Leads skill](../agents/local-business-leads/SKILL.md).

## Example request

> Find independent fitness studios that may need a new website and rank the results by public review signals. I’m researching Austin, Texas.

## Important location limit

The current Muapi-backed search filters by **country**, not city, neighborhood, or radius. Adding “Austin” to a keyword is not a verified city filter. This walkthrough can produce a country-level candidate set and a manual verification queue; it cannot claim to return “Austin studios” as a complete or geographically bounded set.

## Workflow

1. Confirm the business category, country, lead criteria, and intended use. Keep the search read-only; do not contact the businesses.
2. Check the live `local.business_search` schema and current price. Search the category within the supported country scope and preserve the exact query, filters, timestamp, and result count.
3. Deduplicate chain locations and near-identical listings. Keep the returned address and listing identifiers so a human can verify the geography.
4. Apply only the requested public criteria, such as rating, review count, or website presence. Treat “no website found” as a search result, not proof that the business has no website.
5. Create two outputs: a candidate list for the supported country-level search, and a separate “needs location verification” list for any city-specific target. Do not use keyword match alone to claim city membership.
6. Summarize the search scope and the number of candidates that pass each qualification step. Include pull time and the underlying listing links/IDs where available.

## Suggested output columns

Business name, returned address, category, rating, review count, website/contact field if returned, qualification criteria passed, location verification status, and source/pull timestamp.

## Failure handling and next step

If the endpoint is unavailable or returns partial data, report that directly. If precise city targeting is essential, ask for an approved city-level source or a user-provided export and label the source. Outreach, CRM imports, or listing edits are separate actions and are not part of this guide.
