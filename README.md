# Chainlink VRF Lottery Contract

This repository hosts a decentralized Ethereum lottery smart contract, secured by Chainlink VRF for verifiable randomness. Built with Solidity, tested on Sepolia testnet, and powered by Chainlink's VRF Coordinator V2 Plus.

---

## 🛠 Features

- Random winner selection via Chainlink VRF
- Native ETH ticket payments (0.01 ETH per entry)
- Prize payout to winner (80% of pot) and contract owner (20%)
- Secure access controls for owner-only actions
- Configurable subscription and gas parameters

---

## ⚙️ Contract Parameters

| Parameter        | Description                               |
|------------------|-------------------------------------------|
| `ticketPrice`     | Fixed price per lottery entry (0.01 ETH) |
| `participants[]` | Dynamic list of players                   |
| `winner`         | Last round's winning address              |
| `prizeAmount`    | ETH paid to winner                        |
| `lotteryowner`   | Contract deployer and admin               |

---

## 🔗 Chainlink VRF Integration

This contract uses [Chainlink VRF v2 Plus](https://docs.chain.link/vrf/v2-5/introduction) on Sepolia:

- **Coordinator Address:** `0x9DdfaCa8183c41ad55329BdeeD9F6A8d53168B1B`
- **KeyHash:** `0x787d74caea10b2b357790d5b5247c2f63d1d91572a9846f780606e4d953677ae`
- **Callback Gas Limit:** `200000` (adjustable)

---

## 🚀 Deployment & Usage

### 1. Deploy

Use Remix or Hardhat with the following constructor args:
```solidity
ChainlinkLottery(
  uint64 subscriptionId,
  address coordinatorAddress,
  bytes32 keyHash
)

2. Chainlink Setup
Fund subscription on Chainlink VRF dashboard

Add your contract as a consumer

Ensure native payment is enabled

3. Participate
Call enterLottery() from any wallet with exactly 0.01 ETH to join.

4. Draw Winner
Use drawWinner() from admin account. Chainlink fulfills randomness and triggers fulfillRandomWords().

5. Reset
Call resetLottery() to clear participants and prepare for a new round.

Deployed on Sepolia Testnet: 0xa69619227c5E80144E1A659b996DA7346f867225
