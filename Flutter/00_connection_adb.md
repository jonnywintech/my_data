
commands to restart adb server `not always nessessary only when you have errors while debugging`

stop server
```bash
adb kill-server
```

start server
```bash
adb start-server
```

pair device if is not paired via passkey
```bash
adb pair <device_ip>:<device_pairing_port>
```
afther typing it will ask you for `passkey`
this option is ususaly in  debugging> wireless> pair with passkey
`pairing ip and port may differ from connecting one and they are 2 different things`

connecting device to wirelless adb service
```bash
connected to 192.168.1.71:41413
```
