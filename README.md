# SWISSTRONIK-TESNET-2.0

gunakan CODESPACE Untuk Menyelesaikan Task : https://github.com/codespaces

# NOTE :

### HAPUS File .env & .sh sebelum Upload ke Repository Github

# GASKEN

### [TASK 1](https://github.com/Nanangwibow0/Tutor-swisstronik/blob/main/DEPLOY.md)
### [TASK 2](https://github.com/Nanangwibow0/Tutor-swisstronik/blob/main/MINT-100-ERC-20.md)
### [TASK 3](https://github.com/Nanangwibow0/Tutor-swisstronik/blob/main/MintERC721.md)
### [TASK 4](https://github.com/Nanangwibow0/Tutor-swisstronik/blob/main/PERC-20.md)

### Eror Saat Push REPOSITORY 

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
salin ssh key yang di tampilkan lalu buka github " PENGATURAN - GPG Key " buat GPG-Key Baru pastekan lalu simpan

Jalankan :

```
git remote set-url origin git@github.com:<username-github>/<repository-github>
```
```
git push -u origin main
```
### DONE
