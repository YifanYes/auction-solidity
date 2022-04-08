# Auction Smart Contract

This is a Smart Contract for a Decentralized Auction like an eBay alternative.

The auction has an **owner** (the person who sells a good or service), a **start** and an **end** date.

The owner can cancel the auction if there is an emergency or can finalize the auction after its end time.

People are sending ETH by calling the function **placeBid()**. The sender's address and the value sent to the auction will be stored in a mapping variable called **bids**.

Users are incentivized to bid the maximun they're willing to pay, but they are not bound to that full amount, but rather to the previous highest bid plus an increment. The contract will autmatically bid up to a given amount.

The **highestBindingBid** is the selling price and the **highestBidder** the person who won the auction.

After the auction ends the owner gets the **highestBindingBid** and everybody else **withdraws** their own amount.

We don't proactively send back the funds to the users that didn't win the auction. We'll use the "withdrawal pattern" instead. We should only send ETH to a user when he explicitly requests it.

This "withdrawal pattern" helps us avoid re-entrance attacks that could cause unexpected behavior, including catastrophic financial loss for the users.
