---
title: "End-to-End DevOps with ESLint, Prettier, Husky, GitHub Actions, CI/CD, and Vercel"
datePublished: Wed Jan 01 2025 11:16:14 GMT+0000 (Coordinated Universal Time)
cuid: cm5dsxidn000g09jr957edyqt
slug: end-to-end-devops-with-eslint-prettier-husky-github-actions-cicd-and-vercel
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1735729968286/45359b56-9118-424e-bf08-8e525f964f7c.png
tags: eslint, nextjs, prettier, ci-cd, github-actions-1, husky, nextjs15

---

1. **Start by creating a new nextjs project**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735701377717/a79b46ea-f954-499b-96e9-73884e69af00.png align="center")
    
2. Now let’s install everything.
    
    ```powershell
     npm install --save-dev prettier eslint-config-prettier husky lint-staged eslint-plugin-prettier
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735703490132/c87d717b-f206-4588-a6a9-34a1fc82e74f.png align="center")
    
3. Now let’s create three files: `.prettierignore`, `.eslintrc.json`, and `.prettierrc`.
    
4. Add this to your `.eslintrc.json`.
    
    ```json
    {
      "extends": ["eslint:recommended", "prettier", "next", "next/core-web-vitals"],
      "plugins": ["prettier"],
      "rules": {
        "prettier/prettier": "error"
      }
    }
    ```
    
5. Add this to your `.prettierignore`.
    
    ```bash
    #Ignore artifacts:
    dist
    .next/
    public/
    build
    
    #Ignore specific files:
    package-lock.json
    ```
    
6. Add this to your `.prettierrc`.
    
    ```json
    {
      "trailingComma": "es5",
      "useTabs": false,
      "tabWidth": 4,
      "semi": true,
      "singleQuote": true,
      "printWidth": 80,
      "bracketSpacing": true
    }
    ```
    
7. Now let's open `package.json` and write some scripts.
    
    ```json
    "scripts": {
            "dev": "next dev",
            "build": "next build",
            "start": "next start",
            "lint": "eslint src --report-unused-disable-directives --max-warnings 0",
            "lint:fix": "eslint src --fix",
            "format": "prettier --write 'src/**/*.{js,jsx,ts,tsx,css,html}'"
    }
    ```
    
8. Now let’s open `eslint.config.js` to tell ESLint that we only want to lint files inside the `src` folder and add `files: ['src/**/*.{ts,tsx,js,jsx}']`. Your ESLint config array will look like this now:
    
    ```json
    const eslintConfig = [
        ...compat.extends('next/core-web-vitals', 'next/typescript'),
        {
            files: ['src/**/*.{ts,tsx,js,jsx}'],
        },
    ];
    ```
    
9. Now let’s push our code to GitHub. The reason I’m doing this is that I want to show you how it will behave before and after configuring Husky.
    
    Here, I’ve created a new GitHub repo and pushed everything there.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735705187049/f2781360-d30a-45d5-ac72-ff7d74123826.png align="center")
    
10. Now add hooks in the `package.json` file in the root directory alongside scripts and dependencies.
    
    ```json
     "husky": {
            "hooks": {
                "pre-commit": "lint-staged",
                "pre-push": "npm run lint && npm run format"
            }
        },
        "lint-staged": {
            "src/**/*.{ts,tsx,js,jsx}": [
                "npm run lint",
                "npm run format"
            ]
    }
    ```
    
11. Now run the `npx husky init` command. It will add a new folder to your project and add a new script to your `package.json`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735705843230/ddf56b5a-058a-4cfb-9e3b-fd82340b1f2a.png align="center")
    
12. Now add `npx lint staged` in your `pre-commit` file like this
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735712530145/e972f12f-5aed-4266-9d10-923b8cd4e147.png align="center")
    
13. Now let’s run `git add .` and `git commit -m '3rd commit'` to check if linting and formatting work.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735712306894/d4956ccf-5625-4cce-a21d-f3c37e5b8e68.png align="center")
    
    Now let’s check by adding an unused variable in `page.tsx` inside the `app` folder to see if our linting works.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735713054891/808f469d-af10-4db0-be06-4ef6a5cf3612.png align="center")
    
    Run `git add .` and `git commit -m 'commit to check linting'` again.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735713208129/6ed53c87-69d4-4110-8809-4723030c8e89.png align="center")
    
    See the error: `a` is assigned but never read, and it is stopping us from committing.
    
    We can run `npm run lint:fix` to fix 90% of the linting errors because we’ve set up a script for that as well.
    
    Now, let’s remove the unused variable and try to commit and push.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735713399548/4f78916a-1c8c-437f-9f24-a8de5a8e7084.png align="center")
    
14. Now, set the commit message policies so that people who push code to your repo follow certain commit message rules.
    
    Install these two packages:
    
    ```powershell
    npm install --save-dev @commitlint/cli
    npm install --save-dev @commitlint/config-conventional
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735714147902/78875854-5674-4ef9-b699-6a3969eaae5c.png align="center")
    
15. Now create a new file in the `.husky` folder and add:
    
    ```powershell
    npx --no-install commitlint --edit "$1"
    ```
    
