# Deployment Plan (Heroku)

## 1) Thong tin credentials can thiet
- GitHub Token: (dat trong GitHub Secrets)
- HEROKU_API_KEY: (dat trong GitHub Secrets)
- Repo target: ngapngap/CLIProxyAPIPlus

## 2) Cac buoc can thuc hien
1. Clone repo fork ve local.
2. Kiem tra workflow file `.github/workflows/sync-and-deploy.yml` da ton tai.
3. Them GitHub Secrets qua API hoac GitHub CLI:
   - HEROKU_API_KEY
   - HEROKU_EMAIL (can hoi user)
4. Push cac thay doi neu can.

## 3) Cach them secrets qua GitHub API
```bash
# Lay public key
curl -H "Authorization: token ghp_..." \
  https://api.github.com/repos/ngapngap/CLIProxyAPIPlus/actions/secrets/public-key

# Ma hoa secret bang libsodium (Python hoac Node.js)
# PUT secret len GitHub
```

## 4) Cach dung GitHub CLI (neu da cai)
```bash
gh auth login --with-token < token.txt
gh secret set HEROKU_API_KEY --repo ngapngap/CLIProxyAPIPlus
gh secret set HEROKU_EMAIL --repo ngapngap/CLIProxyAPIPlus
```

## 5) Workflow file can co noi dung
- Sync voi upstream
- Build va deploy len Heroku

## Luu y
- File nay se duoc dung lam tai lieu huong dan khi trien khai tren repo fork moi.
- Chi tao file nay, khong thuc hien cac lenh khac.
