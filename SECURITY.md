# Security policy

Applies to every repository in the [socialgravity](https://github.com/socialgravity)
organisation, and to the platform behind them.

## Reporting

Email **alvaro@socialgravity.ai**. Put `SECURITY` in the subject. Include what you did, what
you observed, and how you would prove it to a third party. We answer within 72 hours.

If it is easier for you, open a private security advisory on the affected repository instead.
Please do not open a public issue for anything exploitable.

## What we care about most

This is identity infrastructure, so the highest-severity class is not availability. It is
anything that lets a claim be believed that is not true:

1. **A forged or altered receipt that our verifier accepts.** Signature bypass, canonical byte
   ambiguity, an inclusion proof that validates against the wrong tree, a rewritten log head.
2. **Anything that lets the ledger be changed after the fact** without the anchors, the log
   consistency check, or the public mirror catching it.
3. **Consent or scope escalation.** A licence appearing to cover an asset, a use case, a
   channel, a territory or a period that the signed scope does not cover.
4. **Exposure of biometric material or identity documents.** Templates, source samples, KYC
   artifacts.

Denial of service against public verification endpoints is in scope but low severity. Findings
that need us to be dishonest for the attack to work are not findings.

## What is out of scope here

The custody and enforcement layer is not published: biometric matching and thresholds,
watermark embedding and detection, deal gating, KYC internals. You are welcome to attack the
public endpoints and the published format. Please do not attempt to obtain the closed material
itself, and do not use real third-party identities in your testing.

## Disclosure

Report privately, give us a reasonable window to fix, then publish whatever you like. We will
not ask you to stay quiet and we will credit you unless you prefer otherwise. If a finding
means something we published was overclaimed, the correction gets published too.
