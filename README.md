## Установка Eslint & Prettier в create-react-app

Нужно установить
```
create-react-app projectName 
```

Eslint, это конфигурация от Airbnb и необходимые пакеты…
```javascript
npm i -D eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react

yarn add --dev eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react

```
и
Prettier, это конфигурация, чтобы избежать конфликта с Eslint и необходимыми пакетами…
```javascript
npm i -D prettier eslint-config-prettier eslint-plugin-prettier

yarn add --dev prettier eslint-config-prettier eslint-plugin-prettier
```

Чтобы не коммитилось если есть ошибки нужны следующие пакеты
```javascript
npm i -D husky lint-staged pretty-quick
```

husky: Will run npm script before the committing the code.

lint-staged: Запустит пользовательский скрипт на отфильтрованных файлах с расширениями, такими как .js или .jsx

pretty-quick: Предварительно подтвердит ваш код.

package.json

Добавить в script 
```json
"precommit": "NODE_ENV=production lint-staged"
```

вниз 

```json
"lint-staged": {
  "*.{js,jsx}": [
    "pretty-quick --staged",
    "eslint src/ --fix",
    "git add"
  ]
}
```

добавить .eslintrc в коррень
```json
{
  "extends": ["airbnb", "prettier", "prettier/react"],
  "plugins": ["prettier"],
  "rules": {
    "react/jsx-filename-extension": [
      1,
      {
        "extensions": [".js", ".jsx"]
      }
    ],
    "react/prop-types": 0,
    "no-underscore-dangle": 0,
    "import/imports-first": ["error", "absolute-first"],
    "import/newline-after-import": "error"
  },
  "globals": {
    "window": true,
    "document": true,
    "localStorage": true,
    "FormData": true,
    "FileReader": true,
    "Blob": true,
    "navigator": true
  },
  "parser": "babel-eslint"
}
```

добавить .prettierrc в коррень

```json
{
  "singleQuote": true
}
```

Visual Studio Code

Eslint
Prettier
There are some settings you have to do for making these extensions workable.

```javascript
{
  "files.autoSave": "onFocusChange",
  "editor.formatOnSave": true,
  "editor.formatOnType": true,
  "eslint.autoFixOnSave": true,
  "eslint.enable": true,
  "prettier.singleQuote": true,
}
```

Добавить env jest
```json
"env": {
    "jest": true
  },
```

Подправит package.json
```json
"husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  
  
```
и удалить так как устаревшая технология
```json
"precommit": "NODE_ENV=production lint-staged"
```

добавить .prettierignore и .eslintignore