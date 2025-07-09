# 📘 TokenPresaleApp

A decentralized application (dApp) for managing a **token presale**.  
It combines **Solidity smart contracts** with a **Vite-powered frontend** to allow users to securely purchase tokens before the official launch.

---

## 🔹 Features

- **ERC-20 Token (`token.sol`)**
  - Implements a standard ERC-20 token.
  - Configurable name, symbol, total supply, and decimals.

- **Presale Contract (`token_presale.sol`)**
  - Accepts ETH contributions.
  - Calculates token allocation at fixed rate.
  - Tracks presale progress (sold tokens, caps).
  - Owner can withdraw ETH after presale closes.
  - Optional functionality: burning unsold tokens.

- **Frontend (Vite + React)**
  - Connect wallet (MetaMask / WalletConnect).
  - Display presale status: price, progress, remaining supply.
  - Buy tokens with ETH via a simple UI.
  - Responsive design (mobile-friendly).

---

## 📂 Project Structure

```
TokenPresaleApp/
├── contracts/                # Solidity smart contracts
│   ├── token.sol             # ERC-20 Token contract
│   ├── token_presale.sol     # Presale contract logic
│   └── deployed_adr          # Saved deployment addresses
├── public/                   # Static frontend assets (icons, fonts, loaders)
├── src/                      # Frontend application code (React + Vite)
├── .env.default              # Example environment variables
├── vite.config.js            # Vite build config
├── package.json              # Node.js dependencies & scripts
├── README.md                 # Project documentation
└── CONTRIBUTING.md           # Contributor guidelines
```

---

## ⚙️ Tech Stack

- **Smart Contracts:** Solidity (ERC-20, presale logic)
- **Frontend:** React + Vite
- **Blockchain Interaction:** ethers.js
- **Build Tools:** Hardhat or Truffle (for contract deployment)
- **Wallets Supported:** MetaMask, WalletConnect

---

## 🚀 Getting Started

### 1. Clone Repository
```bash
git clone https://github.com/your-organization/your-project.git
cd your-project
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Setup Environment Variables
Copy `.env.default` → `.env` and configure:

```env
VITE_DCL_DEFAULT_ENV=dev
GEN_STATIC_LOCAL=true
VITE_BASE_URL=/
VITE_REACT_APP_WEBSITE_VERSION="0.0.0"
VITE_ALCHEMY_API_KEY=your-key
VITE_CONTRACT_ADDRESS=0xYourDeployedPresaleAddress
VITE_TOKEN_ADDRESS=0xYourTokenAddress
VITE_NETWORK=sepolia
```

### 4. Run Development Server
```bash
npm start
```
Frontend runs at `http://localhost:5173/`

### 5. Build for Production
```bash
npm run build
```

---

## 📜 Smart Contract Workflow

### Deploy Contracts
1. Compile:
   ```bash
   npx hardhat compile
   ```
2. Deploy:
   ```bash
   npx hardhat run scripts/deploy.js --network sepolia
   ```
3. Save deployed addresses inside `contracts/deployed_adr`.

### Token Purchase Flow
- User sends ETH to presale contract.
- Contract calculates allocated tokens.
- tokens transferred to user’s wallet.

### Admin Functions
- Withdraw ETH raised during presale.
- Close presale after end time.
- Optionally burn unsold tokens.

---

## 🧑‍💻 Developer Guide

- **Add a new network:** Update `hardhat.config.js` with RPC + private key.  
- **Change presale parameters:** Modify `token_presale.sol` constants (e.g., rate, cap).  
- **Redeploy contracts:** Run deploy script and update `.env` + `deployed_adr`.  
- **Integrate frontend with new contracts:** Update `.env` with new contract addresses.

---

## 🔐 Security Considerations

- Never expose private keys in `.env` or source control.  
- Use audited libraries (OpenZeppelin).  
- Validate presale math (rate, cap, contributions).  
- Test on testnet (Sepolia/Goerli) before mainnet deployment.  
- Warn users to **only connect via official website**.

---

## 🛠️ Future Roadmap: Staking Platform

Our goal is to **evolve staking into a larger reward platform** after the presale.  

Planned features:
- **Staking Contract**
  - Users can stake tokens for rewards.
  - Multiple staking pools (different lock periods, APYs).
- **Reward Distribution**
  - Stakers earn additional or partner tokens.
- **Frontend Dashboard**
  - Display staked balance, rewards, and APR.
  - Claim/unstake functions.
- **Security**
  - Slashing protection.
  - Audit-ready architecture.

This will allow us to transition from **token distribution** → **long-term ecosystem utility**.

---

## 🤝 Contributing

1. Fork repo  
2. Create feature branch (`git checkout -b feature/my-feature`)  
3. Commit changes (`git commit -m 'Add feature'`)  
4. Push to branch (`git push origin feature/my-feature`)  
5. Open Pull Request

---

## 📄 License

MIT License.  
Smart contracts & frontend are open for use with attribution.
