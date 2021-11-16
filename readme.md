# Vscode cheat sheet

A cheat sheet for Vscode.

- [Vscode](#vscode)
- [Extensions](#extensions)
- [Editor Shortcuts](#editor-shortcuts)
- [Keybindings](#keybindings)
- [Common Git Config](#common-git-config)
- [Github Actions](#github-actions)
  - [Publish A Package On the NPM Registry](#publish-a-package-on-the-npm-registry)
  - [Bundling and Committing a Node Module using Browserify](#bundling-and-committing-a-node-module-using-browserify)
- [Cleaning NPM Cache](#cleaning-npm-cache)
- [Settings JSON](#settings-json)
- [Eslint Configuration](#eslint-configuration)

## Vscode

- `Palette`  **CTRL + P**
- `Command Palette`  **CTRL + SHIFT + P**
  - `Git Clone`
  - `Merge`
- `Type Checking`

 ```javascript
 // @ts-nocheck
 // @ts-check
 ```

- Built-in `Terminal`  **CTRL + `**
  - Select `Javascript Debug Terminal` as `Default Profile`
- `Extensions` **CTRL + SHIFT + X**
- Closing built-in `Terminal`  **CTRL + D**
- `Find` And `Replace`  **CTRL + F**, **CTRL + H**
- `Find` And `Replace Globally`  **CTRL + SHIFT + F**, **CTRL + SHIFT + H**
- `Side By Side` Editing  **CTRL + \\**
- `Fullscreen`  **F11**
- `Markdown` Preview **CTRL + SHIFT + V**
- Split Markdown Preview **ALT + O**
- `Sidebar` Toggle **CTRL + B**
- `Zoom in/out` the whole vscode **CTRL + and CTRL -**
- `Font` size **CTRL + Mouse wheel**

---

## Extensions

- yzhang.markdown-all-in-one
  - Run command `Create Table of Contents` to insert a new table of contents.
- DavidAnson.vscode-markdownlint
- dbaeumer.vscode-eslint
- streetsidesoftware.code-spell-checker
- emmanuelbeziat.vscode-great-icons
- rangav.vscode-thunder-client
- GitHub.copilot
- JuanBlanco.solidity
- ms-vscode-remote.remote-containers
- ms-vscode-remote.remote-ssh
- ms-vscode-remote.remote-ssh-edit

## Editor Shortcuts

- `Copy` an entire `line` (when no text is selected)  **CTRL + C**
- `Delete` an entire `line` (when no text is selected)  **CTRL + SHIFT+K**
- `Cut` an entire `line` (when no text is selected)  **CTRL + X**
- `Move` an entire `line`  **ALT+ARROWS**
- `Select` the current `line`  **CTRL + L**
- Invoke IntelliSense  **CTRL + SPACE**
- `Multiple` selections (multi-cursor)  Hold **ALT** and **select**
- Code Folding  **CTRL + Shift+[** , **]**
- `Rename` Refactoring  **F2**
- `Navigating` on Errors and Warnings  **F8**
- Go to `Definition` **F12**

---

## Keybindings

```json
[
 {
  "key": "ctrl+alt+;",
  "command": "workbench.action.closeWindow"
 },
 {
  "key": "ctrl+shift+w",
  "command": "-workbench.action.closeWindow"
 },
 {
  "key": "ctrl+alt+'",
  "command": "workbench.action.closeActiveEditor"
 },
 {
  "key": "ctrl+w",
  "command": "-workbench.action.closeActiveEditor"
 },
 {
  "key": "ctrl+alt+\\",
  "command": "workbench.action.closeGroup",
  "when": "activeEditorGroupEmpty && multipleEditorGroups"
 },
 {
  "key": "ctrl+w",
  "command": "-workbench.action.closeGroup",
  "when": "activeEditorGroupEmpty && multipleEditorGroups"
 },
 {
  "key": "alt+o",
  "command": "markdown.showPreviewToSide",
  "when": "!notebookEditorFocused && editorLangId == 'markdown'"
 },
 {
  "key": "ctrl+k v",
  "command": "-markdown.showPreviewToSide",
  "when": "!notebookEditorFocused && editorLangId == 'markdown'"
 },
 {
  "key": "ctrl+alt+tab",
  "command": "markdown.extension.onTabKey",
  "when": "editorTextFocus && !editorReadonly && !editorTabMovesFocus && !hasOtherSuggestions && !hasSnippetCompletions && !inSnippetMode && !suggestWidgetVisible && editorLangId == 'markdown'"
 },
 {
  "key": "tab",
  "command": "-markdown.extension.onTabKey",
  "when": "editorTextFocus && !editorReadonly && !editorTabMovesFocus && !hasOtherSuggestions && !hasSnippetCompletions && !inSnippetMode && !suggestWidgetVisible && editorLangId == 'markdown'"
 },
 {
  "key": "ctrl+t ctrl+r",
  "command": "workbench.action.tasks.build"
 },
 {
  "key": "ctrl+shift+b",
  "command": "-workbench.action.tasks.build"
 },
 {
  "key": "ctrl+shift+b",
  "command": "markdown.extension.editing.toggleBold",
  "when": "editorTextFocus && !editorReadonly && editorLangId == 'markdown'"
 },
 {
  "key": "ctrl+b",
  "command": "-markdown.extension.editing.toggleBold",
  "when": "editorTextFocus && !editorReadonly && editorLangId == 'markdown'"
 }
]
```

## Common Git Config

Set **vscode** as default `merge` and `diff` tool

```bash
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'
```

```bash
git config user.email m.gh@linuxmail.org
git config user.name mlibre
git config --global credential.helper store
```

## Github Actions

### Publish A Package On the NPM Registry

1. Create an NPM token: **<https://www.npmjs.com/settings/mlibre/tokens/>**
2. Create a secret variable named `NPM_TOKEN` from the Github repository settings: **<https://github.com/mlibre/Ethereum-Smart-Contract-Deployer/settings/secrets/actions/new>**
3. Create a `yml` file in the repository: `.github/workflows/npm.yml`

```yml
name: Publish on NPM registry

on:
  push:
    branches: ['master']

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: 14.x
          registry-url: https://registry.npmjs.org/
      - run: npm publish --access public
        env:
          NODE_AUTH_TOKEN: ${{secrets.NPM_TOKEN}}
```

### Bundling and Committing a Node Module using Browserify

Create a yml file in the repository: `.github/workflows/browserify.yml`

```yml
name: Browserify Bundle

on:
  push:
    branches: ['master']

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: 14.x
          registry-url: https://registry.npmjs.org/
      # - run: npm install
      - run: npm install
      - run: npm install -g browserify
      - run: browserify -r ./main.js:EthereumTokens -o ./web/bundle.js
      - run: |
          git config --global user.name 'mlibre'
          git config --global user.email 'm.gh@linuxmail.org'
          git add web
          git commit -am "Automated bundle"
          git push

```

## Cleaning NPM Cache

```bash
rm -r node_modules/
npm cache clean --force
sudo npm cache clean --force -g
sudo pacman -R nodejs-lts-fermium npm
# sudo pacman -R nodejs npm
sudo rm -r ~/.npm
rm -r ~/.node-gyp/
rm -r .cache/node-gyp/
sudo rm -r /usr/local/lib/node_modules/
sudo rm -r /usr/lib/node_modules/
sudo pacman -S nodejs-lts-fermium npm
# sudo pacman -S nodejs npm
# Restart the OS
```

## Settings JSON

```json
{
 "update.mode": "none",
 "telemetry.telemetryLevel": "off",
 "breadcrumbs.enabled": false,
 "workbench.iconTheme": "vscode-great-icons",
 "workbench.enableExperiments": false,
 "workbench.activityBar.visible": false,
 "window.titleBarStyle": "custom",
 "window.dialogStyle": "custom",
 "window.zoomLevel": 2,
 "explorer.compactFolders": false,
 "explorer.confirmDelete": false,
 "explorer.confirmDragAndDrop": false,
 "explorer.autoReveal": false,
 "editor.maxTokenizationLineLength": 20000,
 "editor.minimap.enabled": false,
 "editor.largeFileOptimizations": false,
 "editor.insertSpaces": false,
 "editor.tabSize": 3,
 "editor.formatOnSave": true,
 "editor.defaultFormatter": "dbaeumer.vscode-eslint",
 "editor.fontFamily": "'Droid Sans Mono', 'monospace', monospace, 'Droid Sans Fallback', 'Fira Code Retina'",
 // "editor.fontFamily": "Fira Code Retina",
 // "editor.fontLigatures": true,
 "editor.mouseWheelZoom": true,
 "editor.inlineSuggest.enabled": true,
 "git.confirmSync": false,
 "git.pullTags": false,
 "git.autofetch": true,
 "git.enableSmartCommit": true,
 "git.ignoreRebaseWarning": true,
 "diffEditor.ignoreTrimWhitespace": false,
 "extensions.autoCheckUpdates": false,
 "extensions.autoUpdate": "onlyEnabledExtensions",
 "markdown.extension.toc.updateOnSave": false,
 "markdown.extension.completion.respectVscodeSearchExclude": true,
 "markdown.extension.syntax.decorations": false,
 "eslint.codeAction.showDocumentation": {
  "enable": true
 },
 "eslint.format.enable": true,
 "github.copilot.enable": {
  "*": true,
  "yaml": true,
  "plaintext": false,
  "markdown": true
 },
 "[json]": {
  "editor.quickSuggestions": {
   "strings": true
  },
  "editor.defaultFormatter": "vscode.json-language-features"
 },
 "[jsonc]": {
  "editor.quickSuggestions": {
   "strings": true
  },
  "editor.defaultFormatter": "vscode.json-language-features"
 },
 "[solidity]": {
  "editor.defaultFormatter": "JuanBlanco.solidity"
 },
 "[javascript]": {
  "editor.defaultFormatter": "dbaeumer.vscode-eslint"
 },
 "[html]": {
  "editor.suggest.insertMode": "replace",
  "editor.defaultFormatter": "vscode.html-language-features"
 },
 "[markdown]": {
  "editor.defaultFormatter": "yzhang.markdown-all-in-one"
 },
 "terminal.integrated.scrollback": 10000,
 "terminal.integrated.defaultProfile.linux": "JavaScript Debug Terminal",
 "terminal.integrated.persistentSessionScrollback": 1000,
 "terminal.integrated.profiles.linux": {
  "bash": {
   "path": "bash",
   "icon": "terminal-bash"
  },
  "zsh": {
   "path": "zsh"
  },
  "fish": {
   "path": "fish"
  },
  "tmux": {
   "path": "tmux",
   "icon": "terminal-tmux"
  },
  "pwsh": {
   "path": "pwsh",
   "icon": "terminal-powershell"
  },
  "JavaScript Debug Terminal": {
   "extensionIdentifier": "ms-vscode.js-debug",
   "icon": "debug",
   "id": "extension.js-debug.debugTerminal",
   "title": "JavaScript Debug Terminal"
  },
  "bash (migrated)": {
   "path": "bash",
   "args": []
  },
  "/usr/bin/bash (migrated)": {
   "path": "/usr/bin/bash",
   "args": []
  }
 },
 "cSpell.userWords": [
  "adduser",
  "allman",
  "autofetch",
  "AUTOMINE",
  "Autostarts",
  "bitcoinjs",
  "blockcypher",
  "Claimtrie",
  "cname",
  "coinjoin",
  "commandline",
  "corsdomain",
  "Datahub",
  "dbaeumer",
  "difftool",
  "fileupload",
  "Fira",
  "Fullscreen",
  "geoip",
  "getfunding",
  "Grammarly",
  "hashex",
  "hdwallet",
  "healight",
  "heartpulse",
  "IPFS",
  "JOSN",
  "jshashes",
  "LBRY",
  "lbrynet",
  "linebreak",
  "liveshare",
  "mainchain",
  "maticjs",
  "maticnetwork",
  "mergetool",
  "Merkle",
  "metacoin",
  "mforgood",
  "mkdir",
  "mlibre",
  "monero",
  "monospace",
  "nameserver",
  "newbot",
  "nocheck",
  "pacman",
  "pamac",
  "paren",
  "parens",
  "pwsh",
  "redlist",
  "Reiner",
  "reposted",
  "resolv",
  "rpcapi",
  "rpccorsdomain",
  "scrollback",
  "signup",
  "solcjs",
  "stylesheet",
  "syncmode",
  "Syyuu",
  "tmpfs",
  "TOKENNAME",
  "Tradingview",
  "txid",
  "txpool",
  "usermod",
  "UTXO",
  "UTXOs",
  "xrandr"
 ]
}
```

## Eslint Configuration

```javascript
module.exports = {
 "env": {
  "commonjs": true,
  "es2021": true,
  "node": true,
  "mocha": true
 },
 "extends": [
  "eslint:recommended",
  "plugin:node/recommended"
 ],
 "parserOptions": {
  "ecmaVersion": 12,
  "impliedStrict": true
 },
 "rules": {
  "linebreak-style": [
   "error",
   "unix"
  ],
  "quotes": [
   "error",
   "double"
  ],
  "semi": [
   "error",
   "always"
  ],
  "one-var": [
   "error",
   "never"
  ],
  "brace-style": [
   "error",
   "allman",
   {
    "allowSingleLine": true
   }
  ],
  // "arrow-parens": [
  //  "error",
  //  "always"
  // ],
  "arrow-body-style": [
   "error",
   "always"
  ],
  "no-template-curly-in-string": [
   "error"
  ],
  "prefer-const": [
   "error",
   {
    "destructuring": "any",
    "ignoreReadBeforeAssign": false
   }
  ],
  "no-new-object": [
   "error",
  ],
  "no-extra-parens": [
   "error",
   "all",
   {
    "conditionalAssign": false
   }
  ],
  "no-empty-function": [
   "error",
  ],
  "no-empty": [
   "warn",
   { 
    "allowEmptyCatch": true
   }
  ],
  "no-eq-null": [
   "error",
  ],
  "no-extra-bind": [
   "error",
  ],
  "no-self-compare": [
   "error",
  ],
  "no-useless-call": [
   "error",
  ],
  "no-undefined": [
   "error",
  ],
  "no-undef": [
   "warn",
  ],
  "no-array-constructor": [
   "error",
  ],
  "prefer-destructuring": [
   "error", {
    "VariableDeclarator": {
     "array": true,
     "object": true
    },
    "AssignmentExpression": {
     "array": false,
     "object": false
    }
   },
   {
    "enforceForRenamedProperties": false
   }
  ],
  "object-shorthand": [
   "warn",
  ],
  "prefer-spread": [
   "warn",
  ],
  "prefer-template": [
   "warn",
  ],
  "no-loop-func": [
   "warn",
  ],
  "prefer-rest-params": [
   "warn",
  ],
  "no-new-func": [
   "warn",
  ],
  "space-before-blocks": [
   "warn",
  ],
  "space-before-function-paren": ["error", "always"],
  "keyword-spacing": [
   "error"
  ],
  // "func-call-spacing": [
  //  "error", "always"
  // ],
  "function-paren-newline": [
   "warn",
  ],
  "no-unneeded-ternary": [
   "warn",
  ],
  "no-process-exit": "off",
  "require-await": "warn",
  "indent": [
   "error",
   "tab", 
   {
    "MemberExpression": 0
   }
  ],
  "no-tabs": 0,
  "node/no-unpublished-import": "off",
  "node/no-unpublished-require": "off"
 }
};
```
