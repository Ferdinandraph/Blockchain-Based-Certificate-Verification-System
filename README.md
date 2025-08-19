FUTO Blockchain-Based Certificate Verification System
This project is a decentralized platform for issuing, managing, and verifying academic certificates for the Federal University of Technology, Owerri (FUTO) using Ethereum's Sepolia testnet. It enables the FUTO Senate to issue secure, tamper-proof certificates, allows graduates to view and share them, and permits third parties (e.g., employers) to verify their authenticity, addressing challenges in traditional certificate systems like fraud, inefficiency, and inaccessibility.
Table of Contents

Overview
Core Problems Addressed
Features
Technology Stack
System Workflow
User Interfaces
Login Page
Issuer Dashboard (FUTO Senate)
Recipient Dashboard (FUTO Graduate)
Verifier Dashboard (Third Parties)
Signup Page (Verifiers Only)


Actors and Functionalities
Setup Instructions
Future Enhancements
Contributing
License

Overview
The FUTO Certificate Verification System leverages blockchain technology to issue, manage, and verify academic certificates securely. Built on Ethereum's Sepolia testnet, it ensures:

Tamper-Proof Records: Certificates are stored as cryptographic hashes on the blockchain, preventing fraud.
Accessibility: Graduates access certificates via a simple digital wallet, no complex credentials needed.
Transparency: Third parties verify certificates instantly using blockchain data.
Efficiency: Smart contracts automate issuance and verification, reducing manual processes.

This demo uses fake data and Sepolia testnet for zero-cost testing, with potential for real-world deployment.
Core Problems Addressed

Fraud and Forgery: Traditional certificates are prone to manipulation; blockchain ensures immutability.
High Costs and Delays: Manual verification processes are slow and costly; automation via smart contracts speeds up operations.
Exclusion of Stakeholders: Graduates without physical access to FUTO can view/share certificates; verifiers access globally.
Lack of Transparency: Centralized records lack auditability; blockchain logs are public and verifiable.

Features

Smart Contracts: Automate certificate issuance, verification, and revocation on Ethereum Sepolia.
Digital Identity: MetaMask wallet for secure, user-friendly access (no bank accounts or IDs needed).
Decentralized Verification: Third parties verify certificates directly via blockchain.
User-Friendly DApp: Responsive web interface mimicking familiar apps, with FUTO green/white gradient.
Admin Oversight: FUTO Senate manages certificates via a secure dashboard.

Technology Stack

Frontend: React.js, Tailwind CSS (CDN-hosted via cdn.jsdelivr.net), JSX components, single-page app.
Backend: Node.js, Express.js (RESTful API), MongoDB (certificate metadata), JWT for authentication.
Blockchain: Ethereum Sepolia testnet, Hardhat for smart contract development, Web3.js/Ethers.js for interaction, MetaMask for transactions (funded via Sepolia faucet).
Database: MongoDB for storing issuer, recipient, verifier, and certificate metadata.
Security: Bcrypt for password hashing, JWT for secure authentication.

System Workflow

Issuer (FUTO Senate):
Logs in with pre-created credentials.
Issues certificates by uploading details and signing via MetaMask.
Smart contract generates a SHA-256 hash, stores it on Sepolia, and saves metadata in MongoDB.
Manages/revokes certificates via dashboard.


Recipient (Graduate):
Logs in using JAMB number.
Views/downloads/shares certificates; checks blockchain-verified status.


** verifier (Third Party)**:
Signs up or logs in with email/password.
Verifies certificates by ID/link, with blockchain confirming validity.


Blockchain Integration:
Smart contracts handle issuance, verification, and revocation.
All actions are logged immutably, ensuring transparency.



User Interfaces
Login Page

Purpose: Authenticate users (Issuers, Recipients, Verifiers).
Components:
Dropdown: Select role (Issuer, Recipient, Verifier).
Username/Email: Username (Issuers), JAMB number (Recipients), email (Verifiers).
Password: Custom (Issuers/Verifiers), JAMB number (Recipients).
Buttons: "Login", "Sign Up" (Verifiers), "Forgot Password" (Verifiers).


