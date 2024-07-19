# SampleProject

## Setup guide

### Init project

```
ng new <PROJECT_NAME>
```

### Nvmrc

- Create file `.nvmrc` in the root
- Specify node version in this file.

File Name: `.nvmrc`

```
<NODE_VERSION>
```

### eslint

- Run `ng add @angular-eslint/schematics`
- Config `.eslintrc.json`
- Run with `ng lint --fix`

### prettier

- Run `npm install prettier --save-dev`
- Run `npm install prettier-eslint eslint-config-prettier eslint-plugin-prettier --save-dev`
- Rename file `eslint.config.js` with `.eslintrc.json`
- Adjust `.eslintrc.json` as follows
  File Name: `.eslintrc.json`

```js
{
  "root": true,
  "ignorePatterns": ["projects/**/*"],
  "plugins": ["@angular-eslint"],
  "overrides": [
    {
      "plugins": ["@angular-eslint"],
      "files": ["*.ts"],
      "extends": [
        "eslint:recommended",
        "plugin:@typescript-eslint/recommended",
        "plugin:@angular-eslint/recommended",
        "plugin:@angular-eslint/template/process-inline-templates",
        "plugin:prettier/recommended"
      ],
      "rules": {
        "@angular-eslint/directive-selector": [
          "error",
          {
            "type": "attribute",
            "prefix": "app",
            "style": "camelCase"
          }
        ],
        "@angular-eslint/component-selector": [
          "error",
          {
            "type": "element",
            "prefix": "app",
            "style": "kebab-case"
          }
        ]
      }
    },
    {
      "files": ["*.html"],
      "excludedFiles": ["*inline-template-*.component.html"],
      "extends": [
        "plugin:@angular-eslint/template/recommended",
        "plugin:@angular-eslint/template/accessibility",
        "plugin:prettier/recommended"
      ],
      "rules": {
        "prettier/prettier": [
          "error",
          {
            "parser": "angular"
          }
        ]
      }
    }
  ]
}

```

- Add file `.prettierrc.json` and `.prettierignore` to the root of the project.
- Config as follows.

File Name: `.prettierrc.json`

```json
{
  "tabWidth": 2,
  "useTabs": false,
  "singleQuote": true,
  "semi": true,
  "bracketSpacing": true,
  "arrowParens": "avoid",
  "trailingComma": "es5",
  "bracketSameLine": true,
  "printWidth": 80
}
```

\*Semicolon is optional

File Name: `.prettierignore` (usually for generated code)

```
src/app/core/api/*
```

- Run with `npx prettier --write .`
- Run `npm install prettier-eslint eslint-config-prettier eslint-plugin-prettier --save-dev`

## Lint staged

- Run `npm install lint-staged`
- In `package.json` add

```
"lint-staged": {
    "**/*": "prettier --write --ignore-unknown",
    "*.ts": "eslint"
  }
```

## Pre-commit hook (husky and lint staged)

- Run `npm install husky`
- Run `npx husky-init`
- In `.husky/pre-commit` add

```
npx lint-staged
```

---

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 18.1.1.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.dev/tools/cli) page.
