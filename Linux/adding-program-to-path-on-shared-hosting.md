Adding chromium for example on shared hosting

Taking Hostinger for example it have `~/.profile` version of .bashrc configuration file

open it with editor
```bash
nano ~/.profile
```

at the end of file add folowing
```bash
export PATH=$PATH:/home1/chromium/chrome-linux
```
replace after `$PATH:` with your route to app it may differ

- save then reload  .profile

```bash
source ~/.profile
```
