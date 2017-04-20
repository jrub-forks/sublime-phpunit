# Sublime PHPUnit

Convenient Sublime Text commands for running your PHPUnit tests. Scans up the directory tree to find the closest phpunit.xml file and runs phpunit from there. If it can't find one, it just runs phpunit from `/`.

## Installation


Installation is as simple as cloning the repository into your Sublime Text install's `Packages` folder:

```bash
git clone https://github.com/adamwathan/sublime-phpunit ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/sublime-phpunit
```

## Available Commands & Example Keybindings

You can find the commands in the command palette under "Sublime PHPUnit", or map any of these commands to whatever shortcuts you want:

Here's the full list of commands:

```
run_phpunit_test
run_phpunit_tests_in_dir
run_single_phpunit_test
run_last_phpunit_test
run_all_phpunit_tests
````

Here are some example keybindings:

```json
[
    { "keys": ["alt+t"], "command": "run_phpunit_test"},
    { "keys": ["super+alt+t"], "command": "run_single_phpunit_test"},
    { "keys": ["super+alt+l+t"], "command": "run_last_phpunit_test"},
    { "keys": ["super+shift+t"], "command": "run_phpunit_tests_in_dir"},
    { "keys": ["super+shift+ctrl+t"], "command": "run_all_phpunit_tests"},
]

```

## Using iTerm2 instead of Terminal.app

By default, this package uses macOS's built-in Terminal.app. If you want to use iTerm2, you can do so changing the terminal in your settings:

```
{
    "phpunit-sublime-terminal": "iTerm",
}
```

## Using fish shell

If you use [fish shell](https://fishshell.com/), specify this in your settings: 

```
{
    "php-sublime-shell": "fish"
}
``` 

This will instruct Sublime PHPUnit to connect the commands using fish's `; and` instead of bash's `&&`.

#### Options

Below are the options supported by this package. They are set in the user preferences file (`Preferences.sublime-settings -- User`). You can get to these by pressing `⌘` + `,`, or by going to `Sublime > Preferences > Settings`

* * *


`phpunit-sublime-terminal` **string** -- *optional* -- **default:** `"Terminal"`

> By default, this package will attempt to open the OS X *Terminal.app* application for executing tests.
> 
> If you prefer to use *iTerm.app* set the value for this property to `"iTerm"`.



`phpunit-sublime-autofocus` **boolean** -- *optional* -- **default:** `false`

> If you want to re-focus sublime after you start your tests, set this to `true`. The package will automatically switch focus back to the last Sublime window you had focused.
>
> *Note: This happens pretty much immediately, so if your terminal window is behind your sublime window -- you'll miss all the terminal output. If you activate this, best to make sure your Sublime and Terminal apps aren't stacked.*



`phpunit-sublime-autofocus-delay` **int** -- *optional* -- **default:** `100`

> The time, in milliseconds, you want to wait before re-focusing Sublime. If `phpunit-sublime-autofocus` is `false`, this option is ignored. This is best used if things are moving too fast for your machine and you need to introduce a delay. Most won't need it.
>
> *Note: This delay happens on the main Sublime thread. You **should NOT** try to estimate how long your test suite will run and put that value here. You will end up beach-balling Sublime for the duration of the delay.*
