# SherpaX-BTC

## Comparison of existing BTC cross-chain solutions
|  Project | Features                                            | Defects                                   |
| -------- | ----------------------------------------------------| ----------------------------------------- |
| ChainX   | BTC multisig custody + light node cross-chain.      | BTC multisig custody has limitations (for example, up to 15 re-signatures, huge exchange fees, custodians only have the burden of reputation and no financial burden). |
| Interlay | BTC cross-chain can be achieved in the form of over-collateralization of gaming assets. | The same defects as other defi logics (risk liquidation caused by currency price fluctuations, and limited BTC cross-chain assets caused by over-collateralization). |
| Ethereum WBTC | There are several agencies that guarantee a federal-like cross-chain. | Too much centralization, there is a risk of centralization. |
| RenBTC        | Distributed key + all verification nodes of the network jointly guarantee the custody of BTC. | The distributed key calculation of a single private key needs to find a trusted execution environment that recovers the key security. In a responsible communication implementation environment, it is easy to leak the private key. |

## Background
After BTC taproot is upgraded, it brings two major technologies: MAST contract + aggregate signature.
It brings a new safe technical solution to the distributed privacy and safe computing threshold signature.
It also brings a decentralized (multi-signature escrow node can be enough) cross-chain solution to BTC.

## Technical Summary
Our latest cross-chain solution for the ChainX network combines the advantages of the above solutions to launch a BTC cross-chain approach that is equally decentralized as the POS consensus.

The plan is as follows:

From the BTC network cross-chain to the ChainX network, BTC adopts light node cross-chain. Originally, this cross-chain model is the most decentralized and safest.                

XBTC crosses back from the ChainX network to the BTC network. We adopt micro-collateral game theory + verification node consensus layer custody integration + Taproot threshold algorithm integration to achieve the same decentralized cross-chain as the POS network.
               
 - Among them, Taproot's threshold algorithm: This is the implementation of our application for this grant. The use of aggregate signatures combined with Merkel tree contracts to implement threshold wallets, of course, requires the cooperation of our ComingChat distributed privacy network.
 - The verification node consensus integration: bind the custodian of the BTC and the verification node of the POS network one by one, so that we can achieve the same decentralization of our BTC cross-chain and the POS network.
 - The micro-collateral game theory: There is no need to over-collateralize like Interlay, only a small amount of collateral much smaller than the custodial BTC quota is needed to punish some nodes for laziness or collusion. This can support enough BTC to cross-chain to the ChainX network.

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

