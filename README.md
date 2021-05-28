# Cisco Automation With Exscript & Python3

# Used to automate finding/changing configuration on Cisco devices
### Can be used for any device that supports ssh but purpose built for Cisco switches/routers

#### Getting Started
1. You need python3, pip3, and exscript. If on Windows view "Using WSL 2 on Windows" 
    - pip3 - https://www.makeuseof.com/tag/install-pip-for-python/ 
        - sudo apt install python3-pip
    - exscript -  https://github.com/knipknap/exscript.git  
        - pip3 install -r requirements.txt .
2. Change 'hosts/hosts_file' to include the hosts to connect to
    - One host per line, no other formatting required
3. To run the file
    - python3 cisco_cmd.py or ./cisco_cmd.py (Syntax below)
4. Results are printed to console and appened to results.txt
    - Can send results to different file (Syntax below)

#### Syntax: 
" " or ' '  are REQUIRED when using spaces

-o is NOT required

###### Help

> ./cisco_cmd.py -h, --help

###### List built-in commands

> ./cisco_cmd.py -b, --list-builtin

###### To run built-in commands

> ./cisco_cmd.py -c `<built-in_command>`, --cmd `<built-in_command>`

###### To run a custom command

> ./cisco_cmd.py -d `<custom_command>`, --custom `<custom_command>`

###### Optional user input filter for built-in commands
> ./cisco_cmd.py -c `<built-in_command>` -o `<option>`, ./cisco_cmd.py --cmd `<built-in_command>` --option `<option>`

###### To run modules & multiple commands 
>These modules are located in the "modules" directory. To see contents of file/module - cat `<module_name>`

> ./cisco_cmd.py -m `<module_name>`, --module `<module_name>`

###### To list the available modules

> ./cisco_cmd.py -l, --list-modules

#### Examples:
> ./cisco_cmd.py -c shmac -o abcd
> 
> ./cisco_cmd.py -c shmactable
>
> ./cisco_cmd.py -c shintstatus -o '| in Gi1/0/1'
>
> ./cisco_cmd.py -c shint -o Gi1/0/1
>
> ./cisco_cmd.py -c shint -o 'Gi1/0/1 | in CRC'
> 
> ./cisco_cmd.py -c shrun
>
> ./cisco_cmd.py -c shrun -o '| begin secret'
>
> ./cisco_cmd.py -d 'show vtp status | in trunk'
>
> ./cisco_cmd.py -d 'show run | begin trunk'
>
> ./cisco_cmd.py -m `<name_of_module>`
>
> ./cisco_cmd.py -m shmactableint
>
> ./cisco_cmd.py -m health

#### ToDo

Add templates for better interactions - https://exscript.readthedocs.io/en/latest/cli_tutorial.html#the-exscript-template-language

Add modules & built-in tasks

Printing results to another file on the fly
