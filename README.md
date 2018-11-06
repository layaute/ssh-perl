# ssh-perl
execute a batch of commands on a list of IPs
NAME
       ssh-perl - execute a batch of commands on a list of IPs
       The script generates a result file for each IP containing the output of the executed commands
       A log file is generated to records events

SYNOPSIS
       ssh-perl takes one or more arguments
       ssh-perl [OPTION] --path [PATH]
       [OPTION] will allow you to modify or specify various parameters
       [PATH] is a path to a folder containing the list of commands and the list of IPs
       Example:
        ./ssh-perl.pl --path /opt/ssh-perl/hp_switch/ -p 22

OPTION
       -path: mandatory, specifies the path to the folder containing the necessary information for ssh-perl
       --help, -h: display the manual
       -p: specify the port to reach the device (-p 4222 or -p=22)
       -t_rsa: timer used to match the RSA key (default value 5s)
       -t_pass: timer used to match the password (default value 5s)
       -t_login: timer used to match the login (default value 2s)
       -t_login2: timer used to match the second login (default value 2s)
       -t_cmd: timer used to match the prompt after a command has been entered (default value 20s)
       --port: add the port to be used for each device in the ip.txt file
       --sudo: to have sudo rights on a server
       --debug: Print debug output -SH PATH Must be a path to a folder containing 2 files:
       ip.txt: a list of IPs
       cmd.txt: a list of commands

[ip.txt]
       Contains the list of IPs respecting this format
       location;@IP
       Example:
        France;10.33.42.42
        Spain;10.34.42.42
       Example with --port:
        France;10.33.42.42;22
        Spain;10.34.42.42;4222

[cmd.txt]
       Contains the list of commands to be executed
       One command per line
       Example:
        no page
        show run
        sh ip int brief
       It's a best practice to use a command that will skip page display
       Example:
        no page
        term len 0
        skyp display
        skip-page-display
RESULT
       ssh-perl will generate two folders in your [PATH] directory
       A folder named RESULT containing all output files
       A subfolder containing the location and date of execution will also be generated
       Example:
        [PATH]/RESULT/France/2018-10-18/10.33.42.42.conf
        [PATH]/RESULT/Spain/2018-10-18/10.34.42.42.conf
       A folder named log containing the logs output
       Example:
        [PATH]/log/2018-10-18_cmdtool.log

BUGS
       No known bugs.

AUTHOR
       hugo.allamel@hoistgroup.com
       2018-11-06
