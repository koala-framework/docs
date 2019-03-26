# Pre Commit Hooks

## Installing dependencies

    npm install husky lint-staged prettier prettylint @vivid-planet/vplint
    
#### Add script for Typescript typechecks

    // package.json
    "scripts": {
        ...,
        "tsc": "tsc --skipLibCheck --noEmit --project ./tsconfig.json && :"
    }

#### Configure `prettier` for code style

    // .prettierrc.json
    {
        "printWidth": 150,
        "tabWidth": 4,
        "trailingComma": "all",
        "semi": true
    }

#### Configure `husky` to use `lint-staged`

    // .huskyrc.json
    {
        "hooks": {
            "pre-commit": "lint-staged"
        }
    }
    
#### Configure `lint-staged` for installed linters

Example configuration for lint typescript, prettier and vivid-planet code

    // .lintstagedrc.json
    {
        "linters": {            
            "*.{ts,tsx}": ["tslint", "npm run tsc --silent"],
            "*.{ts,tsx,js,jsx,json,css,scss,md}": ["prettylint"],
            "*": ["vplint"]
        },
        "ignore": ["package-lock.json", "*.lock"]
    }

    // More infos for filtering files: https://www.npmjs.com/package/lint-staged#filtering-files

#### Configure `GitLab CI`

    // .gitlab-ci.yml
    cache:
        paths:
            - node_modules/
    
    lint:
        only:
            - merge_requests
        tags:
            - vivid
        before_script:
            - npm install
        script:
            - git reset --soft origin/$CI_MERGE_REQUEST_TARGET_BRANCH_NAME
            - node_modules/.bin/lint-staged
