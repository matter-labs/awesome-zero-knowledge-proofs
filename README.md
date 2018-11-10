# Awesome zero knowledge proofs (zkp)

> A curated list of awesome things related to learning zero knowledge proofs

## Contents

- [General introduction](#general-introduction)
- [Applications](#applications)
- [Comparison of the most popular zkp systems](#comparison-of-the-most-popular-zkp-systems)
- [SNARKs](#snarks)
- [STARKs](#starks)
- [Bulletproofs](#bulletproofs)
- [Social media](#social-media)

## General introduction

- [Zero Knowledge Proofs: An illustrated primer by Matthew Green](https://blog.cryptographyengineering.com/2014/11/27/zero-knowledge-proofs-illustrated-primer/)
- [Demystifying zero-knowledge proofs](https://docs.google.com/presentation/d/1gfB6WZMvM9mmDKofFibIgsyYShdf0RV_Y8TLz3k1Ls0/edit#slide=id.p) (math-heavy, awesome introduction into underlying cryptography)
- [Introduction to SNARKs/STARKs by Eli Ben-Sasson](https://www.youtube.com/watch?v=VUN35BC11Qw) (YouTube)

[More complete curated list of implementations and scientific ressources](https://zkp.science)

## Applications

### Active

- [Zcash: Privacy-Protecting Digital Currency](https://z.cash) (SNARKs)
- [Monero: Private Digital Currency](https://www.getmonero.org) (Bulletproofs)

### Work in progress

- [Coda: A Constant-Size Blockchain](https://codaprotocol.com) (recursive SNARKs)
  - [YouTube introduction](https://www.youtube.com/watch?v=qCVACpgQSjo)
- [Grin: Simple, privacy-focused, scalable MimbleWimble chain implementation](http://grin-tech.org) (Bulletproofs)
- [Rollup: Ethereum Plasma on SNARKs](https://github.com/barryWhiteHat/roll_up)
  - [chatroom on gitter](https://gitter.im/barrywhitehat/roll_up)
- [Gnosis dFusion: DEX on SNARKs](https://github.com/gnosis/dex-research/tree/master/dFusion)

## Comparison of the most popular zkp systems

|                                       | SNARKs                     | STARKs                        | Bulletproofs    |
| ------------------------------------: | -------------------------: | ----------------------------: | --------------: |
| Algoritmic complexity: prover         | O(N * log(N))              | O(N * poly-log(N))            | O(N * log(N))   |
| Algoritmic complexity: verifier       | ~O(1)                      | O(poly-log(N))                | O(N)            |
| Communication complexity (proof size) | ~O(1)                      | O(poly-log(N))                | O(log(N))       |
| - size estimate for 1 TX              | Tx: 200 bytes, Key: 50 MB  | 45 kB                         | 1.5 kb          |
| - size estimate for 10.000 TX         | Tx: 200 bytes, Key: 500 GB | 135 kb                        | 2.5 kb          |
| Ethereum/EVM verification gas cost    | ~600k (Groth16)            | ~2.5M (estimate, no impl.)    | N/A             |
| Trusted setup required?               | YES :(                     | NO :)                         | NO :)           |
| Post-quantum secure                   | NO :(                      | YES :)                        | NO :(           |
| Crypto assumptions                    | Strong :(                  | Collision resistant hashes :) | Discrete log :) |

## SNARKs

### Learn

Get started:
- [Introduction to zk-SNARKs with examples](https://media.consensys.net/introduction-to-zksnarks-with-examples-3283b554fc3b)
- [What are zk-SNARKs (Zcash blog)](https://z.cash/technology/zksnarks)

Zcash blog series:
- [Explaining SNARKs Part I: Homomorphic Hidings](https://z.cash/blog/snark-explain/)
- [Explaining SNARKs Part II: Blind Evaluation of Polynomials](https://z.cash/blog/snark-explain2)
- [Explaining SNARKs Part III: The Knowledge of Coefficient Test and Assumption](https://z.cash/blog/snark-explain3/)
- [Explaining SNARKs Part IV: How to make Blind Evaluation of Polynomials Verifiable](https://z.cash/blog/snark-explain4)
- [Explaining SNARKs Part V: From Computations to Polynomials](https://z.cash/blog/snark-explain5/)
- [Explaining SNARKs Part VI: The Pinocchio Protocol](https://z.cash/blog/snark-explain6)
- [Explaining SNARKs Part VII: Pairings of Elliptic Curves](https://z.cash/blog/snark-explain7)

Vitalik Buterin's blog series on SNARKs:
- [Part 1: Quadratic Arithmetic Programs: from Zero to Hero](https://medium.com/@VitalikButerin/quadratic-arithmetic-programs-from-zero-to-hero-f6d558cea649)
- [Part 2: Exploring Elliptic Curve Pairings](https://medium.com/@VitalikButerin/exploring-elliptic-curve-pairings-c73c1864e627)
- [Part 3: Zk-SNARKs: Under the Hood](https://medium.com/@VitalikButerin/zk-snarks-under-the-hood-b33151a013f6)

Protocol descriptions:
- [zkSNARKs in a Nutshell](http://chriseth.github.io/notes/articles/zksnarks/zksnarks.pdf)
- [Groth16 protocol](https://eprint.iacr.org/2016/260.pdf) (original paper)
- [Zcash Sapling protocol spec](https://github.com/zcash/zips/blob/master/protocol/sapling.pdf) (very useful as detailed cheat-sheet of all cryptography used)

### Try

- [libsnark (C++)](https://github.com/scipr-lab/libsnark)
  - [great tutorial](https://github.com/christianlundkvist/libsnark-tutorial)
- [bellmnan (rust)](https://github.com/zkcrypto/bellman/)
  - [demo circuit](https://github.com/ebfull/bellman-demo)
- [jsnark (Java, bindings to libsnark)](https://github.com/akosba/jsnark)
- [snarky (Ocaml, from authors of Coda)](https://github.com/o1-labs/snarky)
- [zokrates (toolbox for zkSNARKs on Ethereum)](https://github.com/Zokrates/ZoKrates)
- [ethsnarks by HarryR (alternative toolkit for viable zk-SNARKS on Ethereum, Web, Mobile and Desktop)](https://github.com/HarryR/ethsnarks)

### Scaling the prover

- [DIZK: Java library for distributed zero knowledge proof systems with Apache Spark](https://github.com/scipr-lab/dizk) (see the [research paper](https://eprint.iacr.org/2018/691))
- [SnarkyGPU: distributed GPU based zkSNARKs prover](https://github.com/matterinc/snarkyGPU) (work in progress)

### Multi-Party Ceremony (MPC) for Trusted Setup

- [“Powers of Tau” protocol for scalable generation of structured reference string](https://eprint.iacr.org/2017/1050)
- [Implementation of ZCash MPC Ceremony, Part I: "Powers of Tau"](https://github.com/ebfull/powersoftau)
  - [Independent implementation in Go](https://github.com/FiloSottile/powersoftau/)
- [Implementation of ZCash MPC Ceremony, Part I: "Sapling Circuit"](https://github.com/zcash-hackworks/sapling-mpc)

## STARKS

<div>
	<img width="200" src="starks.jpg" alt="STARKS">
</div>

Introduction:
- [Transparent Succinct Arguments by Alessandro Chiesa (Oct 2018)](https://gist.github.com/Haseeb-Qureshi/f552fdbbb649ed4bbfeb681beb4091e1)
- [State of the STARK by Eli Ben-Sasson (Devcon IV, Oct 2018)](https://drive.google.com/file/d/1Osa0MXu-04dfwn1YOSgN6CXOgWnsp-Tu/view) ([video](https://www.youtube.com/watch?v=1KSwVIZ82hs))

Vitalik Buterin's blog series on STARKs:
- [Part I: Proofs with Polynomials](https://vitalik.ca/general/2017/11/09/starks_part_1.html)
- [Part II: Thank Goodness It's FRI-day](https://vitalik.ca/general/2017/11/22/starks_part_2.html)
- [Part III: Into the Weeds](https://vitalik.ca/general/2018/07/21/starks_part_3.html)

A Hands-On Tutorial for Zero-Knowledge Proofs by Shir Peled (StarkWare):
- [Part I](http://www.shirpeled.com/2018/09/a-hands-on-tutorial-for-zero-knowledge.html)
- [Part II](http://www.shirpeled.com/2018/10/a-hands-on-tutorial-for-zero-knowledge.html)
- [Part III](http://www.shirpeled.com/2018/10/a-hands-on-tutorial-for-zero-knowledge_2.html)
- [Appendix](http://www.shirpeled.com/2018/10/a-hands-on-tutorial-for-zero-knowledge_4.html)

Academic ressources:
- [The STARK paper](https://eprint.iacr.org/2018/046.pdf)
- [libstark implemenation](https://github.com/elibensasson/libSTARK)

More ressources available at [starkware.co](https://www.starkware.co)

## Bulletproofs

[Introduction and collection of ressources](https://crypto.stanford.edu/bulletproofs/)

## Social media

Stay tuned!

- [Awesome zero knowledge twitter list](https://twitter.com/gluk64/lists/awesome-zkp)
- [Zero-knowledge podcast](https://www.zeroknowledge.fm)
