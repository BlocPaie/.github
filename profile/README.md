<div align="center">

<img src="./logo.png" alt="BlocPaie" width="140" />

# BlocPaie

**Confidential on-chain payroll for the modern workforce.**

Pay contractors on Ethereum while keeping every salary amount, payee identity, and payment status fully encrypted on-chain — powered by Zama's Fully Homomorphic Encryption and ERC-7984 confidential tokens.

[![Ethereum Sepolia](https://img.shields.io/badge/Ethereum-Sepolia-627EEA?logo=ethereum&logoColor=white)](https://sepolia.etherscan.io)
[![Powered by Zama fhEVM](https://img.shields.io/badge/Powered%20by-Zama%20fhEVM-6B46C1)](https://www.zama.ai)
[![Porto](https://img.shields.io/badge/Wallet-Porto%20EIP--7702-0EA5E9)](https://porto.xyz)

</div>

---

## What is BlocPaie?

BlocPaie is an invoice-to-payment platform where companies create on-chain payroll vaults and pay contractors with sponsored, gasless transactions — no MetaMask, no gas fees, no exposed salaries.

- **Privacy by default** — salary amounts, payee addresses, and cheque statuses are stored as FHE ciphertexts. Nobody on-chain — including the contract itself — can read them in plaintext.
- **Passkey-native** — wallets are Porto smart accounts backed by WebAuthn passkeys. No seed phrases.
- **Gasless** — all transactions are sponsored via Ithaca Relay. Companies and contractors pay nothing in gas.
- **Two vault modes** — a transparent ERC-20 vault for compliance-first setups and a confidential vault for full privacy.

---

## How It Works

```
Company                                    Contractor
   │                                           │
   ├─ 1. Create vault (ERC-20 or Confidential) │
   ├─ 2. Deposit USDC / cUSDC                  │
   ├─ 3. Approve invoice                       │
   ├─ 4. Register cheque on-chain              │
   │      └─ Confidential: encrypted payee + amount
   │                                           │
   │                              ┌────────────┤
   │                              │ 5. Execute cheque
   │                              │    USDC / cUSDC transferred
   │                              │ 6. Decrypt cUSDC balance (optional)
   │                              │ 7. Unwrap cUSDC → USDC (optional)
   │                              └────────────┤
   ├─ 8. Withdraw remaining funds              │
```

### Privacy Model

| Data | ERC-20 Vault | Confidential Vault |
|------|--------------|--------------------|
| Salary amount | Public | Encrypted (FHE) |
| Payee address | Public | Encrypted (FHE) |
| Cheque status | Public | Encrypted (FHE) |
| cUSDC balance | — | Holder only (Zama `userDecrypt`) |

---

## Repositories

| Repo | Description |
|------|-------------|
| [**contracts**](https://github.com/BlocPaie/contracts) | Solidity smart contracts — ERC20Vault, ConfidentialVault, VaultFactory, cUSDC (ERC-7984). 88 tests. |
| [**backend**](https://github.com/BlocPaie/backend) | Express REST API — company/contractor identity registry, invoice lifecycle, vault transaction history. |
| [**frontend**](https://github.com/BlocPaie/frontend) | Next.js dApp — company and contractor dashboards, Porto passkey auth, client-side FHE operations. |

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Chain | Ethereum Sepolia |
| Smart contracts | Solidity 0.8.28, OpenZeppelin 5, Zama fhEVM |
| Confidential token | ERC-7984 — cUSDC wrapping USDC |
| Wallet & auth | Porto (EIP-7702 smart accounts, WebAuthn passkeys) |
| Gas sponsorship | Ithaca Relay + Porto merchant route |
| FHE | Zama `@zama-fhe/relayer-sdk` |
| Frontend | Next.js 16, React 19, Wagmi 3, viem 2 |
| Backend | Node.js, Express 4, MongoDB, Mongoose, Zod |

---

## Deployed Contracts (Ethereum Sepolia)

| Contract | Address |
|----------|---------|
| VaultFactory | [`0xfB6760E4aa9eCe674Afc05Ec8c3F5a12384FEF9C`](https://sepolia.etherscan.io/address/0xfB6760E4aa9eCe674Afc05Ec8c3F5a12384FEF9C) |
| MockUSDC | [`0xf1DfBFD875a5E4dAb6a041c4da27f8F0b1b5217f`](https://sepolia.etherscan.io/address/0xf1DfBFD875a5E4dAb6a041c4da27f8F0b1b5217f) |
| ConfidentialUSDC (cUSDC) | [`0x83662eb8350e3Bf66666Bfbc673185379E11Af56`](https://sepolia.etherscan.io/address/0x83662eb8350e3Bf66666Bfbc673185379E11Af56) |

---

<div align="center">
  <sub>Built for the Zama × Porto hackathon &nbsp;·&nbsp; Ethereum Sepolia</sub>
</div>
