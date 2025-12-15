+++
date = '2025-12-14T14:26:50-06:00'
draft = true
title = 'How to Buy Zcash'
+++

This tutorial walks through the process of buying Zcash (ZEC) using [Zashi](https://electriccoin.co/zashi) and [zkP2P](https://zkp2p.xyz).
Zashi is a privacy-focused Zcash wallet with built-in swap functionality.
zkP2P is a peer-to-peer exchange platform to safely swap fiat currency for USDC.
Zashi uses NEAR-intents as a decentralized & trust-minimized way to swap USDC on Base for ZEC on Zcash.
zkP2P uses zero-knowledge proofs to ensure safe trades from fiat (Venmo, Paypal, CashApp, etc) without trusting a centralized exchange. This gives users censorship resistance and KYC-free access to cryptocurrencies.

## Prerequisites

Before starting this tutorial, ensure you have:

- **Zashi wallet** installed and set up on your mobile device
- **Fiat payment account** such as Venmo (or another payment method supported by zkP2P)
- **Small amount of USD** to purchase with (this tutorial uses $10 as an example)

Note: This process involves some transaction fees, so the amount of ZEC you
receive will be slightly less than your starting USD amount.

## Step 1: Buy USDC on zkP2P

The first step is to acquire USDC (a stablecoin) using zkP2P. zkP2P is a
peer-to-peer exchange that connects buyers and sellers directly while using
zero-knowledge proofs to verify payments without revealing sensitive financial
details. You'll purchase USDC on the Base blockchain, which you'll then convert
to Zcash in the next step.

1) Visit https://zkp2p.xyz
2) Create an account
  > An email account is fast and easy to set up, but be aware of security
  > concerns. The email method is hosted by Privy, and you trust them to guard
  > your keys. For this reason, I would only use this wallet for small
  > purchases with immediate withdrawals to Zashi. For larger purchases or
  > selling, I would use a non-custodial wallet like Rabby, MetaMask, Backpack,
  > etc.
3) Click "Get Started" or navigate to the "Buy" tab
4) Under "You send": select your currency, amount, and payment method
  > This tutorial uses $10 USD with Venmo as the payment method
5) Under "You receive": select Base chain (should be the default), then search for and select USDC
6) Click "Start Order" and wait for the order to be created
7) Carefully read the payment instructions on the next screen
  > Note the drop-down arrow to see additional transaction details. The seller may have provided contact information such as a Telegram chat for questions.

{{< img src="screenshots/01-create-order.png" alt="zkP2P payment instructions screen" caption="Payment instructions showing the amount to send and recipient details" >}}

8) Click "Send Payment". You'll be redirected to your payment provider (Venmo in this example) to complete the transaction
9) Complete the payment through your payment provider, then return to zkP2P
10) Back on zkP2P, click "I have completed payment"
11) zkP2P will request permission to sign in with your payment provider to verify the transaction. Grant permission to continue
12) zkP2P will display a list of your recent payments. Select the payment you just completed
  > **Critical**: Ensure you select the correct payment that matches the amount and recipient from step 7

{{< img src="screenshots/02-verify-venmo-payment.png" alt="Payment verification screen" caption="Select the correct payment from your recent transactions" >}}

13) Click "Verify Payment" and wait for verification to complete
14) After 15-30 seconds, the verification should complete and USDC will be deposited to your wallet on the Base blockchain

{{< img src="screenshots/03-generate-payment-proof.png" alt="Verification complete screen" caption="Transaction complete - USDC received on Base chain" >}}

15) Navigate to the "Send" tab on zkP2P and refresh the page to confirm your new USDC balance

{{< img src="screenshots/04-USDC-received.png" alt="zkP2P balance screen" caption="Your USDC balance is now available to send" >}}

## Step 2: Convert USDC to ZEC via Zashi's Swap Feature

Now that you have USDC on the Base blockchain, you'll use Zashi's built-in swap functionality to convert it to Zcash (ZEC). Zashi's swap feature connects to decentralized exchanges to provide competitive rates while maintaining privacy. The ZEC you receive will be deposited directly into a shielded address in your Zashi wallet.

1) Open the Zashi wallet on your device
2) Tap the "Swap" button
3) Select USDC on the Base chain as the token you want to swap from

{{< img src="screenshots/06-zashi-select-USDC.png" alt="Token selection screen in Zashi" caption="Select USDC on Base as the source token" >}}

4) Enter your Base address from zkP2P as a refund address in case the swap fails
  > **Recommended**: Save this Base address as a contact in Zashi's address book for easy access in future swaps

{{< img src="screenshots/07-zashi-add-contact.png" alt="Adding contact in Zashi" caption="Save your Base address as a contact for convenience" >}}

{{< img src="screenshots/08-zashi-swap-rfq.png" alt="Request for quote screen" caption="Zashi preparing to request a swap quote" >}}

5) Enter the amount of USDC you want to swap (in this example, $9.80)
6) Tap "Get a quote" to request current exchange rates
7) Review the quote details and confirm the trade when you're satisfied with the rate

{{< img src="screenshots/09-zashi-swap-review-quote.png" alt="Quote confirmation screen" caption="Review and confirm the swap quote" >}}

8) Zashi will display a Base address where you need to send your USDC. Copy this address

{{< img src="screenshots/10-zashi-swap-deposit-address.png" alt="Deposit address screen" caption="Copy the deposit address provided by Zashi" >}}

9) Return to zkP2P, navigate to the "Send" tab, and send your USDC to the address Zashi provided. Wait for the transaction to be confirmed on the blockchain

{{< img src="screenshots/11-send-from-zkp2p.png" alt="Sending USDC from zkP2P" caption="Send your USDC to the Zashi swap address" >}}

10) Back in Zashi, tap "I've sent the funds"
11) Within a few moments, you should see a "Receiving..." transaction appear in your Zashi wallet
12) After a few minutes, the transaction will confirm and you'll have ZEC in a shielded address

## Conclusion

Congratulations! You've successfully purchased Zcash using zkP2P and Zashi.
Remember to keep your Zashi wallet and recovery phrase secure.
