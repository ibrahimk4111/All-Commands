# All-Commands
[04](#tailwindcss)

## 01.New Repository command
```
git init
git add README.md
git commit -m "comment"
git branch -M main
git remote add origin https://github.com/ibrahimk4111/<your repo name>.git
git push -u origin main
```

## 02.Push to repo
```
git remote add origin https://github.com/ibrahimk4111/<your repo name>.git
git branch -M main
git push -u origin main
```

## 03.React App deployment on github
#### step-1 : 
`First of all push your code on github successfully.`

#### step-2 :
After that Open the VSCODE terminal:
`npm install gh-pages --save-dev`

#### step-3 :
Open 'package.json' file and write :
``` 
           "homepage": "https://{User Name}.github.io/{App Name}"
            
            "scripts": {
                "predeploy": "npm run build",
                "deploy": "gh-pages -d build",
                }
```         
#### step-4 :
`npm run deploy`

#### step-5 :
Then go to your github Repository :
`setting -> pages`

#### step-6 :
`Click on available link there`



## 04.React + vite App deployment on github

#### step-1: Setup base on vite.config :
`base: "/[REPO_NAME]/"`

#### step-2: Create .github/workflows/deploy.yml and add the code bellow :
```
name: Deploy

on:
  push:
    branches:
      - main

jobs:
  build:
    name: Build
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repo
        uses: actions/checkout@v2

      - name: Setup Node
        uses: actions/setup-node@v1
        with:
          node-version: 16

      - name: Install dependencies
        uses: bahmutov/npm-install@v1

      - name: Build project
        run: npm run build

      - name: Upload production-ready build files
        uses: actions/upload-artifact@v2
        with:
          name: production-files
          path: ./dist

  deploy:
    name: Deploy
    needs: build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'

    steps:
      - name: Download artifact
        uses: actions/download-artifact@v2
        with:
          name: production-files
          path: ./dist

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

#### step-3: Push
```
git add . 
git commit -m "deploy workflow" 
git push
```

#### 04. Active workflow
```
-> Config -> Actions -> General -> Workflow permissions -> Read and Write permissions 
-> Actions -> failed deploy -> re-run-job failed jobs 
-> Pages -> gh-pages -> save
```

## TailwindCSS
#### Step 1: open terminal to install
`npm install -D tailwindcss postcss autoprefixer`

#### Step 2: 
`npx tailwindcss init -p`

#### Step 3: go to 'tailwind.config.js' and paste below code
```
/** @type {import('tailwindcss').Config} */

export default {
  content: ["./index.html",
  "./src/**/*.{js,ts,jsx,tsx}",],
  theme: {
    extend: {},
  },
  plugins: [],
}
```
