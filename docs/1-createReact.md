# steps

#

##

```
<!-- tsconfig.json -->
"baseUrl": "./src",

npx create-react-app react-platform --template typescript

npm install --save-dev husky @commitlint/cli @commitlint/config-conventional
npx husky install
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit $1'
npx husky add .husky/pre-commit "npm run lint-staged"
```

commitlint.config.js

```
module.exports = {
    extends: ['@commitlint/config-conventional'],
    rules: {
      'type-case': [2, 'always', ['lower-case', 'upper-case']],
      'type-enum': [2, 'always',['feat', 'fix', 'docs','style','refactor','perf','test', 'chore', 'revert']]
    }
  }
```

```
npm install lint-staged --save-dev

"lint-staged": "lint-staged"
"lint-staged": {
    "*.{js,jsx,ts,tsx}": [
      "eslint --fix",
      "prettier --write"
    ],
    "*.json": [
      "prettier --write"
    ],
    "*.{scss,less,html}": [
      "stylelint --fix",
      "prettier --write"
    ],
    "*.md": [
      "prettier --write"
    ]
  },

npm i eslint -D
npx eslint --init
.eslintignore
```

```
<!-- https://juejin.cn/post/6844903901544742925 -->
rules: {
    'react/jsx-filename-extension': 'off', // 关闭airbnb对于jsx必须写在jsx文件中的设置
    'react/prop-types': 'off', // 关闭airbnb对于必须添加prop-types的校验
    'react/destructuring-assignment': [
      2,
      'always',
      {
        ignoreClassFields: false,
      },
    ],
    'react/jsx-one-expression-per-line': 'off', // 关闭要求一个表达式必须换行的要求，和Prettier冲突了
    'react/jsx-wrap-multilines': [2,{
      prop: 'ignore', // 关闭要求jsx属性中写jsx必须要加括号，和Prettier冲突了
    }],
    <!-- 'react/jsx-wrap-multilines': [
      2,
      'always',
      {
        prop: 'ignore', // 关闭要求jsx属性中写jsx必须要加括号，和Prettier冲突了
      },
    ], -->
    'comma-dangle': [
      'error',
      {
        arrays: 'always-multiline',
        objects: 'always-multiline',
        imports: 'always-multiline',
        exports: 'always-multiline',
        functions: 'only-multiline', // 关闭airbnb对函数调用参数，非一行，最后也要加逗号的限制
      },
    ],
    'jsx-a11y/no-static-element-interactions': 'off', // 关闭非交互元素加事件必须加 role
    'jsx-a11y/click-events-have-key-events': 'off', // 关闭click事件要求有对应键盘事件
    'no-bitwise': 'off', // 不让用位操作符，不知道为啥，先关掉
  },
  overrides: [
    {
      files: ['**/Mi/*.js', '**/Mi/*.jsx'],
      rules: {
        'react/prop-types': 'error', // Mi 文件夹下的是系统组件，必须写prop-types
      },
    },
  ],
```

```
npm i prettier -D
.prettierrc.js
.prettierignore>
npm i eslint-config-prettier eslint-plugin-prettier -D

```

vscode>setting>
"editor.codeActionsOnSave": {
"source.fixAll.eslint": true,
},
重启

```
npm i stylelint stylelint-config-standard -D

.stylelintrc.js

npm i stylelint-prettier -D
npm install -D stylelint-config-rational-order
```

```
npm i --dev eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react eslint-plugin-react-hooks
npm i eslint-config-airbnb eslint-config-airbnb-typescript -D

"extends": [
  "react-app", //  react帮配置好了一些语法，譬如箭头函数
  "airbnb",
  "plugin:prettier/recommended" // prettier配置
]
```
##
