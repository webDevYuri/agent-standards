# Payment Gateway Integration

## Scope

* Apply this guide only when implementing a new payment gateway integration or a clearly new payment flow.
* Do not refactor, audit, or modify an existing payment gateway integration merely to make it match this checklist. Existing payment behavior is out of scope unless the user explicitly requests a payment change or a necessary security correction.
* Confirm the gateway’s current API, authentication, idempotency, webhook, and payment-state behavior from its official documentation before implementation.
* Never use real charges, customer accounts, payment methods, or production data for testing. Use the provider’s sandbox or local fakes.

## Required Safety Checklist

Before considering a new integration complete, address each applicable item and document any provider-specific limitation or deliberate exception.

1. **Idempotency key** — Use a stable idempotency key for retryable payment-creation requests so transport retries cannot create duplicate charges.
2. **Database unique constraints** — Enforce uniqueness for provider transaction IDs, payment references, idempotency keys, and other identifiers that must not repeat.
3. **Database transaction and row locking** — Protect payment and order state transitions from concurrent requests using an appropriate transaction and row-level locking strategy.
4. **Server-side payment validation** — Validate amount, currency, order, customer, and payment status on the server or through the provider; never trust payment-critical values from the client.
5. **Already-paid protection** — Refuse or safely no-op attempts to charge an order, invoice, subscription, or other business object that is already paid.
6. **Verified webhook** — Verify webhook signatures or the provider’s equivalent authenticity mechanism before reading or applying webhook data.
7. **Idempotent webhook processing** — Record and deduplicate provider events so retries do not repeat business updates or other side effects.
8. **Strict payment states** — Define allowed payment states and transitions. Do not mark a payment successful, failed, refunded, or cancelled through an invalid or unverified transition.
9. **Safe failure and timeout handling** — Treat timeouts and ambiguous responses as uncertain until resolved; do not assume success or failure solely because a request timed out.
10. **Payment attempt record** — Persist each meaningful payment attempt with its internal reference, provider reference, status, amount, currency, timestamps, and safe error information.
11. **Atomic business update** — Apply the payment result and its related business effect, such as order fulfillment or entitlement, atomically or through a deliberate recovery mechanism that cannot silently diverge.
12. **Audit and error logging** — Record enough structured audit and error information to support reconciliation, debugging, disputes, and support without logging secrets, full payment credentials, or unnecessary sensitive data.

## Completion Review

* Verify success, duplicate requests, duplicate webhooks, invalid signatures, already-paid attempts, invalid state transitions, provider errors, timeouts, and recovery of uncertain payments in a safe local or sandbox environment.
* Do not claim the integration is complete while an applicable checklist item is unaddressed, unverified, or silently replaced with an unsafe assumption.
