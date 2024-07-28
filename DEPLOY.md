# TASK 1

### Deploy Contrack 

Buat file .sh "swisstronik-deploy.sh" :

```
nano swisstronik-deploy.sh

```
pastekan scrip berikut :

```
#!/bin/bash

# Ensure script stops if there is an error
set -e

# Install dependencies
npm install --save-dev @nomicfoundation/hardhat-toolbox
npm install dotenv

# Initialize Hardhat project
npx hardhat

# Create hardhat.config.js with network settings
cat <<EOL > hardhat.config.js
require("@nomicfoundation/hardhat-toolbox");
require("dotenv").config();

module.exports = {
  solidity: "0.8.19",
  networks: {
    swisstronik: {
      url: "https://json-rpc.testnet.swisstronik.com/",
      accounts: [\`0x\${process.env.PRIVATE_KEY}\`],
    },
  },
};
EOL

# Create .env file
cat <<EOL > .env
PRIVATE_KEY=your-private-key-here
EOL

# Create Hello_swtr.sol contract
mkdir -p contracts
cat <<EOL > contracts/Hello_swtr.sol
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.19;

contract Swisstronik {
    string private message;

    constructor(string memory _message) payable {
        message = _message;
    }

    function setMessage(string memory _message) public {
        message = _message;
    }

    function getMessage() public view returns (string memory) {
        return message;
    }
}
EOL

# Compile the contract
npx hardhat compile

# Create deployment script
mkdir -p scripts
cat <<EOL > scripts/deploy.js
const hre = require("hardhat");

async function main() {
  const contract = await hre.ethers.deployContract("Swisstronik", ["Hello Swisstronik!!"]);
  await contract.waitForDeployment();
  console.log(\`Swisstronik contract deployed to \${contract.target}\`);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
EOL

# Deploy the contract
npx hardhat run scripts/deploy.js --network swisstronik

# Create setMessage script
cat <<EOL > scripts/setMessage.js
const hre = require("hardhat");
const { encryptDataField } = require("@swisstronik/utils");

const sendShieldedTransaction = async (signer, destination, data, value) => {
  const rpclink = hre.network.config.url;
  const [encryptedData] = await encryptDataField(rpclink, data);
  return await signer.sendTransaction({
    from: signer.address,
    to: destination,
    data: encryptedData,
    value,
  });
};

async function main() {
  const contractAddress = "0xf84Df872D385997aBc28E3f07A2E3cd707c9698a";
  const [signer] = await hre.ethers.getSigners();
  const contractFactory = await hre.ethers.getContractFactory("Swisstronik");
  const contract = contractFactory.attach(contractAddress);
  const functionName = "setMessage";
  const messageToSet = "Hello Swisstronik!!";
  const setMessageTx = await sendShieldedTransaction(signer, contractAddress, contract.interface.encodeFunctionData(functionName, [messageToSet]), 0);
  await setMessageTx.wait();
  console.log("Transaction Receipt: ", setMessageTx);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
EOL

# Create getMessage script
cat <<EOL > scripts/getMessage.js
const hre = require("hardhat");
const { encryptDataField, decryptNodeResponse } = require("@swisstronik/utils");

const sendShieldedQuery = async (provider, destination, data) => {
  const rpclink = hre.network.config.url;
  const [encryptedData, usedEncryptedKey] = await encryptDataField(rpclink, data);
  const response = await provider.call({
    to: destination,
    data: encryptedData,
  });
  return await decryptNodeResponse(rpclink, response, usedEncryptedKey);
};

async function main() {
  const contractAddress = "0xf84Df872D385997aBc28E3f07A2E3cd707c9698a";
  const [signer] = await hre.ethers.getSigners();
  const contractFactory = await hre.ethers.getContractFactory("Swisstronik");
  const contract = contractFactory.attach(contractAddress);
  const functionName = "getMessage";
  const responseMessage = await sendShieldedQuery(signer.provider, contractAddress, contract.interface.encodeFunctionData(functionName));
  console.log("Decoded response:", contract.interface.decodeFunctionResult(functionName, responseMessage)[0]);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
EOL

# Run setMessage script
npx hardhat run scripts/setMessage.js --network swisstronik

# Run getMessage script
npx hardhat run scripts/getMessage.js --network swisstronik

echo "All steps completed successfully."

```

simpan dan lanjut CTRL-X lalu Y Kemudian ENTER

```
chmod +x swisstronik-deploy.sh

```

```
./swisstronik-deploy.sh

```

Tunggu Sampai Selesai "SIMPAN CONTRACK DAN HAS nya"

### Buat Repositori di github dan Upload semua File 
### DONE
