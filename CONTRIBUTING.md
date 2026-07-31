# Contributing

Applies to every repository in the [socialgravity](https://github.com/socialgravity)
organisation.

## The short version

These repositories are the public half of a private platform. The specification and the
verifier are published so that you can check our receipts without trusting us, and so that
anyone can implement the format independently. Contributions that make either of those easier
are very welcome.

## What is most useful

1. **An independent implementation.** If you write your own verifier against
   [the spec](https://github.com/socialgravity/receipts/blob/main/docs/receipt-spec-v1.md),
   open an issue and tell us. Anywhere your implementation disagrees with ours is a bug in
   one of them, and we want to know which.
2. **Spec ambiguity.** If two competent readers could canonicalise the same receipt into
   different bytes, that is a defect, not a nitpick. Report it.
3. **Verifier correctness.** A check that passes when it should not is the worst bug we can
   ship. See [SECURITY.md](SECURITY.md) if the finding is exploitable.
4. **Honesty defects.** If a claim in a README or in the spec is stronger than what the code
   actually proves, say so. We would rather publish a caveat.

## How changes land

The public repositories mirror artifacts from a private platform repository. Issues and pull
requests are read and answered here. Accepted changes land upstream first and flow back in the
next sync, so your patch may reappear as part of a larger commit rather than merged verbatim.
You will be credited either way.

## House rules

- Prose is plain. No marketing voice, no em dashes, no emoji in specs or copy.
- A claim goes in only if the code or the published data proves it. If it needs an asterisk,
  it does not go in.
- Code changes to the verifier need a test. `deno test --allow-read verifier/` must stay green.
