+++
date = '2025-12-14T14:26:50-06:00'
draft = true
title = 'How to Buy Zcash'
+++

# Steps to reproduce
## Buy USDC on zkP2P
1) visit zkp2p.xyz
1) create account
  > email account is fast and easy, but trust & privacy concerns
  > I will ONLY ever use this account for small buys and immediate withdrawals.
1) Click "get started" or navigate to the "buy" tab
1) Under "You send": select your currency, amount, and payment method to buy ZEC
  > I will pay 10 USD with Venmo
1) Under "You receive": select Base chain (should be default). Search for & select USDC.
1) Click "Start Order" and wait for the order to be created
1) Carefully read payment instructions
  > Note the drop-down arrow to see more transaction details. The seller may have provided a Telegram chat to ask questions.
  <claude, use screenshot/01-* here>
1) Click "Send Payment". You'll be prompted to log in to your payment provider (Venmo in my case) and complete the payment.
1) AFTER you have completed the payment, return to zkP2P and click "I have completed payment"
1) Next, zkP2P will need to sign in with Venmo.. do it.
1) zkP2P will show a list of recent payments. Select the payment you just sent.
  > BE SURE TO SELECT THE CORRECT PAYMENT
  <claude, use screenshot/02-* here>
1) Click "Verify Payment" and wait for verification to complete.
1) In 15~30 seconds, your transaction should complete and you should have received USDC in your wallet (may need confirmations if using other chain)
  <claude, use screenshot/03-* here>
1) Navigate to "Send" tab on zkP2P and refresh the page to see your new balance
  <claude, use screenshot/04-* here>

## Conert USDC to ZEC via Zashi's swap feature
1) Open Zashi
1) in Zashi, Click "Swap"
1) in Zashi, Select USDC on Base
  <claude, use screenshot/06-* here>
1) in Zashi, paste your Base address from zkP2P to handle refunds if the trade fails. Better yet, add that address as a contact in zashi, so in the future you can just select this contact.
  <claude, use screenshot/07-* and screenshot/08-* here... these specifically show use of the address book>
1) in Zashi, Enter amount ($9.80 in my case)
1) in Zashi, Click "Get a quote"
1) Zashi will ask you to confirm the trade.. do it
  <claude, use screenshot/09-* here>
1) Zashi will show a Base address to send funds. Copy it.
  <claude, use screenshot/10-* here>
1) in zkP2P send funds to the address Zashi gave you and wait for TX to mine
  <claude, use screenshot/11-* here>
1) in Zashi, click "I've sent the funds"
1) You should soon see a "Receiving..." transaction in Zashi
1) After a few minutes it will confirm, and you will have ZEC in a shielded address

Tada!
