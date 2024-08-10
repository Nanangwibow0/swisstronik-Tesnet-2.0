# TASK 5
### Deploy Private NFT

### Install
* Clone Repository
```bash
git clone https://github.com/Nanangwibow0/Deploy-Private-NFT.git
cd swisstronik-deploy-private-nft
```
* Install Dependency

```bash
npm install
```

* Set .env
  
```bash
touch .env
```
* Tambahkan PrivatE Key
```bash
PRIVATE_KEY="your private key"
```

### Update Smart Contract
Ubah Sesuai Keinginan
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract PrivateNFT is ERC721, Ownable {
    uint256 private _currentTokenId = 0;

    event NFTMinted(address recipient, uint256 tokenId);
    event NFTBurned(uint256 tokenId);

    constructor(address initialOwner) ERC721("Nama NFT", "Symbol") Ownable(initialOwner) {}

    function mintNFT(address recipient) public onlyOwner returns (uint256) {
        _currentTokenId += 1;
        uint256 newItemId = _currentTokenId;
        _mint(recipient, newItemId);

        emit NFTMinted(recipient, newItemId);
        return newItemId;
    }

    function burnNFT(uint256 tokenId) public {
        require(ownerOf(tokenId) == msg.sender, "Error: You're not owner");
        _burn(tokenId);
        emit NFTBurned(tokenId);

    }

    function balanceOf(address account) public view override returns (uint256) {
        require(msg.sender == account, "Error: You're not owner");
        return super.balanceOf(account);
    }
}

```
* Compile

```bash
npm run compile
```

### Jalankan
```bash
npm run deploy
npm run mint
```

### Upload File Ke Repository Github

# DONE
