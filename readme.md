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
* Closing built-in `Terminal`  **CTRL+d**
* `Find` And `Replace`  **CTRL+F**, **CTRL+H**
* `Find` And `Replace Globally`  **CTRL+SHIFT+F**, **CTRL+SHIFT+H**
* `Side By Side` Editing  **CTRL+\\**
* `Fullscreen`  **F11**
* Open `Markdown preview` **CTRL+SHIFT+V**
* `Sidebar` Toggle **CTRL+B** 
---

* `Copy` an entire `line` (when no text is selected)  **CTRL+C**
* `Delete` an entire `line` (when no text is selected)  **CTRL+SHIFT+K**
* `Cut` an entire `line` (when no text is selected)  **CTRL+X**
* `Move` an entire `line`  **ALT+ARROWS**
* `Select` the current `line`  **CTRL+L**
* IntelliSense  **CTRL+SPACE**
* `Multiple` selections (multi-cursor)  Hold **ALT** and **select**
* Code `Folding`  **Ctrl+Shift+[** and **]**
* `Rename` Refactoring  **F2**
* `Navigating` on Errors and Warnings  **F8**
* Go to `Definition` **F12**

---
Vscode as default merge, diff tool
```bash
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'