16. Create a new file `commitlint.config.cjs` in the root of the project and add this to your file:
    
    ```json
    module.exports = {
        // extends: ['@commitlint/config-conventional'],
        extends: [],
        rules: {
          'header-min-length': [2, 'always', 10],
          'header-case-start-capital': [2, 'always'],
          'header-end-period': [2, 'always'],
        },
        plugins: [
          {
            rules: {
              'header-case-start-capital': ({ raw }) => {
                return [
                  /^[A-Z]/.test(raw),
                  'Commit message must start with a capital letter',
                ];
              },
              'header-end-period': ({ header }) => {
                return [/\.$/.test(header), 'Commit message must end with a period'];
              },
            },
          },
        ],
      };
    ```
    
    This will ensure various things, such as: 'commit message must start with a capital letter,' 'should have a length of 10,' and 'ends with a full stop.'
    
17. Now let’s try to push something with a wrong commit message. Make sure you change something inside the `src` folder to trigger the hooks.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735715167693/a4fb7c78-38db-4dd9-b0b8-1674593b1eff.png align="center")
    
    And now, let’s fix the message and see.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735715270671/cc974441-40d2-48a8-bbbe-f60063f4b48c.png align="center")
    
18. Now let’s configure a CI pipeline. Create a `.github` folder and a `workflows` folder inside it. Then, create a `ci.yml` file inside the `workflows` folder.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735716958549/05bcb8ff-ef9b-45ea-a3ee-69001f7fb8a4.png align="center")
    
    Paste this content in the file. You can ask ChatGPT to explain this file to you; it’s quite simple, to be honest.
    
    ```yaml
    name: CI workflow for Blog
    
    on:
        push:
        pull_request:
    
    jobs:
        build:
            runs-on: ubuntu-latest
    
            steps:
                - uses: actions/checkout@v2
                  with:
                      fetch-depth: 0 # Fetch all history for all branches and tags
                - name: Use Node.js
                  uses: actions/setup-node@v2
                  with:
                      node-version: '20.17.0'
    
                - name: Install dependencies
                  run: npm install
    
                - name: Run lint
                  run: npm run lint
    
                - name: Run format check
                  run: npm run format
    
                - name: Check commit messages
                  uses: wagoid/commitlint-github-action@v3
                  with:
                      configFile: commitlint.config.cjs
    ```
    

19. Now let’s test the CI pipeline we’ve created.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735717771205/7e813b47-cf85-4d93-8749-ec5210c71725.png align="center")
    
    And let’s open the Actions tab in the GitHub repo.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735717821703/6e1b973c-3d1a-4133-8613-78efc281d824.png align="center")
    
    We passed all the checks! LFG
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735717998331/b7b7b90c-359d-4ead-8eb5-b1eb155e5107.png align="center")
    
    Let’s try to learn about some warnings here (skip if you want). This wasn’t planned, but let’s address it and maybe upgrade our script according to them.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735718540559/ad603769-0445-427b-aca1-f7e165e50a20.png align="center")
    
    **Warning 1: Ubuntu-latest pipelines will use ubuntu-24.04 soon**
    
    Details: GitHub is planning to update the default `ubuntu-latest` runner to use `ubuntu-24.04`. Currently, it likely uses `ubuntu-22.04`.  
    
    This means that your workflow might soon start using Ubuntu 24.04 instead of the current version.  
    
    **Warning 2: The set-output command is deprecated**
    
    Details: The `set-output` command was previously used in GitHub Actions to pass data between steps.
    
    GitHub has replaced this functionality with environment files, which are more secure and performant.
    
    If your workflow uses an action or script that still relies on `set-output`, it will need to be updated.  
    
    Fixing these using the new file—check code comments for changes.
    
    ```yaml
    name: CI workflow for Blog
    
    on:
        push:
        pull_request:
    
    jobs:
        build:
            runs-on: ubuntu-22.04 #replaced the latest to 22.04
    
            steps:
                - uses: actions/checkout@v4 #updated version
                  with:
                      fetch-depth: 0 
                - name: Use Node.js
                  uses: actions/setup-node@v4 #updated version
                  with:
                      node-version: '20.17.0'
    
                - name: Install dependencies
                  run: npm install
    
                - name: Run lint
                  run: npm run lint
    
                - name: Run format check
                  run: npm run format
    
                - name: Check commit messages
                  uses: wagoid/commitlint-github-action@v6 #updated version
                  with:
                      configFile: commitlint.config.cjs
    ```
    
    So we are done here, and now let’s wrap up this blog by building a CD pipeline.
    
20. Go inside the `workflows` folder and create a new file called `deploy.yml`. In this project, we will deploy to Vercel. Vercel deployment is really easy, but I want to give a sample of how things work here.
    
    ```yaml
    name: CD Pipeline to Vercel
    
    on:
        push:
    
    jobs:
        deploy:
            runs-on: ubuntu-22.04
    
            steps:
                - name: Checkout Repository
                  uses: actions/checkout@v4
    
                - name: Install Vercel CLI
                  run: npm install --global vercel@latest
    
                - name: Pull Vercel Environment Information
                  run: vercel pull --yes --environment=preview --token=${{ secrets.VERCEL_TOKEN }}
    
                - name: Build Project Artifacts
                  run: vercel build --token=${{ secrets.VERCEL_TOKEN }}
    
                - name: Deploy Project Artifacts to Vercel
                  run: vercel deploy --yes --prebuilt --token=${{ secrets.VERCEL_TOKEN }}
    ```
    
    Now go to Vercel and get an access token. Name it `VERCEL_TOKEN` and paste this token in the GitHub repository secrets.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735728109781/2651faee-aef7-4566-a046-8cd887cf8780.png align="center")
    
    And now, push the code to GitHub and see the magic happen in the Actions tab.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735728167301/9add170a-bb69-44fb-a6e1-88590be46ab1.png align="center")