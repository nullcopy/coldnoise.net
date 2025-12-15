+++
date = '2025-12-14T14:26:50-06:00'
draft = false
title = 'Buying Zcash the Trustless Way: Zashi + zkP2P'
+++

This tutorial walks through buying Zcash (ZEC) directly from fiat currency
(USD) without needing to trust a company or provide identification. Unlike
traditional exchanges that require KYC verification (identity documents like a
driver's license) and can freeze your account, this method combines
[Zashi](https://electriccoin.co/zashi) (a privacy-focused Zcash wallet app) and
[zkP2P](https://zkp2p.xyz) (a peer-to-peer exchange) to purchase ZEC directly
from other users.

The process: use zkP2P to convert fiat (Venmo, Paypal, CashApp, etc.) into
USDC (a digital dollar), then use Zashi to swap that USDC for ZEC. This
two-step process exists because you can't buy ZEC directly with fiat in a
privacy-preserving way - the intermediate step through USDC makes it possible.
For more technical details, see [how NEAR intents work in
Zashi](https://electriccoin.co/blog/zashi-swaps-decentralized-on-ramp-is-live/)
and [how zkP2P uses zero-knowledge
proofs](https://docs.zkp2p.xyz/protocol/zkp2p-protocol).

## Prerequisites

Before starting this tutorial, you'll need:

### 1. Install Zashi Wallet

[Zashi](https://electriccoin.co/zashi) is the mobile app for you to
store/send/receive Zcash. Download it from:
- **iPhone**: Search "Zashi" in the App Store
- **Android**: Search "Zashi Wallet" in Google Play Store

After installing, open the app and:
1. Tap "Create New Wallet"
3. Follow steps to complete setup

### 2. Payment Method

You'll need a **Venmo, CashApp, Zelle, Revolute, or Paypal account** to pay for
USDC on zkP2P.

### 3. Starting Amount

Have a **small amount of USD ready** (this tutorial uses $10 as an example).
Transaction fees will reduce your final ZEC amount slightly.

## Step 1: Buy USDC on zkP2P

The first step is to acquire USDC (a digital dollar) using zkP2P. zkP2P
connects you directly with sellers, and you'll pay them via Venmo (or another
payment app). You'll receive USDC on the Base blockchain, which you'll then
convert to Zcash in the next step.

### Create Your Account

1) Visit https://zkp2p.xyz
2) Create an account using your email
  > **Security note**: The email signup option uses a service called Privy that
  > controls your zkP2P wallet for you (like how your bank controls your bank
  > account). This is convenient but means you're trusting them. For larger
  > amounts, consider using a self-custody wallet option instead.

### Place Your Order

3) Click "Get Started" or navigate to the "Buy" tab
4) Under "You send": select your currency, amount, and payment method
  > This tutorial uses $10 USD with Venmo as the payment method
5) Under "You receive": select Base chain (should be the default), then search
for and select USDC
6) Click "Start Order" and wait for the order to be created
7) Carefully read the payment instructions on the next screen
  > Note the drop-down arrow to see additional transaction details. The seller
  > may have provided contact information such as their Telegram ID for
  > questions.

{{< img src="screenshots/01-create-order.png" alt="zkP2P payment instructions screen" caption="Payment instructions showing the amount to send and recipient details" >}}

### Complete Payment

8) Click "Send Payment". You'll be redirected to your payment provider (Venmo
in my case) to complete the transaction
9) Complete the payment through your payment provider, then return to zkP2P
10) Back on zkP2P, click "I have completed payment"
11) zkP2P will request permission to sign in with your payment provider to
verify the transaction. Grant permission to continue

### Verify Payment

12) zkP2P will display a list of your recent payments. Select the payment you
just completed
  > **Critical**: Ensure you select the correct payment that matches the amount
  > and recipient from step 7

{{< img src="screenshots/02-verify-venmo-payment.png" alt="Payment verification screen" caption="Select the correct payment from your recent transactions" >}}

13) Click "Verify Payment" and wait for verification to complete
14) After 15-30 seconds, the verification should complete and USDC will be
deposited to your wallet on the Base blockchain

