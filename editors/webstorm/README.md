## Configure External Tool

https://blog.jetbrains.com/webstorm/2016/08/using-external-tools/

Go to *File | Settings | Tools | External Tools* for Windows and Linux or *WebStorm | Preferences | Tools | External Tools* for OS X and click **+** to add a new tool. Let’s name it **Prettier**.

* **Program** set `prettier`

> If on the other hand you have `prettier` installed locally, replace the **Program** with `$ProjectFileDir$/node_modules/.bin/prettier` (on OS X and Linux) or `$ProjectFileDir$\node_modules\.bin\prettier.cmd` (on Windows).

* **Parameters** set `--write [other opts] $FilePathRelativeToProjectRoot$`
* **Working directory** set `$ProjectFileDir$`

![Example](./with-prettier.png)

### Process directories

* Clone the External tool created above and name it `Prettier Directories`
* **Parameters** set `--write [other opts] $FileDirRelativeToProjectRoot$/**/{*.js,*.jsx}`

## Usage

* Cmd-Shift-A on OS X or Ctrl+Shift+A on Windows and Linux
* Type: 'prettier' and hit enter

### Configure Keymap

Now when you setup **External Tool** I guess you want to add hotkey for it. Go to *File | Settings | Keymap* for Windows and Linux *WebStorm | Preferences | Keymap* and type external tool name in search box.

See [this documentation](https://www.jetbrains.com/help/webstorm/configuring-keyboard-shortcuts.html) about configuring keyboard shortcuts.

## Using File Watcher

To automatically format using `prettier` on save, you can use a file watcher.

Go to *File | Settings | Tools | File Watchers* for Windows and Linux or *WebStorm | Preferences | Tools | File Watchers* for OS X and click **+** to add a new tool. Let’s name it **Prettier**.

* **File Type**: JavaScript
* **Scope**: Current File
* **Program** set the full path to a `prettier` executable, such as `/Users/developer/repo/jest/node_modules/.bin/prettier` (on OS X and Linux) or `C:/\Users\developer\repo\jest\node_modules\.bin\prettier.cmd` (on Windows).
* **Arguments** set `--write [other opts] $FilePath$`
* **Working directory** set `$ProjectFileDir$`
* **Immediate file synchronization**: Uncheck to reformat on Save only (otherwise code will jump around while you type).

![Example](./prettier-file-wacther.png)

### Multiple file types  ###

If you woud like to use one watcher for multiple file types.
Or if you like more control, make these changes to the settings above.

* **File Type**: Any
* **Arguments** set `--write $FileDir$/*{.js,.ts,.tsx}`

> I want prettier to run for any Javascript, Typesript or tsx file.

![Example](./prettier-file-watcher-multi-file.jpg)

