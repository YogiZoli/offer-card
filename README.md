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

At the top of the script: `WEBHOOK_URL`, a GHL Inbound Webhook. Empty means no POST, the card is still shown.

## Email gate

After question 12 the visitor gives first name and email. The page posts `name, email, source ("offer-card"), offer_name` to the webhook. The GHL workflow "Lead magnet Offer Card" (sub-account YTC2C) creates or updates the contact and adds the tag `lead-magnet-offer-card`. The delivery email is NOT sent from here: the Lead Magnet Machine picks up the tag.

Inbound Webhook is a premium GHL trigger (a small charge per run).

For affiliates: the same file, with their own webhook URL pasted into `WEBHOOK_URL`.

## Status

- Phase 1: question list and schema. Done.
- Phase 2: questionnaire and result page. Done.
- Phase 3: PDF and Launch Engine export block. Done. The PDF is real text built with jsPDF from the answers, no AI. "Copy for Launch Engine" gives Markdown plus the JSON below, also as a .md download.
- Phase 4: email gate. Done, tested end to end (contact plus tag created in GHL).
- Phase 5: first real Offer Card (Biz In A Box).
