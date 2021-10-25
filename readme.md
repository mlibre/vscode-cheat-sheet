Vscode cheat sheet
===

* Opening `Palette`  **CTRL+P**
* Opening `Command Palette`  **CTRL+SHIFT+P**
	* `Git Clone`  Cloning a git repository
	* `Merge`  Merge branches
* Adding `Type Checking` to a JS file 
	```javascript
	// @ts-nocheck
	// @ts-check
	``` 
* Opening built-in `Terminal`  **CTRL+`**
	* Select `Javascript Debug Terminal` as `Default Profile`
* Closing built-in `Terminal`  **CTRL+D**
* `Find` And `Replace`  **CTRL+F**, **CTRL+H**
* `Find` And `Replace Globally`  **CTRL+SHIFT+F**, **CTRL+SHIFT+H**
* `Side By Side` Editing  **CTRL+\\**
* `Fullscreen`  **F11**
* Open `Markdown preview` **CTRL+SHIFT+V**
* `Sidebar` Toggle **CTRL+B** 
---

## Editor
* `Copy` an entire `line` (when no text is selected)  **CTRL+C**
* `Delete` an entire `line` (when no text is selected)  **CTRL+SHIFT+K**
* `Cut` an entire `line` (when no text is selected)  **CTRL+X**
* `Move` an entire `line`  **ALT+ARROWS**
* `Select` the current `line`  **CTRL+L**
* Invoke `IntelliSense`  **CTRL+SPACE**
* `Multiple` selections (multi-cursor)  Hold **ALT** and **select**
* Code `Folding`  **Ctrl+Shift+[** , **]**
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