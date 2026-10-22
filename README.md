# Offer Card

An interactive lead magnet: 12 simple questions, one per screen, that turn into a clear Offer Card. The second instance of the Lead Magnet Machine.

- Live: https://yogizoli.github.io/offer-card/
- Concept (decisions, do not reopen): Drive doc "Offer Card Clarified Concept"

## How it works

- Static site, one `index.html`, no backend, no AI, zero tokens. Hosted on GitHub Pages.
- Same pattern as `freedom-calculator`, `ghl-income-calculator` and `yt-band-channel-wizard`, built directly in the unified brand design (Shine v3 tokens from `YogiZoli/design-system`).
- Answers are saved in the visitor's browser under the `localStorage` key `offer_card_state`.
- `vendor/` holds jsPDF and html2canvas, the same files as the other lead magnets.

## The 12 components

Who it's for, Big Promise (result plus timeframe), the "even if", Name, Format and Duration, Teaching, Interaction, Community, Support, Bonuses and Extras, Price plus Reason to Act Now, Risk Reversal. Each screen says why it asks, and the result shows the GHL counterpart of each component.

## JSON schema v1

`window.OfferCard.data()` returns the `offer` object with these stable keys:

`name, subtitle, who_for, problem, not_for, promise_result, promise_timeframe, even_if, format, duration, teaching[], interaction, community, support, bonuses[], price, payment_plan, act_now_reason, risk_reversal`

The Launch Engine export (phase 3) maps them to `offer_name`, `offer_promise` and `offer_price_display`.

## Settings

At the top of the script: `WEBHOOK_URL` (email gate, phase 4). Empty means no POST.

## Status

- Phase 1: question list and schema. Done.
- Phase 2: questionnaire and result page. Done.
- Phase 3: PDF and Launch Engine export block.
- Phase 4: email gate.
- Phase 5: first real Offer Card (Biz In A Box).
