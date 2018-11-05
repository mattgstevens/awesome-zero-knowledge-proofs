# awesome zero knowledge proofs

- aka ZK-systems
- aka spooky moon math
- aka dont show your secrets on a public blockchain

A collection of videos, reading materials and tools for learning all about the ZK side of crypto.

---

## SNARKs

(Succinct non-interactive argument of knowledge)

Fast facts:

- used in Zcash
- available in Ethereum as pre-compiled smart contracts
- has a trusted setup phase, making a trusted party needed (OR having to deal with secure multi part computation (sMPC))
- very fast verification, very small proof

### Videos

- [Coda Protocol: Using ZK-SNARKs for a Constant-size Blockchain :: Izaak Meckler at Zcon0 (June 2018)](https://www.youtube.com/watch?v=qCVACpgQSjo)

### Reading

### Tools

- [ZoKrates](https://github.com/Zokrates/ZoKrates)
- [DIZK](https://github.com/scipr-lab/dizk)

---

## STARKs

(Succinct transparent argument of knowledge)

Fast facts:

- newer, ["hotter"](https://twitter.com/avsa/status/1057584874859753472?s=21) cousin of SNARKs
  - newer also means lots of research actively happening during the "warm up phase" for this technique
- does not require a trusted setup phase
- proof length is much longer than SNARK

### Videos

- [Zero-Knowledge Proof Protocol :: Eli Ben-Sasson at Web3 Summit (October 2018)](https://www.youtube.com/watch?v=1KSwVIZ82hs)
- [STARK Arithmetization :: Eli Ben Sasson at Technion Cyber and Computer Security Summer School (September 2017)](https://www.youtube.com/watch?v=9VuZvdxFZQo)
- [STARK Low Degree Testing :: Eli Ben Sasson at Technion Cyber and Computer Security Summer School (September 2017)](https://www.youtube.com/watch?v=L7tZeO8ihcQ)

### Reading

### Tools

---

## Bulletproofs

Fast facts:

- used in Monero
- great proof legth
- verification time

### Videos

- [Diving Into Bolt; A Privacy-Preserving Layer Two Approach :: J. Ayo Akinyele at Zcon0 (June 2018)](https://www.youtube.com/watch?v=z2l5NqJ6sOI)

### Reading

- [Monero Compatible Bulletproofs (December 2017)](https://getmonero.org/2017/12/07/Monero-Compatible-Bulletproofs.html)

### Tools

---

## General

There are other proof systems, and some general Mathematics / ideas / standards that make ZK proofs work in theory and in application.

### Videos

- [Introduction zk SNARKs STARKs :: Eli Ben Sasson at Technion Cyber and Computer Security Summer School (September 2017)](https://www.youtube.com/watch?v=VUN35BC11Qw)

### Reading

- [Initiative for the standardization of usage of proofs](https://zkproof.org/index.html)

## SNARK vs STARK vs Bulletproof comparisson

(Note: summary from the talk "Zero-Knowledge Proof Protocol :: Eli Ben-Sasson at Web3 Summit (October 2018)")

- there are many others proofs now, and more will come in the future, but these three are being used in blockchains already
- STARK prover will be quasi linear to naive computation (naive as in no zero knowledge aspects)
- SNARK is similar, but also has setup which is also scaling linear to the computation & prover time
  - needs trust, and larger keys as the computation becomes larger
- Recursive SNARK (Coda) does not have this drawback of large keys, as the setup is scoped smaller due to epochs
  - break the computation into a sequence of epochs
  - only need to create a key for one epoch
  - still have trusted setup
  - proving time is larger
- Bulletproofs have a great proof length
  - however the verification time is also super linear along with computation and proving time
  - not so good for scalability, as there is no savings for the verifiers to process
- all are using pederson hashes
  - Starkware
  - Sapling release for Zcash
  - Bulletproofs in Monero

---

### STARK Scalability

- 1 TX -> 500kb to 80kb (Consensys 2017) to 45kb now (October 2018)
  - yet to identify lower bound, more room for improvement!
- 10k TX -> 190kb to 135kb
  - 3x greater size even though 10.000 factor increase in payload

---

### SNARK Scalability

- 1 TX -> 200 byte (with a 50MB key to prove)
- 10k TX -> 200 byte (with a 500GB key to prove)

---

### Bulletproof Scalability

- 1 TX -> 1.5kb
- 10k TX -> 2.5kb
  - but the verification time is scaling linear with proving time
