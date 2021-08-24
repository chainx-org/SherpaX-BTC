# SherpaX-BTC

## Background
After BTC taproot is upgraded, it brings two major technologies: MAST contract + aggregate signature.
It brings a new safe technical solution to the distributed privacy and safe computing threshold signature.
It also brings a decentralized (multi-signature escrow node can be enough) cross-chain solution to BTC.

## Technical Summary
- Threshold signature wallet: Trusted environment based on distributed privacy and secure multi-party computing,
Implement aggregate signature algorithm.
- Mechanism of Trusted Custodian Based on Game Theory.

## [Threshold signature wallet](https://github.com/coming-chat/Grants-Program/blob/master/applications/threshold_signature.md)
ComingChat uses its own private communication network and taproot's technology to realize a threshold signature wallet. 
For details, please check [the document of ComingChat](https://github.com/coming-chat/Grants-Program/blob/master/applications/threshold_signature.md)

## Mechanism of Trusted Custodian Based on Game Theory
Using tokens (ksm, kar) available on the existing network as the base currency collateral, combined with reasonable and useful game theory, the collateral token competition is certified as a BTC threshold signature custodian, and the custodian can profit from KSX.

## Example
A, B, and C are campaigning as custodians, and a certain amount (ksx, kar, ksm, usdt) must be mortgaged as collateral. As a custodian, KSX can be used as a return of income.
A, B, and C will generate two escrow addresses at the same time, one of which is the BTC network and the other is the SherpaX network.
These two escrow addresses correspond one-to-one and come from the same private key, but the encryption curve is different, one is ecdsa and the other is 25519, but both support Schnower's signature algorithm.
``

              root 
              /   \
            branch BC(3)
            /    \
         AB(1)   AC(2)
         
 ``
 
Merkel tree generated in combination with aggregated signatures,Among them AB, AC, BC are the aggregate signature public keys of both.

There are three possibilities for two-thirds of a three-person trust. Each round of BTC cross-chain signature operations between (1), (2), and (3) are all competitive. In the case of a game, you can give With a certain reward every time you sign. If there is a combination that does not generate a signature for a certain period of time, we believe that the address may be lost or cheated. The trust will be re-elected to repeat the above logic.

Of course, our real environment will not only have three trustees. Our trustees can approach infinity, at least equivalent to the number of KSM verification nodes. It is even possible to bind the validator node of the Kusama network to give priority as a trustee. Overall, we need n trustees and m signatures each time, 0 <m <n and m/n is close to 2/3.

The detailed BTC decentralized cross-chain solution will be published in the github warehouse soon.

