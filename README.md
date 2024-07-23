# pepetoken
new smart
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract PepeToken is ERC20, Ownable {
    constructor(uint256 initialSupply) ERC20("PepeToken", "PEPE") {
        _mint(msg.sender, initialSupply);
    }
}
npm install @openzeppelin/contracts
mkdir pepe-token-project
cd pepe-token-project
npx hardhat
require("@nomiclabs/hardhat-waffle");

module.exports = {
  solidity: "0.8.0",
  networks: {
    ropsten: {
      url: "https://ropsten.infura.io/v3/YOUR_INFURA_PROJECT_ID", // Замените на ваш URL Infura
      accounts: ["0xYOUR_PRIVATE_KEY"] // Замените на ваш приватный ключ
    }
  }
};
// scripts/deploy.js
async function main() {
  const [deployer] = await ethers.getSigners();

  console.log("Deploying contracts with the account:", deployer.address);

  const initialSupply = ethers.utils.parseUnits("1000000", 18); // 1,000,000 PEPE with 18 decimals
  const PepeToken = await ethers.getContractFactory("PepeToken");
  const pepeToken = await PepeToken.deploy(initialSupply);

  console.log("PepeToken deployed to:", pepeToken.address);
}

main()
  .then(() => process.exit(0))
  .catch(error => {
    console.error(error);
    process.exit(1);
  });
npx hardhat run scripts/deploy.js --network ropsten
