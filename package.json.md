{
  "name": "death-project",
  "version": "1.0.0",
  "description": "Degens Enraged Against The Hoaxes - Blockchain Fraud Detection Ecosystem",
  "main": "backend/index.js",
  "scripts": {
    "start": "node backend/index.js",
    "frontend": "cd death-project && npm start",
    "install-all": "npm install && cd death-project && npm install"
  },
  "dependencies": {
    "express": "^4.18.2",
    "cors": "^2.8.5",
    "web3": "^4.3.0",
    "llama-index": "^0.0.32",
    "dotenv": "^16.3.1"
  },
  "devDependencies": {
    "hardhat": "^2.19.1",
    "@nomicfoundation/hardhat-toolbox": "^4.0.0"
  }
}
