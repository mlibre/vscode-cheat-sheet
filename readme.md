Vscode cheat sheet
===

* `Palette`  **CTRL + P**
* `Command Palette`  **CTRL + SHIFT + P**
	* `Git Clone`
	* `Merge`
* `Type Checking`
	```javascript
	// @ts-nocheck
	// @ts-check
	``` 
* Built-in `Terminal`  **CTRL + `**
	* Select `Javascript Debug Terminal` as `Default Profile`
* `Extensions` **CTRL + SHIFT + X**
* Closing built-in `Terminal`  **CTRL + D**
* `Find` And `Replace`  **CTRL + F**, **CTRL + H**
* `Find` And `Replace Globally`  **CTRL + SHIFT + F**, **CTRL + SHIFT + H**
* `Side By Side` Editing  **CTRL + \\**
* `Fullscreen`  **F11**
* `Markdown` Preview **CTRL + SHIFT + V**
* Split Markdown Preview **ALT + O**
* `Sidebar` Toggle **CTRL + B**
* `Zoom in/out` the whole vscode **CTRL + and CTRL -**
* `Font` size **CTRL + Mouse wheel** 

---

## Editor Shortcuts
* `Copy` an entire `line` (when no text is selected)  **CTRL + C**
* `Delete` an entire `line` (when no text is selected)  **CTRL + SHIFT+K**
* `Cut` an entire `line` (when no text is selected)  **CTRL + X**
* `Move` an entire `line`  **ALT+ARROWS**
* `Select` the current `line`  **CTRL + L**
* Invoke IntelliSense  **CTRL + SPACE**
* `Multiple` selections (multi-cursor)  Hold **ALT** and **select**
* Code Folding  **CTRL + Shift+[** , **]**
* `Rename` Refactoring  **F2**
* `Navigating` on Errors and Warnings  **F8**
* Go to `Definition` **F12**

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

## Using Github Action To Publish A Package On the NPM Registry
1. Create a NPM token: **https://www.npmjs.com/settings/mlibre/tokens/**
2. Create a secret variable named `NPM_TOKEN` from the github repository settings: **https://github.com/mlibre/Ethereum-Smart-Contract-Deployer/settings/secrets/actions/new**
3. Create a yml file in the repository: `.github/workflows/npm.yml`
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
      # - run: npm install
      - run: npm publish --access public
        env:
          NODE_AUTH_TOKEN: ${{secrets.NPM_TOKEN}}
```


## Settings JSON
```json
{
	"explorer.compactFolders": false,
	"git.pullTags": false,
	"breadcrumbs.enabled": false,
	"editor.minimap.enabled": false,
	"telemetry.telemetryLevel": "off",
	"workbench.enableExperiments": false,
	"extensions.autoCheckUpdates": false,
	"extensions.autoUpdate": "onlyEnabledExtensions",
	"explorer.confirmDelete": false,
	"explorer.confirmDragAndDrop": false,
	"git.confirmSync": false,
	"editor.insertSpaces": false,
	"diffEditor.ignoreTrimWhitespace": false,
	"editor.largeFileOptimizations": false,
	"git.autofetch": true,
	"git.enableSmartCommit": true,
	"workbench.iconTheme": "vscode-great-icons",
	"window.titleBarStyle": "custom",
	"window.dialogStyle": "custom",
	"eslint.codeAction.showDocumentation": {
		"enable": true
	},
	"liveshare.authenticationProvider": "GitHub",
	"window.zoomLevel": 2,
	"editor.tabSize": 3,
	"update.mode": "none",
	"editor.formatOnSave": true,
	"editor.defaultFormatter": "dbaeumer.vscode-eslint",
	"eslint.format.enable": true,
	"git.ignoreRebaseWarning": true,
	"editor.fontFamily": "'Droid Sans Mono', 'monospace', monospace, 'Droid Sans Fallback'",
	"terminal.integrated.scrollback": 10000,
	"terminal.integrated.defaultProfile.linux": "JavaScript Debug Terminal",
	"terminal.integrated.persistentSessionScrollback": 1000,
	"workbench.activityBar.visible": false,
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
	"editor.inlineSuggest.enabled": true,
	"github.copilot.enable": {
		"*": true,
		"yaml": false,
		"plaintext": false,
		"markdown": true
	},
	"grammarly.hideUnavailablePremiumAlerts": true,
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
		"bitcoinjs",
		"blockcypher",
		"coinjoin",
		"commandline",
		"corsdomain",
		"dbaeumer",
		"difftool",
		"fileupload",
		"Fullscreen",
		"geoip",
		"getfunding",
		"Grammarly",
		"hashex",
		"hdwallet",
		"healight",
		"heartpulse",
		"IPFS",
		"jshashes",
		"LBRY",
		"linebreak",
		"liveshare",
		"mergetool",
		"Merkle",
		"metacoin",
		"mforgood",
		"mlibre",
		"monospace",
		"nocheck",
		"pacman",
		"pamac",
		"paren",
		"parens",
		"pwsh",
		"redlist",
		"Reiner",
		"rpcapi",
		"rpccorsdomain",
		"scrollback",
		"signup",
		"solcjs",
		"stylesheet",
		"syncmode",
		"Syyuu",
		"TOKENNAME",
		"txid",
		"txpool",
		"UTXO",
		"UTXOs"
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
		// 	"error",
		// 	"always"
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
		// 	"error", "always"
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
