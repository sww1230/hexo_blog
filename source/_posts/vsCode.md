---
title: vs code 配置及插件
date: 2019-03-25
tags:
---

#### 推荐使用vs code进行前端编码，规定Tab大小为2个空格
  1. **vs code配置**
      ```` javascript
        {
          "editor.tabSize": 2,
          "workbench.startupEditor": "newUntitledFile",
          "workbench.iconTheme": "vscode-icons",
          // 以下为stylus配置
          "stylusSupremacy.insertColons": false, // 是否插入冒号
          "stylusSupremacy.insertSemicolons": false, // 是否插入分好
          "stylusSupremacy.insertBraces": false, // 是否插入大括号
          "stylusSupremacy.insertNewLineAroundImports": false, // import之后是否换行
          "stylusSupremacy.insertNewLineAroundBlocks": false, // 两个选择器中是否换行
          "vetur.format.defaultFormatter.html": "js-beautify-html",
          "eslint.autoFixOnSave": true,
          "eslint.validate": [
            "javascript",
            {
              "language": "html",
              "autoFix": true
            },
            {
              "language": "vue",
              "autoFix": true
            },
            "javascriptreact",
            "html",
            "vue"
          ],
          "eslint.options": { "plugins": ["html"] },
          "prettier.singleQuote": true,
          "prettier.semi": false,
          "javascript.format.insertSpaceBeforeFunctionParenthesis": false,
          "vetur.format.js.InsertSpaceBeforeFunctionParenthesis": false,
          "vetur.format.defaultFormatter.js": "prettier",
          // "prettier.eslintIntegration": true
        }
      ````
  2. **vs code 插件**
      - Auto Close Tag
      - Path Intellisense
      - Prettier
      - Vetur
      - vscode-icons
      - Markdown Preview Enhanced