Flow: Redirects to respective dashboards after JWT-based authentication.
Design: FUTO green/white gradient, responsive, FUTO logo.

Issuer Dashboard (FUTO Senate)

Purpose: Issue and manage certificates.
Components:
Navigation: Home, Issue Certificate, Manage Certificates, Profile Settings, Logout.
Issue Certificate: Form for Recipient Name, Matric No., Program, Graduation Date, File Upload; "Submit" triggers MetaMask signing, stores hash on Sepolia.
Manage Certificates: Table with Certificate ID, Recipient Name, Issue Date, Status; search by ID/Name; revoke option.
Profile Settings: View Name, Username, Email, Department, Senate Role.


Backend: Pre-loaded issuer data in MongoDB (hashed passwords); smart contract for issuance/revocation.
Design: Clean, green/white gradient, intuitive layout.

Recipient Dashboard (FUTO Graduate)

Purpose: View and share certificates.
Components:
Navigation: My Certificates, Profile Settings, Logout.
My Certificates: List with Certificate ID, Program, Issue Date; details show Issuer, Program, Date, Status (Green "Verified"/Red "Not Verified").
Buttons: "Download" (from MongoDB), "Share" (link).
Profile Settings: View Name, JAMB Number, Program.


Backend: JAMB number login (no hashing); MongoDB for certificate data; Sepolia for status verification.
Design: Student-friendly, green/white gradient.

Verifier Dashboard (Third Parties)

Purpose: Verify certificate authenticity.
Components:
Navigation: Verify Certificate, Profile Settings, Logout.
Verify Certificate: Input Certificate ID/link; "Verify" shows Issuer, Recipient, Program, Date, Status (Green "Valid"/Red "Invalid").
Profile Settings: Update Name, Organization, Email, Password.


Backend: Email/password login (Bcrypt-hashed); Sepolia contract for verification; MongoDB for profiles.
Design: Minimalist, green/white gradient.

Signup Page (Verifiers Only)

Purpose: Register third-party verifiers.
Components:
Fields: Email, Password, Confirm Password, Organization (optional).
Buttons: "Sign Up", "Back to Login".


Flow: Validates inputs, stores hashed password in MongoDB, redirects to dashboard.
Design: Simple, green/white gradient.

Actors and Functionalities



Actor
Functionalities



Issuer
Issue, manage, revoke certificates on blockchain.


Recipient
View, download, share certificates; check status.


Verifier
Verify certificates via blockchain; manage profile.


Setup Instructions

Clone Repository:git clone https://github.com/yourusername/futo-certificate-system.git
cd futo-certificate-system


Install Dependencies:
Backend: npm install (Node.js, Express.js, MongoDB, Web3.js/Ethers.js).
Frontend: React dependencies via CDN (no local install needed).
Blockchain: Install Hardhat (npm install --save-dev hardhat).


Configure Environment:
Create .env file with:MONGODB_URI=mongodb://localhost:27017/futo-certificates
JWT_SECRET=your_jwt_secret
ETHEREUM_PROVIDER=https://sepolia.infura.io/v3/your_infura_key


Set up MongoDB locally or via Atlas.


Deploy Smart Contract:
Use Hardhat to compile and deploy to Sepolia testnet.
Fund MetaMask wallet with Sepolia ETH (via faucet).
Update contract address in frontend/backend.


Run Application:
Backend: npm run start (runs Node.js/Express server).
Frontend: Host index.html via static server (e.g., npx serve).


Test:
Access DApp in browser, connect MetaMask.
Test login, issuance, viewing, and verification flows.



Future Enhancements

Integrate real-world Ethereum mainnet for production.
Add Nigerian payment gateways (e.g., Flutterwave) for certificate issuance fees.
Implement offline access for rural users via cached DApp.
Expand to other universities or document types (e.g., transcripts).

Contributing
Contributions are welcome! Please:

Fork the repository.
Create a feature branch (git checkout -b feature/your-feature).
Commit changes (git commit -m "Add your feature").
Push to branch (git push origin feature/your-feature).
Open a pull request.

License
This project is licensed under the MIT License. See LICENSE for details.
