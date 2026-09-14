# DP-001 — Conversion Content OS

Status: product in production; offer integration is intentionally isolated from `main` until the release package and exact source-license map are complete.

## Purpose

Integrate Conversion Content OS into the existing `e-com.casa/offers/[slug]` architecture without creating a parallel checkout or funnel engine.

## Recommended slug

`conversion-content-os`

## Release gate

Do not register the offer on the public registry until all of the following are true:

- source/license mapping is complete for the three primary PLR sources;
- core manuscript is release-ready;
- Hook Library and Conversion Workbook exist in the delivery package;
- actual bonuses match the sales copy;
- product/catalog entity and price are approved;
- checkout/delivery path is defined;
- no fabricated testimonial, rating, result, scarcity or deadline is present.

## Offer positioning

**Core promise:** Build a repeatable content-and-conversion workflow that helps the user decide what to say, how to structure it, how to adapt it to each channel and how to test the result.

The product must not be marketed as a guaranteed revenue or conversion-uplift system.

## Page architecture

1. Hero — problem recognition and clear transformation.
2. Why more content is not the same as better messaging.
3. Mechanism — Relevance → Attention → Interest → Trust → Desire → Action → Test.
4. Demonstration — real before/after messages and Hook Engine outputs.
5. Modules and toolkit.
6. Channel use cases.
7. Who it is for / not for.
8. Product components and verified bonuses.
9. FAQs and limitations.
10. Offer + checkout CTA.

## Proposed hero direction

**Headline:** Turn one commercial idea into a complete set of hooks, content and conversion messages — without relying on random prompts or manipulative clickbait.

**Subheadline:** A practical operating system for landing pages, email, social video, ecommerce, WhatsApp and paid media, with frameworks, templates, prompts and a reusable workflow.

CTA wording remains provisional until pricing and checkout are approved.

## Product stack

- Core guide / ebook
- Hook Library
- CTA & Offer Swipe File
- Prompt Library
- Content Repurposing Matrix
- Conversion Workbook
- Landing Page Blueprint bonus
- Email Conversion Pack bonus
- Optional Hook Generator when software is live

## Existing repository fit

The repository already uses a dynamic `src/app/offers/[slug]` route, offer registry/resolver and a campaign-specific render component. DP-001 should use this existing system rather than introduce another funnel framework.

The current offer route intentionally keeps campaign social proof separate from factual SEO structured data. Preserve that behavior for DP-001: no rating/review schema until a verified review source exists.

## Implementation sequence

1. Create the catalog/digital-product entity or extend the resolver to support a digital deliverable without weakening physical-product saleability rules.
2. Create `src/data/offers/conversion-content-os.ts` only after product data is stable.
3. Register the offer in `src/lib/offers/registry.ts`.
4. Add delivery-aware CTA/checkout behavior.
5. Add a digital-product-safe structured-data model.
6. Add success/delivery activation flow.
7. Validate localization/market behavior.
8. Run build/lint and preview QA before merging.

## Important architecture note

Do not force a digital product through assumptions that only make sense for physical catalog items. If the current `resolveOffer` or saleability layer requires a physical SKU, introduce an explicit digital-product type/path rather than bypassing validation.

## Sales integrity rules

- No demo reviews presented as real customers.
- No fake countdowns or invented seat/inventory constraints.
- No authority/celebrity endorsement without evidence.
- No guaranteed income or performance claims.
- Advertorial/pre-sell pages must not impersonate independent journalism.
- Checkout must disclose price, billing model, delivery format and applicable cancellation/refund terms before payment.

## Hook Generator

The interactive Hook Generator is a separate executable module. It may later be surfaced from the DP-001 offer/product area, but it should not block the initial core-product release. Its server-side generation logic must validate proof assumptions and reject fake proof/scarcity patterns.

## Coordination

This branch is intentionally documentation-first to avoid colliding with concurrent work on `main`. Functional integration can continue here once the product release gate is satisfied.
