# Decentralized Game Account Exchange (DGAE)

## 1. Overview
The **Decentralized Game Account Exchange (DGAE)** is a blockchain-based platform that enables players to buy and sell Web3 game accounts in a secure, transparent, and decentralized manner. It leverages Solidity smart contracts for on-chain account exchange and Next.js for the user interface.

### Key Features
- On-chain account exchange powered by Solidity.  
- Transaction settlement in **USDC stablecoin**.  
- **EIP-712 signed message verification** for both sellers and buyers.  
- Future support for **off-chain account trades**.  

---

## 2. Core Workflow

### Seller Flow
1. Seller lists a game account for sale by submitting:  
   - Account metadata (unique ID, game identifier).  
   - Sale price in USDC.  
   - A signed message verifying ownership of the account (**EIP-712 standard**).  
2. Smart contract verifies the signature to ensure authenticity.  
3. Listing becomes available in the marketplace.  

### Buyer Flow
1. Buyer selects a listed game account.  
2. Buyer signs a transaction with:  
   - Agreement to purchase at the listed price.  
   - Confirmation signature (**EIP-712**).  
3. Smart contract validates buyer’s signed message and ensures payment in USDC.  
4. On successful validation, ownership rights transfer to the buyer.  

### Exchange Settlement
- The smart contract holds **USDC** until both parties’ signatures are verified.  
- Once verified, the seller receives **USDC**, and the buyer obtains proof of account transfer.  

---

## 3. Smart Contract Architecture (Solidity)

### Key Components
- **AccountRegistry**: Maintains mappings of game accounts to owners.  
- **ExchangeContract**: Facilitates listing, purchase, and verification of accounts.  
- **SignatureVerifier**: Uses **EIP-712 standard** for message verification.  

### Solidity Flow
- `listAccount(accountId, price, signature)` → Creates a listing after verifying seller signature.  
- `buyAccount(listingId, signature)` → Buyer confirms purchase.  

Contract validates:  
- Seller signed ownership.  
- Buyer signed confirmation.  
- Payment in **USDC** is sufficient.  

Funds released to seller, ownership transferred to buyer.  

---

## 4. Frontend (Next.js)

### Features
- **Wallet Connection**: MetaMask, WalletConnect, Coinbase Wallet.  
- **Account Listing Dashboard**:  
  - List account with metadata.  
  - Upload signed ownership proof.  
- **Marketplace**:  
  - Browse available accounts.  
  - Filter by game, price, popularity.  
- **Buyer Flow**:  
  - Sign purchase intent message.  
  - Confirm transaction.  
- **Transaction History & Status**  

---

## 5. Future Roadmap

### Phase 1 — Core Exchange (MVP)
- Smart contract with listing and purchase flow.  
- USDC integration.  
- Web3-enabled Next.js frontend.  

### Phase 2 — Enhanced Security & UX
- Escrow with dispute resolution.  
- Integration with popular Web3 games.  
- Gasless transactions via meta-transactions.  

### Phase 3 — Off-Chain Trade Support
- Off-chain trading with on-chain settlement proofs.  
- Integration with third-party gaming APIs.  

### Phase 4 — Governance & DAO
- Governance for fees, rules, and roadmap.  

---

## 6. Technology Stack
- **Smart Contracts**: Solidity, Hardhat/Foundry  
- **Frontend**: Next.js, React.js  
- **Wallet Integration**: Ethers.js, Wagmi, RainbowKit  
- **Stablecoin**: USDC (ERC20)  
- **Infrastructure**: IPFS/Arweave (metadata storage), Ethereum or L2 (Arbitrum, Polygon)  

---

## 7. Benefits
- **Trustless exchange**: No centralized authority.  
- **Stable payments**: USDC ensures price stability.  
- **Ownership verification**: EIP-712 signed messages prevent fraud.  
- **Future expansion**: Off-chain trades and DAO governance.  
