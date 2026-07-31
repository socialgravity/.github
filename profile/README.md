<div align="center">

# SocialGravity

**The licensing layer for human identity.**

A person verifies their face and voice, sets their terms, and licenses them for AI generated
content. Every authorised use carries a cryptographic receipt.

[![Website](https://img.shields.io/badge/site-socialgravity.ai-20231C?style=flat-square)](https://socialgravity.ai)
[![Docs](https://img.shields.io/badge/docs-verify%20a%20receipt-20231C?style=flat-square)](https://socialgravity.ai/docs)
[![Spec](https://img.shields.io/badge/receipt%20spec-v1-6B705C?style=flat-square)](https://github.com/socialgravity/receipts/blob/main/docs/receipt-spec-v1.md)
[![Verifier](https://img.shields.io/badge/verifier-Apache--2.0-6B705C?style=flat-square)](https://github.com/socialgravity/receipts)
[![Ledger](https://img.shields.io/badge/ledger-RFC%206962%20%2B%20RFC%203161-6B705C?style=flat-square)](https://github.com/socialgravity/ledger-anchors)

</div>

---

## Check one of our receipts yourself

No account, no key, no permission from us. One command, thirty seconds:

```sh
deno run --allow-net https://socialgravity.ai/docs/verify.js --license LDNAEEDY5UB
```

Real output, trimmed to four of the nineteen checks:

```text
SocialGravity receipt verification: licence LDNAEEDY5UB
base: https://id.socialgravity.ai/functions/v1

document and log
  PASS           external anchor
                 head timestamped by rfc3161 at 2026-07-31T07:07:01+00:00, covering
                 ledger seq 51 and so this entry at seq 45, which is what rules out
                 back-dating
  PASS           witnessed head
                 today's tree of 56 is a pure append of the publicly witnessed head of
                 30: nothing witnessed has been altered or removed

link 1: person
  NOT CHECKABLE  identity method
                 'document': a government ID was verified. Signed, but the check itself
                 is the issuer's

link 3: licence
  PASS           licence signature
                 Ed25519 verified against the pinned key

VERDICT: INCOMPLETE. 16 passed, 0 failed, 3 not checkable. Nothing contradicted the
receipt, but the lines above marked NOT CHECKABLE are assertions or unavailable data,
not proofs.
```

That is a real licence held by a real, document-verified person, and our own showcase run says
**INCOMPLETE**. It says so because three of its checks are ours to assert rather than yours to
confirm, and the tool will not launder that into a green tick. Three outcomes per check: PASS,
FAIL, or NOT CHECKABLE. A verifier that never says "I cannot check this" is not a verifier, it
is a logo.

Note the `witnessed head` line: that check reads the public
[ledger-anchors](https://github.com/socialgravity/ledger-anchors) mirror and proves today's log
is a pure append of a head we published earlier and cannot now edit.

The verifier fetches only public endpoints and does every check locally against a pinned key.

## What a receipt links

**person → asset → licence → generation → output**

| # | Link | What is on the record |
|---|---|---|
| 1 | **person** | A verified human, and the evidence of what they agreed to |
| 2 | **asset** | A fingerprinted version of their face or voice |
| 3 | **licence** | Signed terms: which assets, which use, which channels, which territories, for how long |
| 4 | **generation** | An authorised use, metered against those terms |
| 5 | **output** | The file that came out, watermarked and registered |

Each link is a signed record in an append-only transparency log. The log's head is timestamped
by an independent authority and mirrored to a public repository. So the answer to "did this
person agree to this" is a check you can run, not an email you have to believe.

## Why part of this is public

A receipt you have to trust us about is not a receipt. So the proof layer is open.

| Repository | What it is |
|---|---|
| [**receipts**](https://github.com/socialgravity/receipts) | The receipt format, its JSON Schema, the API surface, and a zero-dependency verifier you can run yourself. Code Apache-2.0, spec CC BY 4.0. Implement it independently, that is the point. |
| [**ledger-anchors**](https://github.com/socialgravity/ledger-anchors) | Head hashes of our append-only ledger, mirrored where we cannot quietly rewrite them. A witness against our own future selves. |

## Why the rest is not

The custody and enforcement layer stays closed, permanently: biometric template extraction and
matching, matching thresholds, watermark embedding and detection, KYC internals, and the gating
logic that enforces deals. Publishing those would help exactly one audience, the people trying
to defeat them.

**Anyone can verify what we claim. Nobody gets a manual for evading it.**

## Honesty notes

We would rather publish the caveat than the asterisk.

- The register is young. Our docs page marks which records are test data, and the spec says
  what is not yet provable.
- External anchoring began 2026-07-30. Nothing before that date has third-party proof of time.
- The verifier reports NOT CHECKABLE for anything it cannot prove locally, including checks
  that are ours to assert rather than yours to confirm.

## Where things are

- Product and docs: [socialgravity.ai/docs](https://socialgravity.ai/docs)
- API: `https://id.socialgravity.ai/functions/v1`
- Security reports: [SECURITY.md](https://github.com/socialgravity/.github/blob/main/SECURITY.md)
- Contact: [alvaro@socialgravity.ai](mailto:alvaro@socialgravity.ai)
