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

We introduce an open standard to link a cardano wallet adresses to a nickname.

Any application with a user interface to a Cardano wallet implementing this standard achieves the following added values for end users:
* Users are able to associate the nickname to a wallet, when creating a wallet or afterwards. 
* To send assets from a wallet, users may use the nickname instead of the wallet address. 
* In every context the application displays the nickname for any wallet with a defined nickname.  
* The user can provide a list of aliases (e.g. his smartphone addressbook) and filter / flag those nicknames with a valid Open Cardano Wallet Nickname.

No existing protocols must be modified to realize this translation layer.


## Work in Progress
Before this CIP can be submitted, technical solutions for the following aspects shall be discussed:
1. _Phishing attack prevention:_ Any registrar MUST verify (and guarantee to all future users of a nickname) the legitimacy of a nickname. On what basis can we trust a registrar? 
2. _On-chain storage space:_ Is it possible (and reasonable) to store a nickname data record on-chain, contained in the transaction metadata?
3. _Off-chain records:_ Off-chain storage has no limitation of the storage space per nickname. This would allow registrations in bulk, which would lower the cost per nickname. Is this to be considered, if yes: as an alternative to single record on chain storage? 


## Motivation 
<!-- The motivation is critical for CIPs that want to change the Cardano protocol. It should clearly explain why the existing protocol is inadequate to address the problem that the CIP solves. -->

Wallet addresses are not made for humans - they were never meant for humans, but there is no alternative as of yet. This CIP is intended to remedy this shortcoming. 

Since addresses have no semantic, it's hard to distinguish two adresses or to ensure that any address points to the intended wallet. 
It would be helpful if humans could use a nickname instead - a nickname that is already established and can be associated with the owner of the wallet, a 
Any application implementing an interface to cardano wallets shall accept nicknames instead of    
A standard should be established to translate wallet addresses into arbitrary strings and vice versa, similar to how IP addresses can be translated into domain names. It should be possible to use easily remembered words / strings instead of the native addresses of a Cardano wallet. It should be possible to assign already established strings to a wallet address. (e.g. a mail address, a mobile number or Twitter addresses). 

A good solution as _an integral part of the Cadrano Blockchain_ brings a competitive advantage and helps to improve adoption rate.  


## Specification 
<!-- The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Cardano platforms. -->

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

_alternate nickname classes:_ The standard should support the creation of alternative nickname classes with their own verification methods. like this, all adahandle.com nicknames could be integrated into the standard. Alternative verification methods not provided by IOHK may be created be third parties.  

_open directory (open API):_ All valid addresses (and all revoked ones) should be accessible and trustworthy for all.
Since the basic data is available to all, any market participants can implement alternative / better / cheaper solutions.

_abuse prevention:_ The creation and revocation of a handle must be simple and inexpensive. The misuse of handles must be prevented.   (identity theft)
- Certification (blue badge)
- Warning for alternative addresses with similar spelling? Character set restriction
- No emojis in handles (reduced character set to reduce equally confusable characters or to place fake ‹verified badges›?)
- dispute procedure

### 1:1?
to be discussed: 
- Should it be possible to assign several nicknames to a wallet (e.g. an email address, a Twitter handle and a mobile number)? - Probably: yes.
- Should it be possible to assign several wallets to one nickname? -- Probably: no. Implementation and Usability will be more complex. Owners may create another nickname for another wallet.

### additional metadata per wallet
Should it be possible to store additional data, e.g. an icon, a public and a private full-text description of the account, ...?

_strategic brand value:_
This «alias meccano» is a fundamental building block for the Cardano Blockchain usability, and so it’s tied very much to the Cardano brand. That’s why I think IOHK should be the issuer of the smart contract (if that’s part of the solution) and IOHK should provide an index.

### Related CIPs
- [Address Resolution and Validation through DNS and HTTP](https://github.com/cardano-foundation/CIPs/pull/319) (by HeptaSean): aims to link wallets to a domain. Not suitable for everyone. A solution for one-man businesses or small and medium sized companies, but not for everyday people. 
- [CIP 13 - Cardano URI Scheme](https://cips.cardano.org/cips/cip13/#paymenturiqueries): If OCaWa nicknames CIP will be accepted and realized, the URI scheme from CIP-0013 should be extended to support a ocawa-nickname as a valid ``cardanoaddress


## Backwards compatibility
<!-- All CIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The CIP must explain how the author proposes to deal with these incompatibilities. -->
((empty))

## Path to Active
<!-- A reference implementation, observable metrics or anything showing the acceptance of the proposal in the community. It must be completed before any CIP is given status "Active", but it need not be completed before the CIP is accepted. It is better to finish the specification and rationale first and reach consensus on it before writing any code. -->
((empty))


---------

```JSON
{
  "ocawan": "*<UTF-8>",
  "cardanoaddress": "*(<BASE58> | <BECH32>)",
  "class": "<REFERENCE to a class in the central repository of Nickname classes like generic, e_mail, twitter_handle, dns_record, ...>"
  "verification_method": "<Free Text with or without reference to the verification method as described in the central repository>"
  "verification_level": "(regular | extended)"
  "created": "<ISO-DATE>",
  "valid_until": "<ISO-DATE>",
  "issuer": "<reference TBD>"
}
```
[^NFT]: The CIP discussions shall elaborate the best way to implement a decentralized publication system and a directory. Maybe the registrar just signes a simple JSON like the one above, and puts an NFT in the owners wallet. 
[^DNS]: a domain name, as [described in the CIP proposal by HeptaSean](https://github.com/cardano-foundation/CIPs/pull/319) is just another class of established handles. The proposed verification method may be one of the standardized verification methods of OCAWAN.
