Vscode cheat sheet
===

* `Palette`  **CTRL+P**
* `Command Palette`  **CTRL+SHIFT+P**
	* `Git Clone`  Cloning a git repository
	* `Merge`  Merge branches
* `Type Checking` to a JS file 
	```javascript
	// @ts-nocheck
	// @ts-check
	``` 
* Built-in `Terminal`  **CTRL+`**
	* Select `Javascript Debug Terminal` as `Default Profile`
* Closing built-in `Terminal`  **CTRL+D**
* `Find` And `Replace`  **CTRL+F**, **CTRL+H**
* `Find` And `Replace Globally`  **CTRL+SHIFT+F**, **CTRL+SHIFT+H**
* `Side By Side` Editing  **CTRL+\\**
* `Fullscreen`  **F11**
* `Markdown preview` **CTRL+SHIFT+V**
* `Sidebar` Toggle **CTRL+B**
* `Zoom` entire vscode **CTRL + and CTRL -**
* `Font` size **CTRL + Mouse wheel** 

---

## Editor
* `Copy` an entire `line` (when no text is selected)  **CTRL+C**
* `Delete` an entire `line` (when no text is selected)  **CTRL+SHIFT+K**
* `Cut` an entire `line` (when no text is selected)  **CTRL+X**
* `Move` an entire `line`  **ALT+ARROWS**
* `Select` the current `line`  **CTRL+L**
* Invoke `IntelliSense`  **CTRL+SPACE**
* `Multiple` selections (multi-cursor)  Hold **ALT** and **select**
* Code Folding  **Ctrl+Shift+[** , **]**
* `Rename` Refactoring  **F2**
* `Navigating` on Errors and Warnings  **F8**
* Go to `Definition` **F12**

---

## Git
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

## Settings
```json
{
	"explorer.compactFolders": false,
	"workbench.activityBar.visible": false,
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
	"editor.formatOnSave": true,
	"editor.defaultFormatter": "dbaeumer.vscode-eslint",
	"eslint.format.enable": true,
	"update.mode": "none",
	"git.ignoreRebaseWarning": true,
	"editor.fontFamily": "'Droid Sans Mono', 'monospace', monospace, 'Droid Sans Fallback'",
	"terminal.integrated.scrollback": 5000,
	"terminal.integrated.defaultProfile.linux": "JavaScript Debug Terminal",
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
	}
}
```

## Eslint
```json
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
