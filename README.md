## About
These are the instructions from
[Claudio d'Angelis's blog](https://claudiodangelis.com/2012/osx-launch-terminal-from-shortcut/)
on how to setup macOS to launch `Terminal` (or any app) with keyboard
commands.

### Instructions
OSX as is doesn't allow users to set keyboard shortcuts to launch applications, but there are a bunch of 3rd-party softwares and workarounds to achieve that.

If you don't want to use a 3d-party app then the best way to do that is creating a service that just launches an application, and then bind it to a given keyboard shortcut. Let's start:

Open Automator.app and choose new "Service" document:

```
$ open -a Automator
```

In the right tab, set "Service receives" to "no input", then drag and drop "Run AppleScript" action to the workflow:

"Run AppleScript" is located under "Utility" section.

Set the content of the script to:

```
on run {input, parameters}

  tell application "Terminal"
    reopen
    activate
  end tell

end run
```

Save the document as "Open Terminal" (or whatever) and close Automator.app
Go to System Preferences **->** Keyboard **->** Keyboard Shortcuts **->** Services, then scroll until you find your new service under General section and assign it a shortcut.
