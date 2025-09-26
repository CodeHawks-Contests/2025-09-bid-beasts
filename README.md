# BidBeasts NFT Marketplace

# Contest Details

### Prize Pool

- High - 100xp
- Medium - 20xp
- Low - 2xp

- Starts: September 25, 2025 Noon UTC
- Ends: October 02, 2025 Noon UTC

### Stats

- nSLOC: 170
- Complexity Score: 116

[//]: # (contest-details-open)

## About the Project

This smart contract implements a basic auction-based NFT marketplace for the `BidBeasts` ERC721 token. It enables NFT owners to list their tokens for auction, accept bids from participants, and settle auctions with a platform fee mechanism.

The project was developed using Solidity, OpenZeppelin libraries, and is designed for deployment on Ethereum-compatible networks.

---

## The flow is simple:

1. **Listing**:  
   - NFT owners call `listNFT(tokenId, minPrice)` to list their token.
   - The NFT is transferred from the seller to the marketplace contract.

2. **Bidding**:  
   - Users call `placeBid(tokenId)` and send ETH to place a bid.
   - New bids must be higher than the previous bid.
   - Previous bidders are refunded automatically.

3. **Auction Completion**:  
   - After 3 days, anyone can call `endAuction(tokenId)` to finalize the auction.
   - If the highest bid meets or exceeds the minimum price:
     - NFT is transferred to the winning bidder.
     - Seller receives payment minus a 5% marketplace fee.
   - If no valid bids were made:
     - NFT is returned to the original seller.

4. **Fee Withdrawal**:  
   - Contract owner can withdraw accumulated fees using `withdrawFee()`.

---

## The contract also supports:

- **Minimum price enforcement** for listings.
- **Minimum bid enforcement** for bidders.
- **Auction deadline** of exactly 3 days.
- **Automatic refunding** of previous highest bidder.
- **Only owner access** for withdrawing platform fees.

---
## Actors

- **Seller (NFT Owner)**
    - Owns a `BidBeasts` NFT and lists it for auction.
    - Receives payment if the auction is successful.

- **Bidder (Buyer)**
    - Places ETH bids on active auctions.
    - Receives the NFT if they win the auction.

- **Contract Owner (Platform Admin)**
    - Deployed the marketplace contract.
    - Can withdraw accumulated platform fees.
 
[//]: # (contest-details-close)

[//]: # (scope-open)

## BidBeastsNFT Structure

```
├── lib/
├── src/
│   ├── BidBeasts_NFT_ERC721.sol
│   └── BidBeastsNFTMarketPlace.sol
```

---

## Compatibility

- **Chain**: Ethereum  
- **Token Standard**: ERC721  

[//]: # (scope-close)

[//]: # (getting-started-open)

## Set-up

```bash
git clone <repository-url>
cd <repository-folder>

forge install OpenZeppelin/openzeppelin-contracts@v5.1.0
forge install foundry-rs/forge-std

forge compile
forge test

[//]: # (getting-started-close)

[//]: # (known-issues-open)

None Reported! ;)

[//]: # (known-issues-close)
