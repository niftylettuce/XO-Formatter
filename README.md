[Xo-Formatter](https://github.com/niftylettuce/Xo-Formatter) for Sublime Text 3
=================

Sublime Text 3 Plugin to autoformat your javascript code according to the XO configuration files you already have.

This plugin formats but does not lint your code. To also enable linting, use this plugin in conjuction with [SublimeLinter-xo](https://github.com/roadhump/SublimeLinter-xo).


## Installation

### Linter installation
This Sublime Text Plugin depends on a valid installation of xo version 3 or higher. To install `xo`, follow the getting started guide: <https://github.com/sindresorhus/xo>

### Plugin installation

Please use [Package Control](https://sublime.wbond.net/installation) to install the linter plugin. This will ensure that the plugin will be updated when new versions are available. If you want to install from source so you can modify the source code, you probably know what you are doing so we won’t cover that here.

To install via Package Control, do the following:

1. Within Sublime Text, bring up the [Command Palette](http://docs.sublimetext.info/en/sublime-text-3/extensibility/command_palette.html) and type `install`. Among the commands you should see `Package Control: Install Package`. If that command is not highlighted, use the keyboard or mouse to select it. There will be a pause of a few seconds while Package Control fetches the list of available plugins.

1. When the plugin list appears, type `xo format`. Among the entries you should see `Xo-Formatter`. If that entry is not highlighted, use the keyboard or mouse to select it.


## Commands
**Command palette:**

- XoFormatter: Format this file

**Shortcut key:**

* Linux/Windows: [Ctrl + Shift + X]
* Mac: [Cmd + Shift + X]

## Behavior

The formatting will be applied to the last saved state of a file, not the current buffer.
If not using the `format_on_save: true` option, you have to save your file first and then run the command.

## Settings

By default, XoFormatter will supply the following settings:

```javascript
{
  // The Nodejs installation path
  "node_path": {
    "windows": "node.exe",
    "linux": "/usr/bin/nodejs",
    "osx": "/usr/local/bin/node"
  },

  // The location to search for a locally installed xo package.
  // These are all relative paths to a project's directory.
  // If this is not found, it will try to fallback to a global package
  // (see 'xo_path' below)
  "local_xo_path": {
    "windows": "node_modules/.bin/xo",
    "linux": "node_modules/.bin/xo",
    "osx": "node_modules/.bin/xo"
  },

  // The location of the globally installed xo package to use as a fallback
  "xo_path": {
    "windows": "%APPDATA%/npm/node_modules/xo/bin/xo",
    "linux": "/usr/bin/xo",
    "osx": "/usr/local/bin/xo"
  },

  // Specify this path to an xo config file to override the default behavior.
  // Passed to xo as --config. Read more here:
  // https://github.com/sindresorhus/xo
  // If an absolute path is provided, it will use as is.
  // Else, it will look for the file in the root of the project directory.
  // Failing either, it will skip the config file
  "config_path": "",

  // Automatically format when a file is saved.
  "format_on_save": false,

  // Only attempt to format files with whitelisted extensions on save.
  // Leave empty to disable the check
  "format_on_save_extensions": [
    "js",
    "jsx",
    "es",
    "es6",
    "babel"
  ]
}
```

* Modify any settings within the `Preferences -> Package Settings -> Xo-Formatter -> Settings - User` file.

**Project-specific settings override**

To override global plugin configuration for a specific project, add a settings object with a `Xo-Formatter` key in your `.sublime-project`. This file is accessible via `Project -> Edit Project`.

For example:

```
{
  "folders": [
    {
      "path": "."
    }
  ],
  "settings": {
    "Xo-Formatter": {
      "format_on_save": true
    }
  }
}
```

## Contributing

If you find any bugs feel free to report them [here](https://github.com/niftylettuce/Xo-Formatter/issues).

Pull requests are also encouraged.
