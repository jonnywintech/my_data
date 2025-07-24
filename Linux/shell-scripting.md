shell and bash scripts are used for making devops task easiser and optimizing workflow making shell and bash commands.

Bourne Shell - (sh) /bin/sh

Bourne again shell(bash) /bin/bash

`#` musical notation, also called "sharp"
`!` also called "bang"

automated-config.sh
```bash
#! /bin/bash
# it is called shebeng line it gives instruction which shell to run on system

echo "Starting configuration of server";

file_name=config.yaml

# conditionals
if [-d "config"]
then
    echo "reading config directory contents"
    config_files=$(ls config)
else
    echo "config dir not found"
    echo "making new one"
    mkdir config
fi

num_files=xx

if [ num_files -gt 10 ]
    then
        echo "number of files is greather than 10"
elif [ num_files == 10 ]
    then 
        echo "number of files is equal 10"
fi

#this is passing parameters to file
#after running file with ./automated-config.sh <parameter> (eg admin)

#then that parameter is passed into $1

user_group=$1

if [ "$user_group" == "nana" ]
 then
 echo "configure server"
elif [ "$user_group" == "admin" ]
 then
 echo "Configuring server as admin"
else
 echo "No permission to configure server"
fi




all_config_files=$(ls config) 
# referencing command into variable that can be used later on

echo "using file $file_name to configure somethig"

#using variable for file and echoing it in bash

echo "here are $all_config_files located on server"

```


making prompt in shell

```bash
#! /bin/bash

echo "Reading user input"
read -p "Please enter your password" user_pwd

echo "thanks for your password $user_pwd"
# in this case password is ave into user_wpd variable and later on echoed  just for practicing and representing later on how user input can be used
```

multiple parameters script
```bash
#! /bin/bash
echo "user $1"
echo "user $2"
# this displays only this first 2 variable

# however $* represent all parameters entered after script as STRING

#>> /script.sh var1, var2, var3, var4
echo "all variables as string $*"

#>> var1, var2, var3, var4

#looping trough variables and echoing them

for param in $*
 do
 echo $param
 done

 #simple example of bash for in loop

```
Example of while loop and how summing numbers work in bash
```bash
#! /bin/bash

sum=0
while true
 do
  read -p "enter a score: " score
  if [ "$score" == "q" ]
  then
   break
  fi
#here is situation how to sum two numbers in bash with double braces one for eval and another one for getting result as var
  sum=$(($sum+$score))
  echo "toal score $sum"
done
```

Example of basic function
```bash
function hello {
    echo "hello there"
}

# calling funcion
hello
```

creating function with parameters
```bash
function create_file() {
    file_name=$1
    touch $filename
    echo "file succesfully created"
}
```

