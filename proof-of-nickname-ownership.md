# Proof of nickname ownership

To prevent phishing attacks, each ``nickname record`` contains a ``claim of nickname ownership``. This claim must be verified before the nickname is used. This may be executed in a batch, while building an index. The index may include a verification history.

There are a lot of ``claim types``, each with his own procedures to create and verify a claim. Some of those procedures use a hash function (algo to be defined)  

## social media account names 
easy, popular, practial, without costs

It is easy to register any social media account name as a ocawan handle, if the system allows to either ...
- to publish a text message containing the wallet address hash, get a permanent link pointing to this message and put this link into the ownership claim. 
- to add the wallet address (or a hash of it) to your shared profile info and add a link to your profile page into the ownership claim.

Both methods work with twitter, instagram, ...
The second method only works for tiktok, ...


## Mailadress + S/MIME certificate
cumbersome and expensive (~15 USD per Year)


## Google Cloud API
Not applicable, too cumbersome.

Since Google+ was dropped, it is no longer possible to share contact details. A Google Cloud Account and an assiciated API key can reveal the main acccount mail address to anyone presenting an authorized API key. Users must create the Gooogle Cloud Account and create a «sign in with google» 
<!-- 
## google+ > mobile > public
● create a claim:
  1. Log in to your Google account, open ``about me``, click ``Add contact``
  2. Select «Phonenumber (mobile)» in the topmost dropdown, enter your phone number and at the bottom make this number available for everybody. 
  3. share the address of your google contact conte

## google+ > mobile > hashed
● create a claim:
  1. create a md5 hash of your mobile number (e.g. on https://www.md5hashgenerator.com).   
  Make shure to insert your mobile number only, starting with a plus sign and the international prefix, without any before, within and after the number, and no newline.
  2. Log in to your Google account, open ``about me``, scroll to the section ``Info`` and click the Plus sign to add a new entry. (More Info in [Google Account help](https://support.google.com/accounts/answer/6304920?hl=en&utm_source=google-account&utm_medium=profile-card#zippy=%2Cwho-can-view-your-info))
  3. A form with two input fields appears. 
    - enter "cardano-ocawan-mobile-hash" in the upper field (without quotation marks)
    - enter your hash below, without any supplemental characters. 
-->



## twitter


