# Deamons-ora-break
_Per Mac OSX. Notifica per sospendere il lavoro al computer e prendere una pausa per riposare occhi e cervello_.

Istruzioni di implementazione in inglese affinchè sia fruibile da tutti

### Instructions for implementing:

- [Shell script](https://github.com/riettotek/Deamons-ora-break/edit/main/README.md#the-shell-script) that shows the notification
- The config [plist file](https://github.com/riettotek/Deamons-ora-break/edit/main/README.md#the-launchd-agent) for the launchd agent that sets up the recurring reminder
- [CLI commands](https://github.com/riettotek/Deamons-ora-break/edit/main/README.md#CLI-Commands) to initialize such agent.

## The shell script 
_It uses the Mac's built-in notification system to show the message_ 

Place it in this folder `~/scripts/ora-break.sh`
You able to change the location as u prefer, but remember to inform your plist file about the new location

## The launchd agent
_Place this file in_ `~/Library/LaunchAgents/ora-break.plist`
Open the file in your prefered IDE to change the values for the interval of seconds and the directory to place the shell script 
Remember to change path for the shell script in order to match your (see YOURACCOUNT)
```
[...]
    <array>
        <string>sh</string>
        <string>/Users/YOURACCOUNT/scripts/ora-break.sh</string>
    </array>
    <key>StartInterval</key>
    <integer>3600</integer>
[...]
```
## CLI Commands
```
$ launchctl load ~/Library/LaunchAgents/ora-break.plist 
$ launchctl start ora-break
```
-----
### To stop the Agent
Perform this command
```
$ launchctl stop ora-break
```
### Change Settings
if you ever want to change the agent settings, you'll additionally need to unload the agent and then reload and restart it to pick up the changes
```
$ launchctl unload ~/Library/LaunchAgents/ora-break.plist
```
