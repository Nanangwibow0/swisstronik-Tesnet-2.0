# Task 6

### Deploy Proxy

* Clone Repository

```bash
git clone https://github.com/Nanangwibow0/Deploy-Proxy.git
cd swisstronik-deploy-proxy
```

* Install Dependency

```bash
npm install
```

* .env File

buat .env

```bash
touch .env
```

Tambahkan Private key

```bash
PRIVATE_KEY="your private key"
```

* Compile Smart Contract

```bash
npm run compile
```

### Jalankan

```bash
npm run deploy
npm run initialize
npm run add-issuers
npm run list-issuers
npm run upgrade
```
