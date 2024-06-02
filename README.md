# RunSyncedApp

This small application allows to start multiple applications at once and if one of them is closed, the others are killed.

## Usage

```shell
runsyncedapp.exe --config=myconfig.json --log --logfile
```

- `config` : path of the config file
- `log` : enable logging (in console by default)
- `logfile` : log events in a `trace.log` file

## JSON configuration

The configuration file looks like this:

```json
{
    "waitCheck": 10,
    "waitExit": 10,
    "applications": [
        {
            "path": "C:\\Windows\\System32\\dxdiag.exe",
            "useExistingInstance": false,
            "killOnExit": true
        },
        {
            "path": "C:\\Windows\\System32\\charmap.exe",
            "useExistingInstance": false,
            "killOnExit": true
        },
        {
            "path": "C:\\Windows\\System32\\msinfo32.exe",
            "useExistingInstance": false,
            "killOnExit": false
        }
    ]
}
```

The parameters are the following:

- `waitCheck`: time in second to wait after the applications starts and the verifications
- `waitExit`: time in second to wait before the applications closures
- `applications`: array of application to execute:
  - `path`: full path of the application
  - `useExistingInstance`: don't start a new instance if it's already running
  - `killOnExit`: kill the application if it's running after another app has been killed
