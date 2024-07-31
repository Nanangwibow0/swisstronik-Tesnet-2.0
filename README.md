# SWISSTRONIK-TESNET-2.0
Web Tesnet : [www.swisstronik.com](https://www.swisstronik.com/testnet2/dashboard)

Twitter : [X](https://x.com/swisstronik)

### gunakan [CODESPACE](https://github.com/codespaces) Untuk Menyelesaikan Task !!

### Install Node.js

```
# installs fnm (Fast Node Manager)
curl -fsSL https://fnm.vercel.app/install | bash

# activate fnm
source ~/.bashrc

# download and install Node.js
fnm use --install-if-missing 20

# verifies the right Node.js version is in the environment
node -v # should print `v20.16.0`

# verifies the right npm version is in the environment
npm -v # should print `10.8.1`
```
### Install GIT

```
sudo apt-get install git
git --version
```
# GASKEN

### [TASK 1](https://github.com/Nanangwibow0/swisstronik-Tesnet-2.0/blob/main/DEPLOY.md)
### [TASK 2](https://github.com/Nanangwibow0/Tutor-swisstronik/blob/main/MINT-100-ERC-20.md)
### [TASK 3](https://github.com/Nanangwibow0/Tutor-swisstronik/blob/main/MintERC721.md)
### [TASK 4](https://github.com/Nanangwibow0/Tutor-swisstronik/blob/main/PERC-20.md)


# NOTE :

### HAPUS File .env & .sh sebelum Upload ke Repository Github

# Eror Saat Push REPOSITORY 

```
git config --global user.name "username-github"
git config --global user.email "email-github"
```

Buat SSH-KEY

```
ssh-keygen -t ed25519 -C "email-gihub"

```

```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

```
```
cat ~/.ssh/id_ed25519.pub

```
salin ssh key yang di tampilkan lalu buka github " PENGATURAN - GPG Key " buat GPG-Key Baru, pastekan lalu simpan

Jalankan :

```
git remote set-url origin git@github.com:<username-github>/<repository-github>
```
```
ssh -T git@github.com
```
```
git push -u origin main
```
### DONE
