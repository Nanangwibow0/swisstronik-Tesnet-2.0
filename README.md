# SWISSTRONIK-TESNET-2.0

gunakan CODESPACE Untuk Menyelesaikan Task : https://github.com/codespaces

### Eror Saat Push REPOSITORY 

```
git config --global user.name "username-github"
git config --global user.email "email-gihub"
```

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
salin ssh key yang di tampilkan lalu buka github " PENGATURAN - GPKEY " buat GPKEY Baru pastekan lalu simpan

Jalankan :

```
git remote set-url origin git@github.com:<username-github>/<repository-github>
```
```
git push -u origin main
```
### DONE
