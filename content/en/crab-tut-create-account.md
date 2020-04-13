---
id: crab-tut-create-account
title: Create an Account
sidebar_label: Create an Account
---

## Generate a Darwinia account

There are several ways to generate a Darwinia account, you can choose either one based on your preference.  Once your account is created and you have your account `secret phrase` or `secret seed`, you can migrate your account from various medium by importing your account.  

  <!--DOCUSAURUS_CODE_TABS-->
  <!--Darwinia Web Apps-->
### Darwinia Web Apps

Enter [Darwinia Crab Web Wallet](https://apps.darwinia.network), you can see two buttons "Add Account" and "Restore  JSON" in the "Account" column.

![create account](assets/web-wallet-1-en.png)

** New account **

Click "Add Account", after setting the basic account information, click the "Save" button. (By default, only "mnemonic", "private key" need to be switched)

![create account](assets/web-wallet-2-en.png)

Click the "Create and Backup Account" button to back up the account "json file"

![create account](assets/web-wallet-3-en.png)

> Be sure to back up `mnemonics, private keys, json files`, etc. When backing up the json file, please keep the password safe. If the password is lost, the address cannot be restored through the json file, but it can be re-imported through the mnemonic word and private key.

** Restore  json **

If you have created an account before and backed up a json file, you can directly select "Restore JSON".

![create account](assets/web-wallet-4-en.png)

** Restore account via "Mnemonic" **

If you forget the password of the JSON file, you can use the "mnemonic word" to recover it. Click "Add Account" to replace the mnemonic with the original account's mnemonic. (The name and password can be reset)

![create account](assets/web-wallet-5-en.png)

  <!--Polkadot.js Browser Plugin-->
### Polkadot.js Browser Plugin

**Install the Browser Plugin**

The browser plugin is available for both [Google Chrome](https://chrome.google.com/webstore/detail/polkadot%7Bjs%7D-extension/mopnmbcafieddcagagdcbnhejhlodfdd?hl=en) and [FireFox](https://addons.mozilla.org/en-US/firefox/addon/polkadot-js-extension).

![polkadot-js](assets/polkadot-js-1-cn.png)

** New Account **

Click the extension to open the "Account Management" dialog box, click the "Create New Account" button, and then follow the instructions.

![polkadot-js](assets/polkadot-js-2-cn.png)

![polkadot-js](assets/polkadot-js-3-cn.png)

> Make sure to keep the mnemonics safe.

**Set Address for Darwinia Mainnet or Crab Network**

Now we will ensure that the addresses are displayed as Darwinia mainnet addresses.  Your address will be different depending on network selection.

Click on "Options" at the top of the plugin window.  Select `Crab Network` or `Substrate` in "Display Address Format for" dropdown box. 

![polkadot-js](assets/polkadot-js-4-cn.png)

> Crab Network share the same `Network ID` as `Substrate`, if you need to choose a network when generating an account, use `substrate` as the same effect as `crab network`.

  <!--Subkey CLI-->
### Subkey

Subkey is recommended for technically advanced users who are comfortable with command line and compiling Rust code. Subkey allows you to generate keys on any device that can compile the code. Subkey may also be useful for automated account generation, using an air-gapped device other than one running iOS or Android or other specific purposes. It is not recommended for general users.

To [install Subkey](https://substrate.dev/docs/en/ecosystem/subkey#more-subkey-to-explore), run:

```bash
$ curl https://getsubstrate.io -sSf | bash -s -- --fast
$ cargo install --force --git https://github.com/paritytech/substrate subkey
$ cargo build -p subkey
```

After installing Subkey successfully, run:

```shell
subkey -n substrate generate
```

You should see an output something like below- **save all of this information somewhere secure you will not be able to recover your account if you lose your phrase or seed.**

```text
Secret phrase `destroy vague trend estate person civil cattle lab hockey tooth error pigeon` is account:
  Network ID/version: substrate
  Secret seed:        0x58e57817a2ccfa696ed6c3735d4cc4646f894bf7daf51a94f0c4702a92e40710
  Public key (hex):   0x225ce1f9c178189d2a977a195f822ebbfb538b317f23f83ab35605fb009fa438
  Account ID:         0x225ce1f9c178189d2a977a195f822ebbfb538b317f23f83ab35605fb009fa438
  SS58 Address:       2owvscruh7PNbykGLMZPxHyjYdi1Ryanrm4PTxVKh85Ef8Dn
```

> If you previously created an account for other networks other than `substrate` or `crab network`, you need to derive the  correct `Address` from your previous  `secret phrase` or `secret seed`.  You can use `subkey -n substrate inspect "YOUR SECRET PHRASE HERE"` to obtain the Crab network-ID inclusive Address (SS58).

  <!--Polkadot.js Web Apps-->
### Polkadot.js Web Apps
TODO: complete guide when Darwinia network is supported

  <!--Mobile Wallet-->
### ~~Itering ID Wallet~~

Coming soon.

### ~~Math Wallet~~

Coming soon.
  <!--END_DOCUSAURUS_CODE_TABS-->
<hr />

## Storing your key safely

> **DISCLAIMER: Key Security**
Your secret seed is the _only_ way to get access to your account. You must keep
the secret both secure and private. If you share you secret with anyone they
will be able to have full access to your account, including all of your funds.
The secret, for this reason, is a target from hackers and others with bad
intentions to steal your funds. We recommend a variety of account generation
methods that have various convienience and security tradeoffs. Please review
this page carefully before making your address so that you understand the risks
of the account generation method you choose and how to properly mitigate them
in order to keep your funds safe.

The seed is your **key** to the account. Knowing the seed allows you, or anyone
else who knows the seed, to re-generate and control this account.

It is imperative to store the seed somewhere safe, secret, and secure. If
you lose access to your account, you can re-create it by entering the seed. This
also means that somebody else can have control over your account if they have
access to your seed.

For maximum security, the seed should be written down on paper or another non-digital device and stored in a
safe place. You may also want to protect your seed from physical damage, as well (e.g. by storing in a sealed
plastic bag to prevent water damage, storing it in a fireproof safe, etc.) It is recommended that you store
multiple copies of the seed in geographically separate locations (e.g., one in your home safe and one in a
safety deposit box at your bank).

You should definitely not store your seed on any kind of computer that has or may have access to the internet
in the future.