# AiWA ConsentChain

Secure, blockchain-based logging of West African Language oral submissions using WordPress, GCS, Vault, and Polygon.

## 🔍 Overview
AiWA RecordChain is an auditable, end-to-end pipeline that captures, verifies, and immutably logs audio submissions for the AiWA (Ai West Africa) language preservation project. Built for long-term data integrity and ethical transparency, this system ensures every oral history is:

- Collected via WordPress (Forminator)
- Uploaded to Google Cloud Storage (GCS)
- Hashed (SHA-256) for integrity
- Logged immutably to the Polygon blockchain (Mumbai → Mainnet)
- Secured using HashiCorp Vault for secrets management

All data is cross-linked back to WordPress as a Custom Post Type with associated metadata.

---

## 🧱 Architecture
- **Frontend**: WordPress + Forminator
- **Storage**: Google Cloud Storage (GCS)
- **Blockchain**: Custom Solidity contract deployed to Polygon
- **Secrets**: Managed via HashiCorp Vault (AppRole auth)
- **Plugin**: All custom logic lives in a dedicated WordPress plugin

---

## ✅ Phase 1 Scope (Testnet MVP)
- Deploy MandinkaRecordingLog.sol to Polygon Mumbai
- Trigger contract logging from Forminator hook
- Store SHA-256 hashes + GCS URI + Tx hash in WordPress
- Fetch RPC, GCP, and wallet secrets from Vault via Human Made plugin

---

## 📂 Repository Structure
wp-content/plugins/aiwa-recordchain/ 
├── contracts/ # Solidity contracts (e.g., MandinkaRecordingLog.sol) 
├── src/ 
│ ├── blockchain.php # Web3 calls to Polygon 
│ ├── gcs.php # GCS upload logic 
│ ├── hash.php # SHA-256 hash generation 
│ ├── vault.php # Vault integration 
│ └── form-handler.php # Hook from Forminator submission 
├── cron/ # Tx confirmation polling logic 
├── assets/ 
├── aiwa-recordchain.php # Main plugin loader 
├── README.md 
├── .gitignore 
└── LICENSE.md

---

## 🛡 License

> Ai WEST AFRICA (AiWA) CONFIDENTIAL  
© 2023–2025 Ai West Africa (AiWA), a project of Cellular Vibrations and MaximillianGroup. All Rights Reserved.

See `LICENSE.md` for full terms.

---

## 📄 .gitignore (excerpt)
*.log /vendor/ .env *.zip *.tar.gz node_modules/ .DS_Store .idea/ pycache/ .gcloud/ secrets/

---

## 📦 Requirements
- PHP 8.1+
- WordPress 6.1+
- Composer (for Vault and GCS SDKs)
- Google Cloud project + service account
- Polygon wallet + RPC endpoint (Mumbai for dev)
- HashiCorp Vault (AppRole enabled)

---

## 🧪 Testing Checklist
- [ ] Form submission stores in GCS
- [ ] Hashes generated correctly
- [ ] Transaction sent to testnet contract
- [ ] WordPress CPT updated with all fields
- [ ] Vault integration works end-to-end
- [ ] Cron verifies confirmations and updates post

---

## 🧠 Phase 2 Preview
Once tested, this will migrate to Polygon Mainnet with monitoring, admin dashboards, and transcription integration.

---

## 🤝 Credits
Built by AiWA (Ai West Africa), Cellular Vibrations, and the MaximillianGroup for cultural preservation and decentralized accountability.
