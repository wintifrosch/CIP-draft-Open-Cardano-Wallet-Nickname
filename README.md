---
CIP: tbd
Title: OCAWAN - Open Cardano Wallet Nicknames
Authors: wintifrosch <wintifrosch@gmx.ch>
Comments-URI: Issues Section
Status: Pre-Draft
Type: Process
Created: 2022-10-15
License: CC-BY-4.0
---

# Open Cardano Wallet Nickname


## Abstract
<!-- A short (~200 word) description of the technical issue being addressed. -->

We introduce an open standard to link a cardano wallet address to a nickname.

Nicknames are publicly available files on IPFS.
Each registration contains proof that the name is actually owned by the registrant.   
The blockchain is only used to register a nickname via a freely available smart contract. 

Nickname registrations must be renewed every year. 

No existing protocols must be modified to realize this translation layer.  
To kickstart, at least one services must exist to proof nickname ownership claims. 


## Work in Progress

<!-- 

-->
Before this CIP can be submitted, technical solutions for the following aspects shall be discussed in the issues section:
1. [Phishing attack prevention](https://github.com/wintifrosch/OCAWAN__Open_Cardano_Wallet_Nickname__predraft/issues/3)  
   Any registrar MUST verify (and guarantee to all future users of a nickname) the legitimacy of a nickname. On what basis can we trust a registrar? How can we ensure that even trusted registrars will add one single fraudulent record?
2. [On-chain storage space](https://github.com/wintifrosch/OCAWAN__Open_Cardano_Wallet_Nickname__predraft/issues/4)  
   Is it possible (and reasonable) to store a nickname data record on-chain, contained in the transaction metadata?
3. [Off-chain records](https://github.com/wintifrosch/OCAWAN__Open_Cardano_Wallet_Nickname__predraft/issues/5)   
   Off-chain storage has no limitation of the storage space per nickname. This would allow registrations in bulk, which would lower the cost per nickname. Is this to be considered, if yes: as an alternative to single record on chain storage? 
4. [Trust issues](https://github.com/wintifrosch/OCAWAN__Open_Cardano_Wallet_Nickname__predraft/issues/7)
   Where is cryptography required?

## Motivation 
<!-- The motivation is critical for CIPs that want to change the Cardano protocol. It should clearly explain why the existing protocol is inadequate to address the problem that the CIP solves. -->

Wallet addresses are not made for humans - they were never meant for humans, but there is no alternative as of yet. This CIP is intended to remedy this shortcoming.  
Since wallet addresses have no semantic, it's hard for humans to distinguish two adresses or to ensure that any address points to the intended wallet. 
It would be helpful for humans to use a nickname instead - a nickname that can be associated with the owner of the wallet, a nickname that is already established and shared. 

The solution shall be implemented in «wallet apps»[^WalletApp].   
From a users perspective, a good and broadly adapted nickname solution would be perceived as _a feature of the Cadrano Blockchain_, which brings a competitive advantage (even a [USP](https://en.wikipedia.org/wiki/Unique_selling_proposition)?) and improves adoption rate of the Cardano Blockchain. The implementation might therefore be supported by the Cardano Foundation and/or receive Project Catalyst support. 


## Features

Any «wallet app» achieves the following added values for end users by implementing this standard:
* Users are able to associate their nickname to their wallet, upon creating a wallet or afterwards. 
* To send assets from a wallet, their peers may use the nickname instead of the legacy wallet address. 
* In every context, the application displays the nickname for any wallet (if registered).  
* The user can provide a list of strings and filter / flag those nicknames with a valid Open Cardano Wallet Nickname (e.g. by granting read access to the addressbook).

This solution compromises privacy. It should be made abundantly clear to all users registering a nickname.

## Specification 
<!-- The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Cardano platforms. -->

<!-- 

It is relatively easy to create a smart contract to build such a register. The hard part is to build an open distributed system that prevents phishing attacks by providing _verifiable ownersip claims_: You always have to trust a third party to have verified this claim. Which third parties do you trust? How do you identify non-trustworthy third parties, and who can ban them?

For e-mail addresses, a S/MIME certificate solves this problem, but they are only used by a few (and they are based on a trusted registrar). Most online services with user accounts have a much simpler verification method by sending a verfification code to the mail address. Over an oAuth mechanism, some of them provide limited access to the verified Mail adresses (e.g. «Sign in with google»). But you won't share the oAuth secret in this verification system.  
There could be a system to which the user has set up a «login with google» and thus granted access to his account mail address. This system can now provide a zero knowledge proof to any third party, that the system can verify if a given adress is correct. (A possible ZKP could be: in four iterations, the proofing system must identify one out of ten md5 hashes of the mail address, created by the third party using a random secret provided by the proofing system.) 

The task is much easier for systems where users may publish data (social media apps, dropbox, ...) 

### Registering
 
### Claim verification


new capter structure proposal 2022-10-17

1. Wallet App Use Cases
2. Indexer usecases
  - crawler
  - validator
  - publisher
2. validation
  - nickname classes
  - nickname ownership verification
  - nickname class evolution
  
1. data structures
  - json format
  - CRUD transactions
  - nickname classes
  - on-chain
  - off-chain (for bulk publications)
  - index data format




--> 
### 1. Registration
The open standard defines how a nickname can be registered. The registration contains a standardised description of how the authenticity of the nickname has been checked. The verification must be renewed periodically (1 to 3 Years + 1 month).
The «standardized description» refers to a defined catalogue of nickname sources and corresponding verification methods, like a DNS TXT record.[^DNS]  

_For free:_ The basic registration of a nickname should be automated, free of charge (or very inexpensive, covering transaction fees) in order to facilitate a large adoption rate among ada holders. Ideally, the nickname can optionally be provided when creating a wallet and can be changed later very easily within the wallet app. 

_verified nicknames:_ The basic registration may be upgraded upon request via additional procedures. Users recognise those «comprehensively verified confirmations» by a blue badge, similar to «twitter verified». The documents required for the verification can be sighted or are referenced in the confirmation document.

IOHK provides a reference implementation to establish the standard and set a benchmark in terms of performance and cost.  
IOHK also provides an API through which newly registered nicknames can be reported so that they appear in the index as soon as possible. The new entries reported there are publicly viewable. Each registration is validated before it appears in the public list.  

Process:
1. The owner of a wallet deposits his wallet address and any handle with a registrar of his choice.
2. The registrar ensures, that the nickname is available. 
3. The registrar verifies that the owner actually owns the wallet.
4. If the handle meets the syntactic requirements for mail addresses, mobile numbers, Twitter handles, Domain Names (among other strings, tbd), the registrar ensures that the owner actually owns this nickname.
5. The registrar's confirmation is published.[^NFT]


### 2. De-registration 
Revoking a nickname is free of charge. (The fee to register a name, if any, for creating a handle also covers the cost of revoking a handle). 
If the periodic confirmation is not renewed, the verification expires and the nickname is removed.


### 3. Lookup
IOHK provides a free public API through which the registered wallet address can be requested for a given string (and vice versa, incl. bulk requests (<200 nicknames per request), rate-limited (< 5 API-requests per API-Key), API available in every stake pool relay (opt-out). 

The open standard and the publication of the proofs on the internet allows anyone to realise an alternative/better lookup service. 


### 4. Usability Style Guide
_Moderated by IOHK:_ Together with the community, IOHK moderates a usability style guide for providers of solutions that support the standard. The style guide ensures that the functions work and look similar in different systems. 

_Word mark:_ A word mark is established to designate this nickname standard and to distinguish to alternatives like adahandle.com. (Camelcase «OCaWaN» or «OCAWA nicknames»?)

_Icon:_  A figurative mark is established to represent an ADA handle, e.g. a symbolised dark blue or white Cardano star (fewer rays and dots for use in text next to characters?). <img width="22" alt="image" src="https://user-images.githubusercontent.com/3762931/196009522-6230d30c-2a1c-48cf-b054-7b5fa0b06a08.png"> This icon says: «I am a cardano wallet nickname. You may click me to send money to my wallet adress». This icon may appear wherever a CIP-13 URI like ``web+cardano:wintifrosch`` appears. (The icon may be used for any CIP 13 URI, with or without nickname) 
- For example, it is possible that operating system manufacturers (Android, iOS/MacOS, Windows) mark those entries in the address books of their users for which an Ada handle exists, or an extension might add a cardano wallet link to any contact card where an alias is found.  
- Wallet providers could check for which contacts in the users contact list a wallet is available and can list them for the user (similar to how a chat app lists those contacts that can be addressed directly).
- On a Homepage, this icon to represent the ADA Handle may be placed beside Twitter, Instagram, etc... icons.

_Cardano URI scheme:_ A protocol is defined on how the nickname can be represented as an URI . Each (wallet) app can register for this URI format in the operating system and translate the nickname to the wallet adress. (cf. [CIP-0013](https://cips.cardano.org/cips/cip13/#paymenturiqueries))


### 5. Standard Evolvement Procedure  
The Standard establishes procedures to share, elaborate and publish future updates to the standard.


## Rationale ((fragment; keywords only))
<!-- The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work. The rationale should provide evidence of consensus within the community and discuss important objections or concerns raised during discussion. -->

_Proof of ownership:_ Whether a nickname actually designates the correct account can be checked at any time because a certificate for the handle must be stored in the wallet.[^NFT]

_Adoption rate:_ Market penetration is essential. A solution to this problem is only successful if it is used by as many wallet owners as possible and supported by as many wallet manufacturers as possible. This solution should therefore be specified and operated by IOHK or by the Cardano Foundation. 
- ease of use
- low costs / no business model
- open standard / Alternate registries must be certified by IOHK

_universal standard:_ A universal solution as part of the standard prevents alternative solutions from establishing themselves. This strengthens the Cardano brand, because all wallets work with the same "OCAWA nickname" standard. And it prevents users from being stranded because a solution is no longer operated. And then alternatives spring up. 

_no false claims:_
Since every nickname must be verifiable by design, alle validated nicknames are -- well: _valid_ [^ahadandle-1].  
Since all claims must be confirme / renewed periodically, the nicknames become invalid and are available again for everyone that can proof to own this nickname. This is a very common scenario in the real world, e.g. for mobile numbers. [^adahandle-2]

_alternate nickname classes:_ The standard should support the creation of alternative nickname classes with their own verification methods. like this, all adahandle.com nicknames could be integrated into the standard. Alternative verification methods not provided by IOHK may be created be third parties.  

_open directory (open API):_ All valid addresses (and all revoked ones) should be accessible and trustworthy for all.
Since the basic data is available to all, any market participants can implement alternative / better / cheaper solutions.

_abuse prevention:_ The creation and revocation of a handle must be simple and inexpensive. The misuse of handles must be prevented.   (identity theft)
- Certification (blue badge)
- Warning for alternative addresses with similar spelling? Character set restriction
- No emojis in handles (reduced character set to reduce equally confusable characters or to place fake ‹verified badges›?)
- dispute procedure

_privacy concerns:_
The fact that there's no way to connect a cardano wallet address to a person is a huge feature, not a flaw.
The need for privacy is gradual, and it is always a compromise between costs and benefits.
OCAWAN is a solution for those people willingly to share at least one of their wallet addresses.

If OCAWAN becomes a reality, it should be made abundantly clear that this solution compromises privacy. OCAWAN is and will always be opt-in.
(more [here](https://forum.cardano.org/t/cip-human-readable-token-alternative-for-wallet-addresses/109027/27?u=wintifrosch))

<!-- 
more here: 
The fact that there's no way to connect a cardano wallet address to a person is a huge feature, not a flaw.

OCAWAN is a solution for those people willingly to share at least one of their wallet addresses. Because you can have an indefinite number of addresses per wallet, they only share kind of a sub ledger, not their whole wallet.  

> That is a massive RED FLAG. [...] Think of the AI algorithms of the future.

I share your stance. BTW I'm looking for methods that _everyone_ can verify that my nicknames are linked to a Cardano wallet address. It's not essential whether google is the system providing this proof. 

Suppose we have two versions of the Cardano blockchain, one with nicknames and the other one without. The first is proud to show the banner «we protect your privacy!» and the other one «reviews confirm: we have the best usability!». Which one will be the popular one?   

If OCAWAN becomes a reality, it should be made abundantly clear that this solution compromises privacy. OCAWAN is and will always be opt-in. You and me are not in the target group.

The need for privacy is gradual, and it is always a compromise between costs and benefits. If you were a privacy maximist, you might even avoid Cardano.


-->

_built for the eternity_

#### 1:1?
to be discussed: 
- Should it be possible to assign several nicknames to a wallet (e.g. an email address, a Twitter handle and a mobile number)? - Probably: yes.
- Should it be possible to assign several wallets to one nickname? -- Probably: no. Implementation and Usability will be more complex. Owners may create another nickname for another wallet.


#### additional metadata per wallet:_
Should it be possible to store additional data, e.g. an icon, a public and a private full-text description of the account, ...?

_strategic brand value:_
This «alias meccano» is a fundamental building block for the Cardano Blockchain usability, and so it’s tied very much to the Cardano brand. That’s why I think IOHK should be the issuer of the smart contract (if that’s part of the solution) and IOHK should provide an index.

_Alterntive solutions:_
There are solutions implemented and in use, but they only work as long as the owning companies provides this service. This CIP proposes an open solution instead. Existing solutions will become superfluous. They can add their names to the index though. 

### Related CIPs
- [Address Resolution and Validation through DNS and HTTP](https://github.com/cardano-foundation/CIPs/pull/319) (by HeptaSean): aims to link wallets to a domain. Not suitable for everyone. A solution for one-man businesses or small and medium sized companies, but not for everyday people. 
- [CIP 13 - Cardano URI Scheme](https://cips.cardano.org/cips/cip13/#paymenturiqueries): If OCaWa nicknames CIP will be accepted and realized, the URI scheme from CIP-0013 should be extended to support a ocawa-nickname as a valid ``cardanoaddress`` 


## Backwards compatibility
<!-- All CIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The CIP must explain how the author proposes to deal with these incompatibilities. -->
((empty))

## Path to Active
<!-- A reference implementation, observable metrics or anything showing the acceptance of the proposal in the community. It must be completed before any CIP is given status "Active", but it need not be completed before the CIP is accepted. It is better to finish the specification and rationale first and reach consensus on it before writing any code. -->
((empty))


---------
[^WalletApp]: For readability reasons, the term «wallet app» is used in this CIP for every application that provides a user interface to interact with cardano wallets. 
[^NFT]: The CIP discussions shall elaborate the best way to implement a decentralized publication system and a directory. Maybe the registrar just signes a simple JSON like the one above, and puts an NFT in the owners wallet. 
[^DNS]: a domain name, as [described in the CIP proposal by HeptaSean](https://github.com/cardano-foundation/CIPs/pull/319) is just another class of established handles. The proposed verification method may be one of the standardized verification methods of OCAWAN.
[^ahadandle-1]:  That's not true for [adahandle.com](adahandle.com), where everybody can use every nickname, as long this name is still available. You can create handles for as many phishing victims as you want, as long as you pay adahandle for it.
[^adahandle-2]: That's not true for [adahandle.com](adahandle.com), where every handle is gone forever. Adahandle will die, since it's own popularity will turn into a death sentence. 
