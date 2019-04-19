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




#Новый 


#eslint
<pre><code>▶ npm install --save-dev eslint eslint-loader babel-loader babel-eslint eslint-plugin-react
</code></pre>
<ul>
<li><code>eslint</code> is the core JavaScript linter.</li>
<li><code>eslint-loader</code> tells webpack that you want to use eslint in our build</li>
<li><code>babel-loader</code> transpiles our code with webpack</li>
<li><code>babel-eslint</code> provides linting for valid ES6 code</li>
<li><code>eslint-plugin-react</code> extends ESLint rules to cover React</li>
</ul>
<pre><code>▶ touch .eslintrc
</code></pre>
<p>add the following rules in your <code>.eslintrc</code>file, or you can make your own rules</p>
<div class="highlight highlight-source-json"><pre>{
  <span class="pl-s"><span class="pl-pds">"</span>parser<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>babel-eslint<span class="pl-pds">"</span></span>,
  <span class="pl-s"><span class="pl-pds">"</span>env<span class="pl-pds">"</span></span>: {
    <span class="pl-s"><span class="pl-pds">"</span>browser<span class="pl-pds">"</span></span>: <span class="pl-c1">true</span>,
    <span class="pl-s"><span class="pl-pds">"</span>commonjs<span class="pl-pds">"</span></span>: <span class="pl-c1">true</span>,
    <span class="pl-s"><span class="pl-pds">"</span>es6<span class="pl-pds">"</span></span>: <span class="pl-c1">true</span>,
    <span class="pl-s"><span class="pl-pds">"</span>node<span class="pl-pds">"</span></span>: <span class="pl-c1">true</span>
  },
  <span class="pl-s"><span class="pl-pds">"</span>plugins<span class="pl-pds">"</span></span>: [
    <span class="pl-s"><span class="pl-pds">"</span>react<span class="pl-pds">"</span></span>
  ],
  <span class="pl-s"><span class="pl-pds">"</span>extends<span class="pl-pds">"</span></span>: [<span class="pl-s"><span class="pl-pds">"</span>plugin:prettier/recommended<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>plugin:react/recommended<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>eslint:recommended<span class="pl-pds">"</span></span>],
  <span class="pl-s"><span class="pl-pds">"</span>rules<span class="pl-pds">"</span></span>: {
    <span class="pl-s"><span class="pl-pds">"</span>quotes<span class="pl-pds">"</span></span>: [<span class="pl-c1">1</span>, <span class="pl-s"><span class="pl-pds">"</span>double<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>avoid-escape<span class="pl-pds">"</span></span>],
    <span class="pl-s"><span class="pl-pds">"</span>react/prop-types<span class="pl-pds">"</span></span>: <span class="pl-c1">0</span>,
    <span class="pl-s"><span class="pl-pds">"</span>no-console<span class="pl-pds">"</span></span>: <span class="pl-c1">0</span>,
    <span class="pl-s"><span class="pl-pds">"</span>no-unused-vars<span class="pl-pds">"</span></span>: <span class="pl-c1">1</span>,
    <span class="pl-s"><span class="pl-pds">"</span>no-func-assign<span class="pl-pds">"</span></span>: <span class="pl-c1">2</span>,
    <span class="pl-s"><span class="pl-pds">"</span>no-const-assign<span class="pl-pds">"</span></span>: <span class="pl-c1">2</span>,
    <span class="pl-s"><span class="pl-pds">"</span>no-var<span class="pl-pds">"</span></span>: <span class="pl-c1">2</span>,
    <span class="pl-s"><span class="pl-pds">"</span>react/react-in-jsx-scope<span class="pl-pds">"</span></span>: <span class="pl-c1">0</span>
  }
}</pre></div>
<h2>prettier</h2>
<pre><code>▶ npm install --save-dev prettier eslint-config-prettier eslint-plugin-prettier
</code></pre>
<ul>
<li><code>prettier</code> — the core prettier library. Duh.</li>
<li><code>eslint-plugin-prettier</code> — this plugin allows you to format code using Prettier when you run --fix</li>
<li><code>eslint-config-prettier</code> — This library solves the conflicts between eslint and prettier. It turns off conflicting rules. ESLint’s rules, not Prettier’s. Obviously.</li>
</ul>
<h2>vscode settings</h2>
<p><code>.vscode/settings.json</code></p>
<div class="highlight highlight-source-json"><pre>{
  <span class="pl-s"><span class="pl-pds">"</span>editor.formatOnSave<span class="pl-pds">"</span></span>: <span class="pl-c1">true</span>,
  <span class="pl-s"><span class="pl-pds">"</span>[javascript]<span class="pl-pds">"</span></span>: {
    <span class="pl-s"><span class="pl-pds">"</span>editor.formatOnSave<span class="pl-pds">"</span></span>: <span class="pl-c1">false</span>
  },
  <span class="pl-s"><span class="pl-pds">"</span>eslint.autoFixOnSave<span class="pl-pds">"</span></span>: <span class="pl-c1">true</span>,
  <span class="pl-s"><span class="pl-pds">"</span>eslint.alwaysShowStatus<span class="pl-pds">"</span></span>: <span class="pl-c1">true</span>,
  <span class="pl-s"><span class="pl-pds">"</span>files.associations<span class="pl-pds">"</span></span>: {
    <span class="pl-s"><span class="pl-pds">"</span>*.js<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>javascriptreact<span class="pl-pds">"</span></span>
  }
}</pre></div>
<p>after the above setting, you vscode should be able to lint and fix your code automatically</p>
<h2>git hook</h2>
<pre><code>▶ npm install --save-dev pretty-quick husky lint-staged
</code></pre>
<p>Add the following code into <code>package.json</code> file, it’ll fix the error automatically</p>
<div class="highlight highlight-source-json"><pre><span class="pl-s"><span class="pl-pds">"</span>husky<span class="pl-pds">"</span></span>: {
	<span class="pl-s"><span class="pl-pds">"</span>hooks<span class="pl-pds">"</span></span>: {
	  <span class="pl-s"><span class="pl-pds">"</span>pre-commit<span class="pl-pds">"</span></span>: <span class="pl-s"><span class="pl-pds">"</span>pretty-quick --staged<span class="pl-pds">"</span></span>
	}
},</pre></div>
<p>now try a commit, what a beautiful result<br>
<a target="_blank" rel="noopener noreferrer" href="https://user-images.githubusercontent.com/25027560/49007971-b5661a00-f1a7-11e8-88e7-17562def7ca6.png"><img src="https://user-images.githubusercontent.com/25027560/49007971-b5661a00-f1a7-11e8-88e7-17562def7ca6.png" alt="image" style="max-width:100%;"></a></p>
<h2>references</h2>
<p><a href="https://www.youtube.com/watch?v=bfyI9yl3qfE" rel="nofollow">Add ESLint &amp; Prettier to VS Code for a Create React App - YouTube</a><br>
<a href="https://alligator.io/react/linting-react/" rel="nofollow">Linting React Using ESLint with Create React App ← Alligator.io</a><br>
<a href="https://www.robinwieruch.de/react-eslint-webpack-babel/" rel="nofollow">React Code Style with ESLint + Babel + Webpack - RWieruch</a><br>
<a href="https://blog.gojekengineering.com/eslint-prettier-for-a-consistent-react-codebase-eaa673debb1d" rel="nofollow">ESLint + Prettier For a Consistent React Codebase – GO-JEK Product + Tech</a></p>
