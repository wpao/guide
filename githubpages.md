note :
project ini di buat menggunakan vite, react-ts, tailwindcss

# membuat githubPages
## langkah 1
pilih project yang akan di push
edit file vite.config.ts tambahkan base
```
export default defineConfig({
  plugins: [tailwindcss(), react()],

  // Konfigurasi base untuk GitHub Pages
  base: "/wedding04-pages/",
});
```
## langkah 2
tambahkan package
```
pnpm add -D gh-pages
```
tambahkan pada file package.json
```
"scripts": {
    "deploy": "gh-pages -d dist"
  },
```

## langkah 3
## silahkan buka github

- buat repo private
```
wedding04 // contoh nama
// Choose visibility to private
```

- buat repo public
```
wedding04-pages // contoh nama
Choose visibility to public 
Checklist Add README to TRUE
```

- buat token
```
TOKEN_WEDDING_04 // contoh nama
```

- buat secrets
secrets -> token
```
SECRETS_WEDDING_04 // contoh nama
```

## -
buat file sebagai berikut (sejajar dengan src)
.github/workflows/deploy.yml
```base
name: Deploy Vite to GitHub Pages (Private → Public)

on:
  push:
    branches:
      - master

permissions:
  contents: write

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout source code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Setup pnpm
        uses: pnpm/action-setup@v4
        with:
          version: 9

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: pnpm

      - name: Install dependencies
        run: pnpm install --frozen-lockfile

      - name: Build project
        run: pnpm run build

      - name: Deploy to public repo
        uses: peaceiris/actions-gh-pages@v4
        with:
          personal_token: ${{ secrets.WEDDING_04_SECRET }}
          external_repository: wpao/wedding04-pages
          publish_branch: gh-pages
          publish_dir: ./dist
          enable_jekyll: false
```


## langkah 5
```base
git commit -am 'comment'
git push
pnpm run build
pnpm run deploy
```
# jika menggunakan react router
perhatikan baseURL nya
