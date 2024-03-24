# All_commands

|Commands|Repositories|Live Demos|
|------|------|------|
|* [My VsCode Setting](#My_VSCode_Setting)|
|01. [New Repository command](#01_New_Repository_command)|[Responsive Navbar](https://github.com/ibrahimk4111/Responsive_nav_bar)|
|02. [React App Deployment on Github](#02_React_App_Deployment_on_Github)|[Arifs BD Ltd](https://github.com/ibrahimk4111/arifsbd)|
|03. [React Vite App Deployment on Github](#03_React_Vite_App_Deployment_on_Github)|[Currency Converter](https://github.com/ibrahimk4111/currency_converter)
|04. [TailwindCSS Installation in Vite Project](#04_TailwindCSS_Installation_on_React_Vite_App)|
|05. [Mongoose + NodeJs + Express app Deploy on render](#05_Mongoose_NodeJs_Express_app_Deploy_on_render)|[Mongoose + Express](https://github.com/ibrahimk4111/mongo_express)
|06. [tailwind css container customise](#06_tailwind_css_container_customise)|

## 01_New_Repository_Command

           git init
           git add README.md
           git commit -m "comment"
           git branch -M main
           git remote add origin https://github.com/ibrahimk4111/<your repo name>.git
           git push -u origin main

[back to top](#All_commands)


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

[back to top](#All_commands)


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
           
[back to top](#All_commands)

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
           
[back to top](#All_commands)

## 05_Mongoose_NodeJs_Express_app_Deploy_on_render
           
   #### step 1: 
           connect to the github repo
           
   #### step 2: 
           set Environment key and value same as your .env file contains

[back to top](#All_commands)

## 06_tailwind_css_container_customise
           
   ```
           theme: {
               container: {
                 center: true,
                 padding: "1rem",
                 screens: {
                   sm: "100%",
                   md: "80%",
                   lg: "900px",
                   xl: "1050px",
                   xxl: "1150px",
                 },
               },
           }

```
[back to top](#All_commands)

## My_VSCode_Setting

```
{
  "files.autoSave": "onWindowChange",
  "editor.linkedEditing": true,
  "css.lint.unknownAtRules": "ignore",
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript]": {
    "editor.defaultFormatter": "vscode.typescript-language-features"
  },
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "workbench.iconTheme": "material-icon-theme",
  "editor.showUnused": false,
  "javascript.updateImportsOnFileMove.enabled": "always",
  "workbench.editorAssociations": {
    "*.sqlite3": "default"
  },
  "editor.mouseWheelZoom": true,
  "workbench.list.mouseWheelScrollSensitivity": 0.5,
  "screencastMode.mouseIndicatorSize": 100,
  "html.format.templating": true,
  "files.associations": {
    "**/templates/*.html": "django-html",
    "**/templates/*": "django-txt",
    "**/requirements{/**,*}.{txt,in}": "pip-requirements",
    "*.html": "html"
  },
  "emmet.includeLanguages": {
    "django-html": "html",
    "django-css": "css"
  },
  "[django-html]": {
    "editor.quickSuggestions": {
      "other": true,
      "comments": true,
      "strings": true
    }
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "workbench.colorTheme": "SynthWave '84",
}

```

[back to top](#All_commands)
