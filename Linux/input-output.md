chaining multipe commands in terminal

| pipe command


output of one command to input to anotherone

cat `intput` >>> `output` | `input`

example
```bash
cat /var/log/syslog | less
```


```bash
ls /bin/bash | less
```

it will output page by page output of this and with `space` i can jump between, `enter` to jump one line next  and `q` to quit

example with `grep`
```bin
history | grep sudo
```
>>> output is history with all fields where sudo is used

`>` overides content of the file with curent output 
```bash
history | grep rm > sudo-rm-commands.txt
```

`>>` appends text to file
```bash
history | grep sudo >> sudo-rm-commands.txt
```

Every program standard output 


STDIN (0) = standard input
STDOUT(1) = standard output
STDERR(2) = standard error


