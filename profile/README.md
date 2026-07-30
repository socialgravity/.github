# SocialGravity

Licensing infrastructure for human identity. A person verifies their face and voice, sets
their terms, and licenses them for AI-generated content. Every authorised use carries a
cryptographic receipt linking the person, their permission, the licence, the generation and
the output.

## Why part of this is public

A receipt you have to trust us about is not a receipt. So the proof layer is open:

- [**receipts**](https://github.com/socialgravity/receipts): the receipt format, its JSON
  Schema, the API surface, and a zero-dependency verifier you can run yourself. Code
  Apache-2.0, spec CC BY 4.0. Implement it independently; that is the point.
- [**ledger-anchors**](https://github.com/socialgravity/ledger-anchors): hourly head hashes
  of our append-only ledger, mirrored here so the record of what we said, and when, is held
  by a third party we cannot quietly rewrite.

Verify a real licence right now:

```
deno run --allow-net https://socialgravity.ai/docs/verify.js --license L24SQXLKQFC
```

The custody and enforcement layer stays closed: biometric matching, thresholds,
watermarking, deal gating. Anyone can verify what we claim. Nobody gets a manual for
evading it.

## Where things are

- Product and docs: [socialgravity.ai/docs](https://socialgravity.ai/docs)
- API: `https://id.socialgravity.ai/functions/v1`
- Contact: [alvaro@socialgravity.ai](mailto:alvaro@socialgravity.ai)

We publish honestly or not at all: the docs page says which records are test data, and
external anchoring of our ledger began 2026-07-30, so nothing before that date has
third-party proof of time.
