# Awesome zero knowledge proofs (zkp)

> [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
> A curated list of awesome things related to learning zero knowledge proofs

## Contents

- [General introduction](#general-introduction)
- [Courses](#courses)
- [Applications](#applications)
- [Comparison of the most popular zkp systems](#comparison-of-the-most-popular-zkp-systems)
- [Bulletproofs](#bulletproofs)
  - [Halo](#halo)
- [SNARKs](#snarks)
- [SNORKs](#snorks)
  - [Sonic](#sonic)
  - [Marlin](#marlin)
  - [PLONK](#plonk)
- [STARKs](#starks)
  - [FRI-STARKs](#fri-starks)
  - [SuperSonic](#supersonic)
  - [Fractal](#fractal)
- [Social media](#social-media)

## General introduction

[Zero-Knowledge Proofs Starter Pack](https://ethresear.ch/t/zero-knowledge-proofs-starter-pack/4519): alternative introductory list for beginners (more videos).

- [Zero Knowledge Proofs: An illustrated primer by Matthew Green](https://blog.cryptographyengineering.com/2014/11/27/zero-knowledge-proofs-illustrated-primer/)
- [Demystifying zero-knowledge proofs](https://docs.google.com/presentation/d/1gfB6WZMvM9mmDKofFibIgsyYShdf0RV_Y8TLz3k1Ls0/edit#slide=id.p) ([video](https://www.youtube.com/watch?v=_6TqUNVLChc)) (math-heavy, awesome introduction into underlying cryptography)
- [Introduction to SNARKs/STARKs by Eli Ben-Sasson](https://www.youtube.com/watch?v=VUN35BC11Qw) (YouTube)
- [On Interactive Proofs and Zero-Knowledge: A Primer](https://medium.com/magicofc/interactive-proofs-and-zero-knowledge-b32f6c8d66c3)

A Hands-On Tutorial for Zero-Knowledge Proofs by Shir Peled (StarkWare):
- [Part I](https://www.shirpeled.com/2018/09/a-hands-on-tutorial-for-zero-knowledge.html)
- [Part II](https://www.shirpeled.com/2018/10/a-hands-on-tutorial-for-zero-knowledge.html)
- [Part III](https://www.shirpeled.com/2018/10/a-hands-on-tutorial-for-zero-knowledge_2.html)
- [Appendix](https://www.shirpeled.com/2018/10/a-hands-on-tutorial-for-zero-knowledge_4.html)

Zero-Knowledge Proofs for Engineers (Dark Forest)
- [Part I](https://blog.zkga.me/intro-to-zksnarks)
- [Part II](https://blog.zkga.me/df-init-circuit)

More complete curated list of implementations and scientific resources:
[https://zkp.science](https://zkp.science)

## Courses

- [The 9th BIU Winter School on Cryptography: Zero Knowledge](https://cyber.biu.ac.il/event/the-9th-biu-winter-school-on-cryptography/)
- [UIUC: ECE498AC/CS498AM: Applied Cryptography, Fall 2019](http://soc1024.ece.illinois.edu/teaching/ece498ac/fall2019/)

## Use cases

- [Awesome Privacy on Blockchains](https://github.com/Mikerah/awesome-privacy-on-blockchains)

## Applications

### Ethereum

- [ZK Sync](https://medium.com/matter-labs/introducing-zk-sync-the-missing-link-to-mass-adoption-of-ethereum-14c9cea83f58) by [Matter Labs](https://matter-labs.io)
  - [ZK SDK](https://zksync.io)
  - [ZK Sync code](https://github.com/matter-labs/zksync)
  - [ZK Sync live demo](https://demo.matter-labs.io)
- [SNARK-based permissioned database: rollup by BarryWhitehat](https://github.com/barryWhiteHat/roll_up)
- [Gnosis dFusion: DEX on SNARKs](https://github.com/gnosis/dex-research/tree/master/dFusion)
- [Loopring DEX Protocol (v3)](https://github.com/Loopring/protocols/blob/master/packages/loopring_v3/DESIGN.md)
- [zkPoD: A Practical Decentralized System for Data Exchange](https://github.com/sec-bit/zkPoD-node)
- [Dark Forest: zkSNARK space warfare strategy game](https://zkga.me/)

### Other blockchains

- [Zcash: Privacy-Protecting Digital Currency](https://z.cash) (SNARKs)
  - [chatroom](https://chat.zcashcommunity.com/channel/zapps-wg)
- [Monero: Private Digital Currency](https://www.getmonero.org) (Bulletproofs)
- [Coda: A Constant-Size Blockchain](https://codaprotocol.com) (recursive SNARKs)
  - [YouTube introduction](https://www.youtube.com/watch?v=qCVACpgQSjo)
- [Grin: Simple, privacy-focused, scalable MimbleWimble chain implementation](https://grin.mw/) (Bulletproofs)
- [Beam: Private and Scalable Coin based on MimbleWimble](https://www.beam.mw)

## Comparison of the most popular zkp systems

|                                       | SNARKs                     | STARKs                        | Bulletproofs    |
| ------------------------------------: | -------------------------: | ----------------------------: | --------------: |
| Algorithmic complexity: prover        | O(N * log(N))              | O(N * poly-log(N))            | O(N * log(N))   |
| Algorithmic complexity: verifier      | ~O(1)                      | O(poly-log(N))                | O(N)            |
| Communication complexity (proof size) | ~O(1)                      | O(poly-log(N))                | O(log(N))       |
| - size estimate for 1 TX              | Tx: 200 bytes, Key: 50 MB  | 45 kB                         | 1.5 kb          |
| - size estimate for 10.000 TX         | Tx: 200 bytes, Key: 500 GB | 135 kb                        | 2.5 kb          |
| Ethereum/EVM verification gas cost    | ~600k (Groth16)            | ~2.5M (estimate, no impl.)    | N/A             |
| Trusted setup required?               | YES :unamused:             | NO :smile:                    | NO :smile:      |
| Post-quantum secure                   | NO :unamused:              | YES :smile:                   | NO :unamused:   |
| Crypto assumptions                    | Strong :unamused:          | Collision resistant hashes :smile: | Discrete log :smirk: |

## Bulletproofs

- [Introduction and collection of resources](https://crypto.stanford.edu/bulletproofs/)
- [From Zero (Knowledge) to Bulletproofs](https://github.com/AdamISZ/from0k2bp) - a long and very nice gradual explanation
- [Bulletproofs](http://sikoba.com/docs/SKOR_DK_Bulletproofs_201905.pdf) - succinct and complete description of the protocol

### Try
- [Implementation in Haskell](https://github.com/adjoint-io/bulletproofs)
- [Implementation in Rust](https://github.com/dalek-cryptography/bulletproofs)

### Proof system implementations:
- [Programmable Constraint Systems for Bulletproofs](https://medium.com/interstellar/programmable-constraint-systems-for-bulletproofs-365b9feb92f7)

### Halo

- [Halo: Recursive bullet proof composition](https://www.coindesk.com/you-can-now-prove-a-whole-blockchain-with-one-math-problem-really)

## SNARKs

> SNARK = **S**uccinct **N**on-interactive **AR**guments of **K**nowledge

### Learn

Get started:
- [Introduction to zk-SNARKs with examples](https://media.consensys.net/introduction-to-zksnarks-with-examples-3283b554fc3b)
- [What are zk-SNARKs (Zcash blog)](https://z.cash/technology/zksnarks)
- [BabySNARK- The simplest possible SNARK for NP. You know, for kids!](https://github.com/initc3/babySNARK)

Why and How zk-SNARK Works:

- [Why and How zk-SNARK Works 1: Introduction & the Medium of a Proof](https://medium.com/@imolfar/why-and-how-zk-snark-works-1-introduction-the-medium-of-a-proof-d946e931160)
- [Why and How zk-SNARK Works 2: Proving Knowledge of a Polynomial](https://medium.com/@imolfar/why-and-how-zk-snark-works-2-proving-knowledge-of-a-polynomial-f817760e2805)
- [Why and How zk-SNARK Works 3: Non-interactivity & Distributed Setup](https://medium.com/@imolfar/why-and-how-zk-snark-works-3-non-interactivity-distributed-setup-c0310c0e5d1c)
- [Why and How zk-SNARK Works 4: General-Purpose Computation](https://medium.com/@imolfar/why-and-how-zk-snark-works-4-general-purpose-computation-dcdc8081ee42)
- [Why and How zk-SNARK Works 5: Variable Polynomials](https://medium.com/@imolfar/why-and-how-zk-snark-works-5-variable-polynomials-3b4e06859e30)
- [Why and How zk-SNARK Works 6: Verifiable Computation Protocol
](https://medium.com/@imolfar/why-and-how-zk-snark-works-6-verifiable-computation-protocol-1aa19f95a5cc)
- [Why and How zk-SNARK Works 7: Constraints and Public Inputs](https://medium.com/@imolfar/why-and-how-zk-snark-works-7-constraints-and-public-inputs-e95f6596dd1c)
- [Why and How zk-SNARK Works 8: Zero-Knowledge Computation](https://medium.com/@imolfar/why-and-how-zk-snark-works-8-zero-knowledge-computation-f120339c2c55)

ZkStudyClub:
- [ZkStudyClub Part 1: Polynomial Commitments with Justin Drake](https://www.youtube.com/watch?v=bz16BURH_u8)
- [ZkStudyClub Part 2: Polynomial Commitments with Justin Drake](https://www.youtube.com/watch?v=BfV7HBHXfC0)
- [ZkStudyClub Part 3: Polynomial Commitments with Justin Drake](https://www.youtube.com/watch?v=TbNauD5wgXM)

Electric Coin blog series:
- [Explaining SNARKs Part I: Homomorphic Hidings](https://electriccoin.co/blog/snark-explain/)
- [Explaining SNARKs Part II: Blind Evaluation of Polynomials](https://electriccoin.co/blog/snark-explain2/)
- [Explaining SNARKs Part III: The Knowledge of Coefficient Test and Assumption](https://electriccoin.co/blog/snark-explain3/)
- [Explaining SNARKs Part IV: How to make Blind Evaluation of Polynomials Verifiable](https://electriccoin.co/blog/snark-explain4/)
- [Explaining SNARKs Part V: From Computations to Polynomials](https://electriccoin.co/blog/snark-explain5/)
- [Explaining SNARKs Part VI: The Pinocchio Protocol](https://electriccoin.co/blog/snark-explain6/)
- [Explaining SNARKs Part VII: Pairings of Elliptic Curves](https://electriccoin.co/blog/snark-explain7/)

Vitalik Buterin's blog series on SNARKs:
- [Part 1: Quadratic Arithmetic Programs: from Zero to Hero](https://medium.com/@VitalikButerin/quadratic-arithmetic-programs-from-zero-to-hero-f6d558cea649)
- [Part 2: Exploring Elliptic Curve Pairings](https://medium.com/@VitalikButerin/exploring-elliptic-curve-pairings-c73c1864e627)
- [Part 3: Zk-SNARKs: Under the Hood](https://medium.com/@VitalikButerin/zk-snarks-under-the-hood-b33151a013f6)

Protocol descriptions:
- [zkSNARKs in a Nutshell](https://chriseth.github.io/notes/articles/zksnarks/zksnarks.pdf)
- [Groth16 protocol](https://eprint.iacr.org/2016/260.pdf) (original paper)
- [Zcash Sapling protocol spec](https://github.com/zcash/zips/blob/master/protocol/protocol.pdf) (very useful as detailed cheat-sheet of all cryptography used)

### Try

- [libsnark (C++)](https://github.com/scipr-lab/libsnark)
  - [great tutorial](https://github.com/christianlundkvist/libsnark-tutorial)
- [bellman (rust)](https://github.com/zkcrypto/bellman/)
  - [demo circuit](https://github.com/ebfull/bellman-demo)
- [jsnark (Java, bindings to libsnark)](https://github.com/akosba/jsnark)
- [snarky (Ocaml, from authors of Coda)](https://github.com/o1-labs/snarky)
- [zokrates (toolbox for zkSNARKs on Ethereum)](https://github.com/Zokrates/ZoKrates)
  - [ZoKrates Remix plugin tutorial](https://medium.com/coinmonks/zokrates-zksnarks-on-ethereum-made-easy-8022300f8ba6)
  - [Zero Knowledge Proof Application Demo, with libsnarks, truffle and docker](https://medium.com/hackernoon/zero-knowledge-proof-application-demo-2a457cfc73c1)
- [ethsnarks by HarryR (alternative toolkit for viable zk-SNARKS on Ethereum, Web, Mobile and Desktop)](https://github.com/HarryR/ethsnarks)
- [gnark - library for zero-knowledge proof protocols written in Go](https://github.com/ConsenSys/gnark)
- [circom and snarkjs tutorial](https://github.com/iden3/circom/blob/master/TUTORIAL.md)
  - [Roll-up tutorial using Circom and SnarkJS by Ying Tong](https://github.com/therealyingtong/roll_up_circom_tutorial)

### Scaling the prover

- [DIZK: Java library for distributed zero knowledge proof systems with Apache Spark](https://github.com/scipr-lab/dizk) (see the [research paper](https://eprint.iacr.org/2018/691))
- [SnarkyGPU: distributed GPU based zkSNARKs prover](https://github.com/matterinc/snarkyGPU) (work in progress)

### Multi-Party Ceremony (MPC) for Trusted Setup

- [“Powers of Tau” protocol for scalable generation of structured reference string](https://eprint.iacr.org/2017/1050)
- [Implementation of ZCash MPC Ceremony, Part I: "Powers of Tau"](https://github.com/ebfull/powersoftau)
  - [Archived independent implementation in Go](https://github.com/FiloSottile/powersoftau/)
- [Implementation of ZCash MPC Ceremony, Part I: "Sapling Circuit"](https://github.com/zcash-hackworks/sapling-mpc)

## SNORKs

> SNORK = **S**uccinct **N**on-interactive **O**ecumenical (Universal) a**R**guments of **K**nowledge

SNORKs are SNARKs with universal and updateable trusted setup.

### Sonic

- [Introducing Sonic: A Practical zk-SNARK with a Nearly Trustless Setup](https://www.benthamsgaze.org/2019/02/07/introducing-sonic-a-practical-zk-snark-with-a-nearly-trustless-setup/)
- [Sonic: Zero-Knowledge SNARKs from Linear-Size Universal and Updateable Structured Reference Strings](https://eprint.iacr.org/2019/099)
- [Sonic MPC implementation by Matter Labs](https://github.com/matter-labs/alpha_line)

### PLONK

(This is a recent development. Contributions are welcome!)

- [Awesome PLONK](https://github.com/Fluidex/awesome-plonk): A curated list of awesome things related to plonk proof system.
- [Understanding PLONK by Vitalik Buterin](https://vitalik.ca/general/2019/09/22/plonk.html)
- [Ignition: Trusted Setup MPC Ceremony for PLONK](https://medium.com/aztec-protocol/aztec-announcing-our-ignition-ceremony-757850264cfe)

### Marlin

(This is a recent development. Contributions are welcome!)

- [A Marlin is One of the Fastest SNARKs in the Ocean](https://www.benthamsgaze.org/2019/09/19/a-marlin-is-one-of-the-fastest-snarks-in-the-ocean/)
- [Marlin: Preprocessing zkSNARKs with Universal and Updatable SRS](https://eprint.iacr.org/2019/1047.pdf)

## STARKS

> STARK = **S**uccinct (**S**calable) **T**ransparent **AR**guments of **K**nowledge

STARKs are SNARKs without Trusted Setup.

### Learn

Get started:
- [STARK @ Home {video playlist}](https://www.youtube.com/playlist?list=PLcIyXLwiPilUFGw7r2uyWerOkbx4GFMXq)

### FRI-STARKs

Introduction:
- [Transparent Succinct Arguments by Alessandro Chiesa (Oct 2018)](https://gist.github.com/Haseeb-Qureshi/f552fdbbb649ed4bbfeb681beb4091e1)
- [State of the STARK by Eli Ben-Sasson (Devcon IV, Oct 2018)](https://drive.google.com/file/d/1Osa0MXu-04dfwn1YOSgN6CXOgWnsp-Tu/view) ([video](https://www.youtube.com/watch?v=1KSwVIZ82hs))
- [Introduction to ZK-STARKs by remco@0x.org](https://hackmd.io/s/rJHYnQ3Z4)

Vitalik Buterin's blog series on STARKs:
- [Part I: Proofs with Polynomials](https://vitalik.ca/general/2017/11/09/starks_part_1.html)
- [Part II: Thank Goodness It's FRI-day](https://vitalik.ca/general/2017/11/22/starks_part_2.html)
- [Part III: Into the Weeds](https://vitalik.ca/general/2018/07/21/starks_part_3.html)

Academic resources:
- [The STARK paper](https://eprint.iacr.org/2018/046.pdf)
- [libstark implemenation](https://github.com/elibensasson/libSTARK)

More resources available at [starkware.co](https://www.starkware.co)

### SuperSonic

(This is a recent development. Contributions are welcome!)

- [Transparent SNARKs from DARK Compilers (Dec 2019)](https://eprint.iacr.org/2019/1229.pdf)
- [Introducing Sonic: A Practical zk-SNARK with a Nearly Trustless Setup](https://www.benthamsgaze.org/2019/02/07/introducing-sonic-a-practical-zk-snark-with-a-nearly-trustless-setup/)

### Fractal

(This is a recent development. Contributions are welcome!)

- [Fractal: Post-Quantum and Transparent Recursive Proofs from Holography](https://eprint.iacr.org/2019/1076)

## Social media

Stay tuned!

- [Awesome zero knowledge twitter list](https://twitter.com/gluk64/lists/awesome-zkp)
- [Zero-knowledge podcast](https://www.zeroknowledge.fm)
- [ZKProof, an academic and industry initiative for standardizing Zero Knowledge Proofs](https://zkproof.org/)
