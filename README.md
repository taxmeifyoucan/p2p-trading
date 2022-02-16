# Peer-to-peer (crypto) trading networks

This repository sums up what I learned by single-handedly running a web of trust P2P group for asset exchange. 

## Motivation

Bitcoin (ehm p2p electronic cash or something like that?) and cryptocurrencies are designed for P2P exchange. However, the vast majority of users today lean towards third-party services. CEXs are [penetrating](https://en.wikipedia.org/wiki/Crypto.com_Arena) mainstream and people find it a default way of acquaring crypto assets, completely leaving behind p2p nature of these technologies. Each of these exchanges is a regulated business tightly connected to the fiat world. Normalization of KYC already occurred, and people find it ok to submit their personal data to acquire crypto. Ineffective KYC/AML practices are destroying the benefits of permissionless and private transacting.


P2P trading allows for the avoidance of third parties while maintaining the censorship-resistant nature of cryptoanarchistic tools.

![Bitcoin a klid](https://user-images.githubusercontent.com/61149543/154226607-d56b75f3-624a-4230-b86a-ce3cdcedab64.png)

Our historical experience teaches us about the benefits of p2p trading. Ask central/eastern Europeans about the veksel or fartsovka. 

## Current solutions

Platforms for P2P marketplaces already exist. Why reinvent the wheel? 

Indeed, there are many solutions, I recommend you check first:

* Bisq
* HodlHodl
* Paxful
* LocalCoinSwap
* Bitzlato
* LocalCryptos
* Binance P2P
* Or agregators like Monetory

These marketplaces enable you to buy crypto from other users somewhat directly. They aim to be global and use escrow or multisig with a third-party arbiter to assure the security of trading. This adds significant overhead for smaller traders and newbies. In some cases, you need crypto collateral to lock within multisig, which blocks new users. It is still easier for people to use KYC CEXs than these p2p platforms.

## Web of trust groups

Let's make it easier and more local by using the web of trust. Any web of trust experience you have, such as from using PGP, can be extended in a variety of ways to cover p2p trading.

Each member of the group must have a certain level of trust. This trust can be gained by recommendations from other group members or a trusted persona in the community. The guarantee has to be clear and directly confirm that he can guarantee that the member is a trusted person and is not going to cheat or leak information. 

A new member must understand the group's [rules](/rules.md), verbally agree with them, and respect them. From my experience, around 30% of people won't pass the filter.

In this simple setup, the burden of verifying the integrity, intentions of each member is on the administrator of the group. Trust in the trading within the group is largely based on the reputation of the admin. 

Trust within this group is still subjective to each member. It is recommended to start with smaller trading amounts and incrementally gain more trust. 

### Discussions

People like to talk. In addition to the trading group, create another one that is intended for discussion, questions. If somebody has a question about trading, technical problems, etc, it should be separated from the trading group which accommodates only offers. Preventing spam is not an easy job, and especially with larger groups, notification to hundreds of people is unnecessary. 

## Technologies

### Platform

Groups like this are preferably sitting on an E2E encrypted chat platform which enables larger group conversations. Signal would be recommended based  on its network effect and my experience, however keep in mind it is sacrificing a level of privacy. 

Important Signal features to consider in secure p2p trading:

* E2E encryption
  * no brainer, maybe if it is some self-hosted platform I would consider it not needed but pls encrypt everything) 
* Disappearing messages
  * Turn them on, 2 days are the sweet spot from our experience 
* Perfect forward secrecy
  * New members have no idea about previous trades
* Groups work well 
  * With new updates Signal enabled larger group conversation with admin management and invite links

There are also important disadvantages to consider:
* Leaking your phone number, anonymity decreased
  * Someone may consider it better for keeping track of the web of trust
* Any or limited support for bots
* Not pinned messages
* No option to edit a message or delete after the period set by Signal client

Anonymous and encrypted platforms like Threema, Wickr, Matrix, Rocketchat are also homes to groups like this. The choice depends on what your community uses the most, go with the network effect. 

### Payments

#### Crypto 

The original purpose of the group I am basing my experience on was to boost the adoption of Bitcoin Lightning. Lightning enables small payments with a low fee with instant finality. This prevents double-spending attacks possible with RBF and without waiting for confirmations, it is fast and ideal for cash deals. Trading smaller amounts with lower trust for DCA is also ideal with LN. Preimage in LN gives users proof of payment in case of disputes. The group was supposed to teach people about the possibilities of LN and help with LN<>onchain swaps, bootstrapping LN liquidity. 

LN is the default payment method preferred over onchain or altcoins. This is because fast and feeless experience enables LN to become a neutral asset that can be easily swapped to anything. Do you have BTC onchain, Monero, or ETH instead of LN? Just swap it (via a third-party, Boltz, Fixedfloat..) at the moment of payment, it will still cost you the same one onchain tx! Another layer of anonymity is added as the recipient doesn't see who sent the payment in LN.

Onchain payments are also popular and necessary for bigger amounts, but lightning is required. Other groups inspired by this one are enabling either all crypto or focusing on a specific asset, e.g. Monero group, stable coins group. 

#### Fiat

The good old dirty fiat. Somebody needs to touch it in the end. The physical version of Bitcoin, paper cash, enables fast, feeless, and anonymous payments. This is ideal especially for local groups within a city, county, or smaller country. 

The LN group covers the whole Czechoslovakia and further. Cash is still popular, mostly in the big cities, but the most commonly used fiat payment methods are banks or fintech products with instant payments, e.g. Revolut. It's fast and comfortable for people, as they mostly have some sort of bank account. For bankless people, cash is not the only option-coupons, direct payment for products are alternatives. E.g. pay my phone bill and I send you sats.

(Instant) bank transfers fit most of the users and keep a certain degree of privacy as bank doesn't know that payments are intended for crypto. Make sure the transaction note doesn't mention anything crypto-related! Smaller transactions from random people hopefully stay under the radar and don't cause any questions from the bank. With a more cashless society, this becomes unavoidable.

# Group rules

Make sure each member understands the rules. This should include verifying he has a crypto wallet and knows how to use it. Check out an [example of the rules for the LN p2p group](/rules.md).  

# Scaling and improvement ideas

As you can tell at this point, this approach is not scalable at all. All the burden stays with the admin(s) who is a SPOF. 

Keeping track of the web of trust (who guarantees who) is not automated and not transparent (also a privacy consideration). All of this is handled by an admin who needs to be trusted and active. It really gets overwhelming and there is no compensation for the admin so the motivation to verify new members (the biggest chunk of work) is lost.

Certain things could be automated via chatbots. Signal doesn't enable bots, but I built one using a script with signal-cli. Bots could be used to talk to members who want to join, share the rules, and keep track of the web of trust. It could also work as an intermediary for posting offers from/to groups or between different trading groups with various trust levels.

Multiple groups can be created for more trusted and less trusted members. With successful trades, members can move to a group with higher trust, e.g. intended for higher amounts. 

This would require keeping track of successful trades, which breaks privacy and is not entirely possible without some sort of reporting system via form or bot. 

Proof of lightning is another idea for filtering member requests. Similar to Telegram's lntxbot, the bot would require a small LN payment to access the group. Only after this, is the member contacted by the admin. Or can access a lower-level trust group. 

Lightning stake could be also used for incentivizing web of trust or compensating admins, arbitors. This requires a higher LN deposit when accessing the group. Part of the deposit is a fee for admin and the other part stays as an escrow stake. The deposit would be lost if party is cheats to the cheated party. However, arbitrage, in this case, would be far big management overhead.

Decentralizing governance and arbitrage to trusted members can be done via a simple DAO. Automatization of the web of trust via DAO would let members vote on new members and arbiters, delegates instead of admin. Stuff gets complicated at this point as there is no practical implementation so far.

All of this is pushing towards specialized software for trusted p2p trading rather than messaging groups. Specialized software, FOSS solution which would enable creating networks of traders with different levels of trust alongside channels for verification, discussion. Automation and cryptographic verification in these processes are the only things that would make this scale. DAO UI could be part of it as well. Also, automated hedging for trading within the app would be cool - there you have a business model. Liquidity is another issue discussed below. 

Keeping anonymity and trust at the same time is another challenge. Zero-knowledge proof of reputation could also be implemented in specialized app. 

# Obsereved phenomenas

You can see the market at work as people are asking for fees, the bigger price spread when it significantly moves up or down. People are only selling with premiums at the lowest dips. Generally, this is caused by limited liquidity in the group. Some clever group members are using hedging to offer liquidity even at the lowest dips. A derivative market or decentralized loan on Ethereum enables anybody to make a profit by selling crypto with a small fee at any price level. [Vekslosh](https://github.com/Kixunil/vekslosh/) or other software which makes it easy for end-users to bring even more liquidity to the market. 

Surprisingly, people are generally friendly, cooperative, and even make friendships. People are making contacts and exchanging even goods, food, building a little parallel economy. It seems like the community is not that toxic if they are not on the bluebird app. 

Check also [p2p exchange protocol repo](https://gitlab.com/sovereign-individuals/p2p-exchange-protocol) for a similar initiative from the community. A bunch of other groups inspired by LN veksel emerged, mostly local groups within the cities. But there is never enough of them. With all this knowledge, go ahead and create your own! 

![LN Bisq](https://user-images.githubusercontent.com/61149543/154251311-0c1fbd36-2c48-4673-8732-ab172fad4dc3.png)
