---
title: "Two Results on Common-Mask Unclonability"
date: 2026-07-30 17:18:04 +0800
permalink: /blog/common-mask-unclonability-results/
excerpt: "I prove a Goldreich-Levin search-to-decision theorem for arbitrarily entangled split states and an exponential upper bound for the uniform-mask I/X/Z parity game."
tags:
  - quantum cryptography
  - unclonable cryptography
  - Goldreich-Levin
  - monogamy of entanglement
read_time: true
share: false
related: false
---

I have proved two results about common-mask challenges in unclonable
encryption (UE).

## 1. A Goldreich-Levin theorem for UE

Fix any finite-dimensional UE token ensemble. Split one token between Bob and
Charlie before revealing the key \\(k\\) and a uniformly random common mask
\\(r\in\{0,1\}^n\\). Let \\(p_D\\) be the probability that both parties correctly
output \\(\langle r,m\rangle\\).

**Theorem.** If \\(p_D\geq1/2\\), there exist local one-copy measurements, with
no post-split communication, such that both parties recover \\(m\\) with
probability

\\[
p_S\geq(2p_D-1)^4.
\\]

Equivalently,

\\[
p_D=\frac12+\varepsilon
\quad\Longrightarrow\quad
p_S\geq16\varepsilon^4.
\\]

This holds for arbitrarily entangled post-split states and does not require
commuting decoders. It is an information-theoretic, possibly inefficient and
nonuniform reduction.

## 2. An exponential bound for the two-basis UE parity game

Sample \\(x,\theta,r\\) independently and uniformly from \\(\{0,1\}^n\\). Split
one BB84 state

\\[
\lvert x_\theta\rangle
=\bigotimes_{j=1}^n H^{\theta_j}\lvert x_j\rangle
\\]

before revealing the common question \\((\theta,r)\\). Both recipients must
output \\(\langle r,x\rangle\\) without communicating. Let \\(\omega_n\\) be the
supremum of their joint success probability over all finite-dimensional
splitting channels and local decoders.

**Theorem.** For every \\(n\geq1\\),

\\[
\omega_n\leq
\frac12\left[1+\left(\frac{\sqrt3}{2}\right)^n\right].
\\]

Thus

\\[
\omega_n-\frac12
\leq\frac12\left(\frac{\sqrt3}{2}\right)^n
=2^{-\Omega(n)}.
\\]

An explicit product Breidbart strategy gives the lower bound

\\[
\omega_n\geq
\frac12+
\frac12\left(\frac{1+1/\sqrt2}{2}\right)^n.
\\]

The bounds are not equal. The proof does not establish the exact value,
tightness, a product theorem \\(\omega_n=\omega_1^n\\), or a bound for
infinite-dimensional or commuting-operator strategies.


## Public timestamp and provenance

<div class="notice--info" markdown="1">
**Timestamped claim statement**

- [Approved statement](/files/provenance/common-mask-results-statement-v1.txt)
- SHA-256: `e8d5caf37125fe5a5755833b98c3d7fbd874002346cf90e6944b93767dce6ae1`
- [OpenTimestamps proof](/files/provenance/common-mask-results-statement-v1.txt.ots)
- [Public Git history](https://github.com/zoeabcd/zoeabcd.github.io/commits/master/files/provenance/common-mask-results-statement-v1.txt)

To verify, download the statement and its `.ots` proof and use the
[OpenTimestamps verifier](https://opentimestamps.org/). The proof was submitted
to independent public calendars at publication; Bitcoin confirmation may
initially appear as pending and can then be upgraded by the verifier.
</div>

The timestamp binds the exact approved statement and the SHA-256 digests of
both source manuscripts, rather than a manually entered page date.
