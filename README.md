# All commands

|Front end|repos|
|-----|------|
|01. [New Repository command](#01_New_Repository_command)|[Responsive Navbar](https://github.com/ibrahimk4111/Responsive_nav_bar)|
|02. [React App Deployment on Github](#02_React_App_Deployment_on_Github)|
|03. [React Vite App Deployment on Github](#03_React_Vite_App_Deployment_on_Github)|
|04. [TailwindCSS Installation in Vite Project](#04_TailwindCSS_Installation_on_React_Vite_App)|
|04. [Mongoose + NodeJs + Express app Deploy on render](#05_Mongoose_NodeJs_Express_app_Deploy_on_render)|

## 01_New_Repository_Command

           git init
           git add README.md
           git commit -m "comment"
           git branch -M main
           git remote add origin https://github.com/ibrahimk4111/<your repo name>.git
           git push -u origin main

[back to top](#All-commands-and-Projects-demo)


## 02_React_App_Deployment_on_Github
##### step-1 : 
           First of all push your code on github successfully.

##### step-2 : After that Open the VSCODE terminal:
           npm install gh-pages --save-dev

##### step-3 : Open 'package.json' file and write :
          
           "homepage": "https://{User Name}.github.io/{App Name}"
                       
           "scripts": {
           "predeploy": "npm run build",
           "deploy": "gh-pages -d build",
           }
           
##### step-4 : npm run deploy

#### step-5 : Then go to your github Repository :
           setting -> pages

##### step-6 : Click on available link there

[back to top](#All-commands-and-Projects-demo)


## 03_React_Vite_App_Deployment_on_Github

#### step-1: Setup base on vite.config :
           base: "/[REPO_NAME]/"

#### step-2: Create .github/workflows/deploy.yml and add the code bellow :
           
           # Simple workflow for deploying static content to GitHub Pages
           name: deploy
           
           on:
             push:
               branches: ['main']
           
             # Allows you to run this workflow manually from the Actions tab
             workflow_dispatch:
           
           # Sets the GITHUB_TOKEN permissions to allow deployment to GitHub Pages
           permissions:
             contents: read
             pages: write
             id-token: write
           
           # Allow one concurrent deployment
           concurrency:
             group: 'pages'
             cancel-in-progress: true
           
           jobs:
             # Single deploy job since we're just deploying
             deploy:
               environment:
                 name: github-pages
                 url: ${{ steps.deployment.outputs.page_url }}
               runs-on: ubuntu-latest
               steps:
                 - name: Checkout
                   uses: actions/checkout@v4
                 - name: Set up Node
                   uses: actions/setup-node@v3
                   with:
                     node-version: 18
                     cache: 'npm'
                 - name: Install dependencies
                   run: npm install
                 - name: Build
                   run: npm run build
                 - name: Setup Pages
                   uses: actions/configure-pages@v3
                 - name: Upload artifact
                   uses: actions/upload-pages-artifact@v2
                   with:
                     # Upload dist repository
                     path: './dist'
                 - name: Deploy to GitHub Pages
                   id: deployment
                   uses: actions/deploy-pages@v2
           

#### step-3: Push
           
           git add . 
           git commit -m "deploy workflow" 
           git push
           
#### 04. Active workflow
           
           * Config -> Actions -> General -> Workflow permissions -> Read and Write permissions
           * Actions -> failed deploy -> re-run-job failed jobs 
           * Pages -> gh-pages -> save
           
[back to top](#All-commands-and-Projects-demo)

## 04_TailwindCSS_Installation_on_React_Vite_App
#### Step 1: open terminal to install
           npm install -D tailwindcss postcss autoprefixer

#### Step 2: 
           npx tailwindcss init -p

#### Step 3: go to 'tailwind.config.js' and paste below code
           
           /** @type {import('tailwindcss').Config} */
           
           export default {
             content: ["./index.html",
             "./src/**/*.{js,ts,jsx,tsx}",],
             theme: {
               extend: {},
             },
             plugins: [],
           }
           
[back to top](#All-commands-and-Projects-demo)

## 05_Mongoose_NodeJs_Express_app_Deploy_on_render
           
   #### step 1: 
           connect to the github repo
           
   #### step 2: 
           set Environment key and value same as your .env file contains

[back to top](#All-commands-and-Projects-demo)
