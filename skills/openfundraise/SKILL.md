---
name: openfundraise
description: Answer questions about a nonprofit's fundraising with the OpenFundraise tools - totals, breakdowns, campaigns, donations, supporters, events and tickets, recurring giving, attribution, checkout conversion, experiments, peer-to-peer pages and payouts. Use when the user asks about their OpenFundraise organization's donors, gifts, campaigns or events.
---

# Working with OpenFundraise

The OpenFundraise tools read live data for the organizations the signed-in person belongs to. Each person sees only what their role allows in the OpenFundraise dashboard, so a tool can return a permission message for one person and data for another.

## Pick the organization

Call `list_organizations` when you don't know which organization the user means, or when a tool says more than one organization is available. Pass the organization's slug as `organization` on later calls.

## Pick the right tool

| Question | Tool |
| --- | --- |
| How much did we raise, and how does it compare with before? | `get_fundraising_overview` |
| Totals split by campaign, channel, designation, payment method, device, location, event or UTM | `get_donation_breakdown` |
| Campaign progress against goals | `list_campaigns` |
| Specific gifts, newest first, with filters | `search_donations`, then `get_donation` for one gift |
| A donor's profile and history | `search_supporters`, then `get_supporter` |
| Events, ticket types, registrations, attendees and check-ins | `list_events`, then `get_event` |
| New, renewing, failing and cancelled recurring plans | `get_recurring_analytics` |
| Where online donors came from | `get_traffic_attribution` |
| Checkout drop-off | `get_checkout_funnel` |
| A/B test results | `get_experiments` |
| Peer-to-peer and team pages | `list_p2p_fundraisers` |
| Payouts, processor fees and net received | `list_payouts` |

Use `get_donation_breakdown` for totals by any dimension. Paging through `search_donations` to add up gifts is slower and can miss gifts.

## Read amounts carefully

Summaries report USD. Individual gifts keep their original currency and also show USD values. "Raised" includes donor-covered fees; check each tool's money definitions before you compare numbers from different tools.

## Actions

`resend_receipt` emails a donor's receipt again to the address on file, and `add_supporter_note` adds an internal staff note. Show the user exactly what will happen, including the note's wording, and wait for them to agree before you call either one.

## Privacy

Donor names, emails, phone numbers and addresses are private to the organization. Share them only with the signed-in user, and leave them out of the `context` argument the tools accept.

## When a tool is missing

If no tool can do what the user asked, such as refunds, exports or sending messages, say so plainly and call `get_more_tools` with a short description of what was needed. That records the request for the OpenFundraise team.
