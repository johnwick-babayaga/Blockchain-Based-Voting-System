# 🗳️ Blockchain-Based Voting System
> Tamper-evident, auditable, privacy-preserving election platform built on Blockchain + MERN stack

A secure digital voting platform enabling eligible users to cast exactly one verifiable vote using blockchain. The system provides auditability, on-chain proofs, privacy-preserving flows, and React dashboards for voters & administrators.

## ✅ Problem Statement
Design and implement a tamper-evident voting system where:
- Each eligible voter can cast **exactly one ballot**
- Final tally is **publicly verifiable**
- Every vote carries **on-chain proof (tx hash, block number)**

Backend → Node.js (Express)  
Blockchain → Ethereum (Ganache/Web3.js) or Hyperledger (chaincode)  
Database → MongoDB  
Frontend → React  

REST APIs must support:
create → open → close → tally

Privacy features such as **commit–reveal** (EVM) or **private data collections** (Fabric) are required.

## 🚀 Key Features
### 🔌 Ledger Abstraction
- Interchangeable blockchain backend
- Same REST API for EVM / Fabric
- Smart contract OR chaincode implementation

### ✅ Smart Contract / Chaincode
Core capabilities:
- `createElection`
- `registerVoter`
- `castVote`
- `closeElection`
- `getTally`

Guarantees:
- One vote per eligible voter
- Records immutable
- Phase-based voting enforcement

## 👥 Eligibility & Identity
- Admin uploads eligible voters (`address ↔ voterId`)
- Stored in MongoDB + anchored on-chain
- Authentication:
  - EVM → wallet signatures
  - Fabric → MSP identity

## 🕶 Privacy Options
### EVM
- Commit-reveal:
  - Commit = hash(choice + salt)
  - Reveal choice + salt later
- Optional: encrypt votes off-chain & store receipt on-chain

### Hyperledger Fabric
- Private Data Collections
- Optional channels for sensitive data

## ✅ Verifiable Tally
- On-chain or deterministic re-tally from reveals
- Frontend displays:
  - Transaction hash
  - Block number
  - Confirmations
- Evidence reports exportable

## 🔐 Fraud Prevention
- Double-vote rejection
- Phase-restricted access
- Malformed reveal mitigation
- Admin action logging with timestamps

## 🖥 React UI
### Voter
1. Select election
2. Select candidate
3. Confirm → sign → submit
4. View receipt
5. Verify vote later

### Admin
- Create elections
- Open/close elections
- Upload eligibility lists
- View participation rate
- Export signed tally proofs

## 🗄 MongoDB Metadata
Stores:
- Election config
- Candidate list
- Eligibility mirror
- Minimal receipts (no sensitive payloads)

## 🔒 Security
- JWT authentication
- TLS encryption
- Rate limiting
- Replay protection
- Input validation
- Server never stores private keys

## 📊 Auditing + Observability
- Structured logging
- Admin action audit trail
- Per-election stats

## ⚙️ Local Dev & Ops
Includes scripts for:
- Ganache/Hyperledger startup
- Contract/chaincode deployment
- Seeding voters/elections
- Smoke tests (create → vote → tally)

## 🏗 Architecture

| Component | Technology |
|----------|------------|
| Blockchain | Ethereum (Ganache) / Hyperledger |
| Smart Logic | Solidity / Chaincode |
| Backend | Node.js + Express |
| Database | MongoDB |
| Frontend | React |
| Auth | JWT |
| Wallet | Web3.js / MetaMask |
| Optional | Docker |

## 📦 Folder Structure (Example)


root/
├── backend/
│ ├── src/
│ ├── contracts/
│ └── routes/
├── frontend/
│ └── src/
├── chaincode/
├── scripts/
└── README.md
