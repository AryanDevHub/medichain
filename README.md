# 🏥 MediChain
### Secure, Decentralized Medical Record Management

**Team Name:** Quarks  
**Project:** MediChain

---

## 📢 Hackathon Submission Materials

To aid the judging process, we have included the following detailed resources:

### 📄 Project Documentation
For a complete breakdown of the problem statement, architectural details, and submission template compliance, please refer to the included PDF:
👉 **[our_submission.pdf](https://drive.google.com/drive/folders/1tWFOkjE9jnOu70TwGnj-AVD6y0t1CROp)**

### 🎥 Explanation Video
Watch our project walkthrough and demonstration here:
👉 **[Google Drive Link - Explanation Video & System Architecture ](https://drive.google.com/drive/folders/1_a4GiUxsLlO2gi95td_MdHxrBX5A5Kec?usp=sharing)**

---

## 💡 Project Overview

**MediChain** is a decentralized electronic health record (EHR) system designed to give patients absolute sovereignty over their medical data. By leveraging **Blockchain technology**, **IPFS storage**, and **AES-256 encryption**, we ensure that sensitive medical records are:

1.  **Tamper-Proof:** Cryptographic hashing ensures records cannot be altered without detection.
2.  **Patient-Controlled:** Patients explicitly grant and revoke access to doctors via smart contracts.
3.  **Secure:** Files are encrypted before leaving the client-side environment.
4.  **Decentralized:** No single point of failure for file storage.

---

## 🌟 Key Features

*   **Role-Based Portals:** Distinct dashboards for **Patients** (manage access, view history) and **Doctors** (upload records, verify integrity).
*   **Smart Access Control:** Access permissions are stored on the Ethereum blockchain. A doctor cannot view or upload records without a transaction signed by the patient.
*   **Hybrid Storage Architecture:** 
    *   **Blockchain:** Stores access logic and file hashes (metadata).
    *   **IPFS (Pinata):** Stores the actual encrypted files.
    *   **SQL (Django):** Caches user metadata for fast retrieval.
*   **Integrity Verification:** The system automatically compares the hash of the downloaded file against the immutable hash stored on the blockchain to detect tampering.
*   **Encryption Microservice:** A dedicated Python/FastAPI service handles AES-256 encryption and decryption isolated from the main application logic.

---

## 🏗️ Tech Stack

*   **Frontend:** React (Vite), Ethers.js, Tailwind/CSS
*   **Backend:** Django REST Framework (Python)
*   **Blockchain:** Solidity, Hardhat, Ethereum (Sepolia Testnet)
*   **Encryption:** FastAPI, PyCryptodome
*   **Storage:** IPFS (via Pinata SDK)

---

## 🚀 Getting Started

### Prerequisites
*   Node.js & npm
*   Python 3.8+
*   MetaMask Browser Extension (connected to Sepolia Testnet)

### 1. Environment Configuration
Copy the example environment file and fill in your API keys:
```bash
cp .env.example .env
```
*You will need API keys for Pinata (IPFS), Alchemy/Infura (RPC URL), and a Testnet Private Key.*

### 2. Automatic Startup (Windows)
We have provided a script to launch all services (Encryption, Backend, Frontend) simultaneously:

Double-click **`start-all.bat`** in the root directory.

### 3. Manual Startup
If you prefer to run services individually:

**Terminal 1: Encryption Service**
```bash
cd encryption_service
python -m venv venv
venv\Scripts\activate
uvicorn main:app --reload --port 8001
```

**Terminal 2: Django Backend**
```bash
cd backend
python -m venv venv
venv\Scripts\activate
python manage.py runserver 0.0.0.0:8002
```

**Terminal 3: React Frontend**
```bash
cd frontend
npm install
npm run dev
```

### 4. Health Check
Run the included PowerShell script to verify all systems are operational:
```powershell
.\health-check.ps1
```

---

## 📱 Usage Guide

### Patient Flow
1.  **Login:** Connect MetaMask and select "Patient".
2.  **Grant Access:** Navigate to "Access Control", enter a Doctor's wallet address, and confirm the transaction.
3.  **View Records:** See a timeline of records uploaded by authorized doctors.

### Doctor Flow
1.  **Login:** Connect MetaMask and select "Doctor".
2.  **Upload Record:** 
    *   Enter the Patient's wallet address.
    *   Select a file.
    *   Click "Upload & Encrypt".
    *   *Note: This will fail if the patient has not granted you access.*
3.  **Verify:** Search for a patient to view their history and verify file integrity against the blockchain.

---

## 📁 Directory Structure

```
saidhury-medichain/
├── backend/              # Django API (User database & metadata)
├── blockchain/           # Smart Contracts & Hardhat config
├── encryption_service/   # Microservice for AES encryption
├── frontend/             # React UI & Web3 integration
├── our_submission.pdf    # HACKATHON SUBMISSION DOCUMENT
└── start-all.bat         # One-click startup script
```

---

## ⚠️ Troubleshooting

*   **MetaMask Connection:** Ensure you are on the **Sepolia** network.
*   **"User not found":** The system auto-registers users upon first login. If issues persist, refresh the page.
*   **Upload Errors:** Check your Pinata API keys in `.env` and ensure you have storage quota available.

---

**Built with ❤️ by Team Quarks**
