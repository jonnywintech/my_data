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

```bin
#! /bin/bash

echo "Reading user input"
read -p "Please enter your password"
```

