# typescript-yarn-workspace-example
## How to run this?
```bash
git clone https://github.com/maulanakurnia/basic-yarn-workspaces.git
cd basic-yarn-workspaces
yarn install
cd packages/common
yarn build
cd ../server
yarn start
```
## How to create this?

```bash
mkdir [name project/repo] && cd
npx lerna init

# and add it on last line of lerna.json

    {
        ... some obj
        "npmClient": "yarn",
        "useWorkspaces": true
    }

# then add a file called tsconfig.json
# copy and paste it

    {
        "private": true,
        "workspaces": [
            "packages/*"
        ],
        ... some obj
    }

# go to packages folder and add common + server folder
cd packages
mkdir common server

# enter folder common & server then yarn init
question name ( common/folder ): @common / @folder 
question version (1.0.0): ENTER
question description: ENTER
question entry point (index.js): dist/index.js 
question repository url: IF YOU HAVE REPO LIKE GITHUB REPO PASTE LINK REPO THERE
question author: YOUR NAME
question license (MIT): ENTER
question private: ENTER

# edit main obj and add typings obj on file package.json in common and server folder
    {
        ... some obj
        "main": "dist/index.js",
        "typings": "dist/index.d.ts",
        ... some obj
    }

# enter to common folder then add file ts
cd server/
mkdir src/
touch index.ts && vim index.ts
# and paste it
    export const add = (a: number, b: number) => a + b;
# save 

# go to server folder then add file ts
mkdir src/
touch index.ts && vim index.ts
# and paste it
    import { add } from "@example/common";

    console.log(add(1, 2));
# save

# add dependecies common on server/package.json 
    {
        ... some obj
        "dependencies": {
            "@example/common": "1.0.0"
        },
        ... some obj
    }

# add @types/node, ts-node, typescript on server folder
yarn add -D @types/node ts-node typescript

# on common folder
yarn add -D @types/node typescript

# then back to root folder and build 
yarn build

# finally go to server folder and run ts-node
yarn start

# finish
```