{{< img src="screenshots/03-generate-payment-proof.png" alt="Verification complete screen" caption="Transaction complete - USDC received on Base chain" >}}

15) Navigate to the "Send" tab on zkP2P and refresh the page to confirm your
new USDC balance

{{< img src="screenshots/04-USDC-received.png" alt="zkP2P balance screen" caption="Your USDC balance is now available to send" >}}

16) **Important**: While on the "Send" tab, look for your wallet address
(starts with "0x"). Copy this address - you'll need it in Step 2 as your refund
address. It's displayed near the top of the screen, usually next to a copy
button.

## Step 2: Convert USDC to ZEC via Zashi's Swap Feature

Now that you have USDC, you'll use Zashi's built-in swap feature to convert it
to Zcash (ZEC). This swap happens without any company in the middle. The ZEC
you receive will go into a "shielded address" (a private address that hides
your transaction details).

### Set Up the Swap

1) Open the Zashi wallet on your device
2) Tap the "Swap" button
3) Select USDC on the Base chain as the token you want to swap from

{{< img src="screenshots/06-zashi-select-USDC.png" alt="Token selection screen in Zashi" caption="Select USDC on Base as the source token" >}}

4) Paste the zkP2P wallet address you copied in Step 1.16 (the one starting
with "0x"). This is your refund address in case the swap fails
  > **Tip**: Save this address as a contact in Zashi's address book so you don't
  > have to copy/paste it next time

<div class="image-row">

{{< img src="screenshots/07-zashi-add-contact.png" alt="Adding contact in Zashi" caption="Save your Base address as a contact for convenience" >}}

{{< img src="screenshots/08-zashi-swap-rfq.png" alt="Request for quote screen" caption="Zashi preparing to request a swap quote" >}}

</div>

### Get a Quote and Confirm

5) Enter the amount of USDC you want to swap (in this example, I have $9.80
available in zkP2P)
6) Tap "Get a quote" to request current exchange rates
7) Review the quote details and confirm the trade when you're satisfied with
the rate

{{< img src="screenshots/09-zashi-swap-review-quote.png" alt="Quote confirmation screen" caption="Review and confirm the swap quote" >}}

### Send Funds and Complete

8) Zashi will display a Base address where you need to send your USDC. Copy
this address

{{< img src="screenshots/10-zashi-swap-deposit-address.png" alt="Deposit address screen" caption="Copy the deposit address provided by Zashi" >}}

9) Return to zkP2P, navigate to the "Send" tab, and send your USDC to the
address Zashi provided. Wait for the transaction to be confirmed (usually 1-2
minutes)

{{< img src="screenshots/11-send-from-zkp2p.png" alt="Sending USDC from zkP2P" caption="Send your USDC to the Zashi swap address" >}}

10) Back in Zashi, tap "I've sent the funds"
11) Within a few moments, you should see a "Receiving..." transaction appear in
your Zashi wallet
12) After a few minutes, the transaction will confirm and you'll have ZEC in a
shielded address

## Conclusion

Congratulations! You've successfully purchased Zcash using zkP2P and Zashi.
Your ZEC will take a few minutes to become "spendable" (ready to send). Once
it's ready, why not test it out? Send me an encrypted message:

1. In Zashi, tap "Send"
2. Scan the QR code below (or paste the address from the caption)
3. Enter a small amount to pay the network fee
4. Leave me some feedback.
5. Send!

The memo is encrypted and only I can read it. I'd love to hear from you.

{{< img src="zec-addr-qr.jpeg" alt="Author's Zcash shielded address QR code" caption="u1rcw0ppy2z4am3rh7kffh0gn3zscw5dpffnvvajwpx4u7qe5syg3ygf0z4cp2w2czxl4tw3k3s5jzgdvdutx0095gp0mdp5mz203cm905kchcp80jsu39s7ummxxeak9rgvel233dgh4rza0t8nsj0dxhu8wmy42dugxgslgedywlwlkm" >}}

---
*"If we can't crack encryption, then people are walking around with a Swiss bank
account in their pocket."* \- **Barack Obama**
