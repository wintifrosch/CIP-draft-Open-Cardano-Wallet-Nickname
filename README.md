---
CIP: Open Cardano Wallet Nicknames (OCAWAN)
Title: An open standard for a registry / translation service fpr user-friendly wallet nicknames
Authors: wintifrosch <wintifrosch@gmx.ch>
Comments-URI: Github Issues or Pull requests for this draft CIP
Status: Pre-Draft
Type: Process
Created: 2022-10-15
License: CC-BY-4.0
---

# CIP draft: Open Cardano Wallet Nickname «OCaWa nickname»


## Abstract
<!-- A short (~200 word) description of the technical issue being addressed. -->

This draft Cardano Improvement Proposal (CIP) proposes an open standard for a registry / translation service for user-friendly wallet nicknames («OCAWA nicknames»). If you know the nickname of a person, you may find his wallet address (his alias, mail-address, phonenumber, twitter handle, ...). 


## Motivation 
<!-- The motivation is critical for CIPs that want to change the Cardano protocol. It should clearly explain why the existing protocol is inadequate to address the problem that the CIP solves. -->

Wallet addresses are not made for humans - they were never meant for humans, but there is no alternative as of yet. This CIP is intended to remedy this shortcoming. 

A standard should be established to translate wallet addresses into arbitrary strings and vice versa, similar to how IP addresses can be translated into domain names. It should be possible to use easily remembered words / strings instead of the native addresses of a Cardano wallet. It should be possible to assign already established strings to a wallet address. (e.g. a mail address, a mobile number or Twitter addresses). 

A good solution as an integral part of the Cadrano Blockchain brings a competitive advantage and improves the adoption rate.  


## Specification 
<!-- The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Cardano platforms. -->

### 1. Registration
The open standard defines how a nickname can be registered. The registration contains a standardised description of how the authenticity of the nickname has been checked. The verification must be renewed periodically (1 to 3 Years + 1 month).

The registration of a nickname should be free of charge or very inexpensive in order to facilitate a large distribution. Ideally, the nickname can already be given when creating a wallet and can be changed very easily within the wallet app.   

IOHK provides a reference implementation to establish the standard and set a benchmark in terms of performance and cost.  
IOHK also provides an API through which newly registered nicknames can be reported so that they appear in the index as soon as possible. The new entries reported there are publicly viewable. Each registration is validated before it appears in the public list.  

Process:
1. The owner of a wallet deposits his wallet address and any handle with a registrar of his choice.
2. The registrar ensures, that the nickname is available. 
3. The registrar verifies that the owner actually owns the wallet.
4. If the handle meets the syntactic requirements for mail addresses, mobile numbers, Twitter handles (among other strings, tbd), the registrar ensures that the owner actually owns this nickname.
5. The registrar's confirmation is published.[^NFT]
6. The registrar's confirmations can be upgraded via additional procedures, by request of the wallet owner. Users recognise comprehensively verified confirmations by a blue badge, similar to «twitter verified». The documents required for the verification can be sighted or are referenced in the confirmation document.


### 2. De-registration 
Revoking a nickname is free of charge. (The fee to register a name, if any, for creating a handle also covers the cost of revoking a handle). 
If the periodic confirmation is not renewed, the verification expires and the nickname is removed.


### 3. Lookup
IOHK provides a free public API through which the registered wallet address can be requested for a given string (and vice versa, incl. bulk requests (<200 nicknames per request), rate-limited (< 5 API-requests per API-Key), API available in every stake pool relay (opt-out). 

The open standard and the publication of the proofs on the internet allows anyone to realise an alternative/better lookup service. 


### 4. Usability Style Guide
**Moderated by IOHK** Together with the community, IOHK moderates a usability style guide for providers of solutions that support the standard. The style guide ensures that the functions work and look similar in different systems. 

**LOGO** A figurative mark is established to represent an ADA handle, e.g. a symbolised dark blue or white Cardano star (fewer rays and dots for use in text next to characters?). 
- For example, it is possible that operating system manufacturers (Android, iOS/MacOS, Windows) mark those entries in the address books of their users for which an Ada handle exists.  
- Wallet providers could check which contacts of the user have a handle and can list them for the user (similar to how a chat app lists those contacts that can be addressed directly).
- On a Homepage, this iconn to represent the ADA Handle may be placed beside Twitter, Instagram, etc... icons.

A protocol is defined on how the nickname can be represented as an URI. Each (wallet) app can register for this URI format in the operating system and translate the nickname to the wallet adress. 


### 5. Standard Evolvement Procedure  
The Standard establishes procedures to share, elaborate and publish future updates to the standard.


## Rationale
<!-- The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work. The rationale should provide evidence of consensus within the community and discuss important objections or concerns raised during discussion. -->

### Proof of ownership
Whether a nickname actually designates the correct account can be checked at any time because a certificate for the handle must be stored in the wallet.[^NFT]

### Adoption rate
Market penetration is essential. A solution to this problem is only successful if it is used by as many wallet owners as possible and supported by as many wallet manufacturers as possible. This solution should therefore be specified and operated by IOHK or by the Cardano Foundation. 
- ease of use
- low costs / no business model
- open standard / Alternate registries must be certified by IOHK

### uniform standard
A universal solution as part of the standard prevents alternative solutions from establishing themselves. This strengthens the Cardano brand, because all wallets work with the same "OCAWA nickname" standard. And it prevents users from being stranded because a solution is no longer operated. And then alternatives spring up. 

### open directory (open API)
All valid addresses (and all revoked ones) should be accessible and trustworthy for all.
Since the basic data is available to all, any market participants can implement alternative / better / cheaper solutions.

### identity theft
The creation and revocation of a handle must be simple and inexpensive. The misuse of handles must be prevented.   (identity theft)
- Certification (blue badge)
- Warning for alternative addresses with similar spelling? Character set restriction

### abuse prevention
- No emojis in handles (reduced character set to reduce equally confusable characters or to place fake ‹verified badges›?)
- dispute procedure

### 1:1?
to be discussed: 
- Should it be possible to assign several nicknames to a wallet (e.g. an email address, a Twitter handle and a mobile number)? - Probably: yes.
- Should it be possible to assign several wallets to one nickname? -- Probably: no. Implementation and Usability will be more complex. Owners may create another nickname for another account.

### additional Metadata per wallet
Should it be possible to store additional data, e.g. an icon, a public and a private full-text description of the account, ...?


### Related CIPs
<!-- The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work. The rationale should provide evidence of consensus within the community and discuss important objections or concerns raised during discussion. -->


## Backwards compatibility
<!-- All CIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The CIP must explain how the author proposes to deal with these incompatibilities. -->


## Path to Active
<!-- A reference implementation, observable metrics or anything showing the acceptance of the proposal in the community. It must be completed before any CIP is given status "Active", but it need not be completed before the CIP is accepted. It is better to finish the specification and rationale first and reach consensus on it before writing any code. -->


[^NFT]: The CIP discussions shall elaborate the best way to implement a decentralized publication system and a directory. Maybe the registrar just signes a simple JSON and puts an NFT in the owners wallet. 
```JSON
{
  "alias": "*<UTF-8>",
  "cardanoaddress": "*(<BASE58> | <BECH32>)",
  "created": "<ISO-DATE>",
  "valid_until": "<ISO-DATE>",
  "issuer": "<TBD>"
}

<!-- A reference implementation, observable metrics or anything showing the acceptance of the proposal in the community. It must be completed before any CIP is given status "Active", but it need not be completed before the CIP is accepted. It is better to finish the specification and rationale first and reach consensus on it before writing any code. -->
